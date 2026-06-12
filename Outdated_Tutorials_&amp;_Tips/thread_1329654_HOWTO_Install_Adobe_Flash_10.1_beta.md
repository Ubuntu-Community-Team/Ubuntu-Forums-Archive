---
title: "HOWTO: Install Adobe Flash 10.1 beta"
date: 2009-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by WattoDaToydarian on 2009-11-17
The Adobe Flash player 10.1 beta was released.

First download the tarball from [***here***]("http://labs.adobe.com/downloads/flashplayer10.html").

Next close Firefox and uninstall your current flash player by removing "flashplugin-installer" ("sudo apt-get remove flashplugin-installer")

Then extract the tarball to an empty location. Either right click and choose "Extract Here" or use "tar xzf flashplayer10_1*" in your terminal.
For **32bit** systems you should be able to run "flashplayer-installer" by doing "./flashplayer-installer" in your terminal.
For **64bit** systems it is a little more tricky. You have to use a terminal, cd to the folder where the new flash player is extracted, and run these commands:
```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
```
To remove it on 64bit systems run these commands:
```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo rm /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
```
If you don't know what 64bit systems are then don't use the commands above...

[*Here is a link to the release notes.*]("http://labs.adobe.com/technologies/flashplayer10/releasenotes.pdf")

Finally open Firefox, click Tools, choose Add-ons, click the plugins tab, and look for Shockwave Flash 10.1.
Once you see that you may enjoy your YouTube videos!:popcorn:

---

### Post by firewrks on 2010-01-21
This worked with an Nvidia 9600GT with Flash 10.1 beta 2 with some additional work. (note: amd64 arch)  It required Nvidia 195 drivers.

1) deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main 
2) sudo apt-get update && sudo apt-get install nvidia-195-modaliases nvidia-glx-195

---

