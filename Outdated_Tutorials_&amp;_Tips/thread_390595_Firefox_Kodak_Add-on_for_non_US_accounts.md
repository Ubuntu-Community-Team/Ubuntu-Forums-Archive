---
title: "Firefox Kodak Add-on for non US accounts"
date: 2007-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by stepheny on 2007-03-22
The Firefox addon “Firefox Companion for Kodak EasyShare Gallery” is installed with the USA [www.kodakgallery.com](www.kodakgallery.com) as default and offers no way to change this to any of the other Kodak galleries. ie [www.kodakgallery.eu.com](www.kodakgallery.eu.com), [www.kodakgallery.de](www.kodakgallery.de) or [www.kodakgallery.co.uk](www.kodakgallery.co.uk) etc

Here is how to change the default gallery.

First install the [Firefox Companion for Kodak EasyShare Gallery]("http://en-us.www.mozilla.com/en-US/add-ons/kodak/") from this link. After it is installed you will find an archive called kodak.jar in your home directory, it is to be found at ~/.mozilla/firefox/xxxxxxx.default/extensions/kodak-companion@mozilla.com. I am not sure how the xxxxxxx.default file receives its name but usually there is only one .default file, if there are more look under them all until you find the kodak related files.

Go to the kodak.jar copy it into a temp directory, ie ~/test. Rename the kodak.jar file in ~/.mozilla/firefox/xxxxxxx.default/extensions/kodak-companion@mozilla.com to kodakOrig.jar so that you can rename it back to kodak.jar if anything goes wrong.

Now go to ~/test and right click on the kodak.jar archive and select “extract here” from the drop down menu. The files are extracted to a directory called kodak.jar_FILES, inside this directory are three directories called “content” “locale” and “skin. Open the path content/js/services/kodak and you will see the file kodakPhotoService.js, open this file with an editor and change all references to kodakgallery.com to the gallery you want to use, in my case this was kodakgallery.eu.com, and save the file.

Now open ~/test/kodak.jar_FILES, select the three directories, right click and select “create archive”. Name this archive kodak.jar and copy it to ~/.mozilla/firefox/xxxxxxx.default/extensions/kodak-companion@mozilla.com.

Restart Firefox and you can now use the Firefox Companion for Kodak EasyShare Gallery to upload your pictures to the gallery you have chosen.

---

### Post by adam.tropics on 2007-03-22
> **stepheny said:**
> 
First install the [Firefox Companion for Kodak EasyShare Gallery]("http://en-us.www.mozilla.com/en-US/add-ons/kodak/") from this link. After it is installed you will find an archive called kodak.jar in your home directory, it is to be found at ~/.mozilla/firefox/xxxxxxx.default/extensions/kodak-companion@mozilla.com. I am not sure how the xxxxxxx.default file receives its name but usually there is only one .default file, if there are more look under them all until you find the kodak related files.


Couple small things. The xxxxxx.default is an identifier for your firefox profile. The .default just denotes that it is clearly the default. There will only be one. (If you ever want another profile btw, start it with firefox -P) Secondly, for me at least the archive was named fotofox.jar..?? Everything else was the same however. Oh, and this isn't too important on this one, as having tried both with this, either is fine, but the jar file, is actually a zip file with a jar extension. A firefox quirk! Nice find though.

---

