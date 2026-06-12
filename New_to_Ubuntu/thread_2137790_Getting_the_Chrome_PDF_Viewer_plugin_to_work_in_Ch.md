---
title: "Getting the Chrome PDF Viewer plugin to work in ChromIUM"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by HamHamT on 2013-04-22
I've tried following the guide at OMGUbuntu:

[http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium](http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium)

> If the above method looks a little complicated then don&#8217;t worry &#8211; there&#8217;s a quicker way to get up and running.

First follow step 1 but install Google Chrome rather than extract it.

Then run the following command (assuming you also have Chromium installed) in a new Terminal window:

sudo ln -s /opt/google/chrome/libpdf.so /usr/lib/chromium-browser/
Finally, open Chromium and follow steps 6 & 7 to enable the PDF reader.

But it isn't getting me anywhere.  I can see the plugin in chromium's about:plugins page, and I have it checked, but whenever I try and view a .pdf in the chromium browser I am getting the following error in terminal:

```
[23:23:0421/220433:ERROR:webplugin_delegate_proxy.cc(377)] PluginMsg_Init returned false
[23:23:0421/220433:ERROR:webplugin_impl.cc(271)] Couldn't initialize plug-in

```

I have tried using the apt-get purge command for both Google Chrome and Chromium, and then reinstalling both programs, but I am getting the same error.

Not sure what I'm doing wrong here.. (I must mention that I am a very new user to Ubuntu in general, running 12.10)

---

### Post by vasa1 on 2013-04-22
> **HamHamT said:**
> I've tried following the guide at OMGUbuntu:

[http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium](http://www.omgubuntu.co.uk/2010/07/use-google-chrome%E2%80%99s-native-pdf-reader-in-chromium)
...
Not sure what I'm doing wrong here... 
Could you perhaps look for a more recent protocol? That's from 2010. Browsers change quite rapidly .

---

### Post by HamHamT on 2013-04-22
Ah, didn't even take that into account.

I've downloaded the newest version for my 64-bit architecture from

[https://www.google.com/intl/es-419/chrome/browser/](https://www.google.com/intl/es-419/chrome/browser/)

and now when trying to install the new updated version using the Ubuntu Software Central application, I am getting an error saying that it conflicts with the google-chrome-unstable package.  Should I do a purge command on this old installation of Google Chrome, install the new .deb file and then reattempt the method described in the Guide I posted originally?

---

