# BigBlueButton Deskshare Chrome Extension
Designed to run on any domain, for use in BigBlueButton meetings to allow the use of desktop sharing through Google Chrome's desktop capture API.
# 
## How to publish yourself?

First step: modify `allowed-domains`/`matches` in `manifest.json` file:

```
{
    "content_scripts": [ {
       "js": [ "content-script.js" ],
       "all_frames": true,
       "run_at": "document_start",
       "matches": ["*://www.domain.com/*"]
    }]
}
```

To test locally, you can add `*://localhost:*/*` in the `matches` list.

Second step: make ZIP of the directory.

Third step: navigate to [Chrome WebStore Developer Dashboard](https://chrome.google.com/webstore/developer/dashboard) and click **Add New Item** blue button.

To learn more about how to publish a chrome extension in Google App Store:

* https://developer.chrome.com/webstore/publish

## How to add inline-install button?

**Make sure that you added and verified your webpage/domain using Google WebMaster tools.** Additional instructions available [here](https://support.google.com/webmasters/answer/35179?hl=en).

```html
<!DOCTYPE html>
<html>
    <head>
        <!-- head; this <link> tag MUST be in <head> section -->
        <link rel="chrome-webstore-item" href="https://chrome.google.com/webstore/detail/your-chrome-extension-id">
    </head>
    <body>
        <!-- body; the button element that is used to invoke inline installation -->
        <button onclick="" id="install-button" style="padding: 0;background: none;height: 61px;vertical-align: middle;cursor:pointer;">
            <img src="https://www.webrtc-experiment.com/images/btn-install-chrome-extension.png" alt="Add to Chrome">
        </button>

        <script>
            document.querySelector('#inline-install').onclick = function() {
                !!navigator.webkitGetUserMedia
                    && !!window.chrome
                    && !!chrome.webstore
                    && !!chrome.webstore.install &&
                chrome.webstore.install(
                    'https://chrome.google.com/webstore/detail/your-chrome-extension-id',
                    successCallback,
                    failureCallback
                );
            };

            function successCallback() {
                location.reload();
            }

            function failureCallback(error) {
                alert(error);
            }
        </script>
    </body>
</html>
```

## For more information

For additional information, click [this link](https://github.com/muaz-khan/WebRTC-Experiment/blob/7cd04a81b30cdca2db159eb746e2714307640767/Chrome-Extensions/desktopCapture/README.md).

## Credits

[Muaz Khan](https://github.com/muaz-khan):

1. Personal Webpage: http://www.muazkhan.com
2. Email: muazkh@gmail.com
3. Twitter: https://twitter.com/muazkh and https://twitter.com/WebRTCWeb
4. Google+: https://plus.google.com/+WebRTC-Experiment
5. Facebook: https://www.facebook.com/WebRTC

## License

[Chrome-Extensions](https://github.com/muaz-khan/Chrome-Extensions) are released under [MIT licence](https://www.webrtc-experiment.com/licence/) . Copyright (c) [Muaz Khan](https://plus.google.com/+MuazKhan).
