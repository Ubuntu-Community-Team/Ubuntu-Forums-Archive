---
title: "every body has gone blue"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by DaveMcC on 2012-09-23
Hi
Can't figure out what has changed, but every YouTube video that I watch is blue, well the people in are.

Both in Firefox and Chrome browsers, but not in movie player or any photo's that I have on the computer.

Point of note is also that the thumb nails belonging to any YouTube video are in the correct colours until the video is played, have also noted that red turns blue

At a loss how to fix this
Running Ubuntu 10.10 (maverick)  

Dave

---

### Post by daslinkard on 2012-09-23
**Fix (work around)**

  **Issue:**  All web browsers flash player video is blue 
  
[LIST]
[*]Chromium
[*]Google Chrome
[*]Firefox
[/LIST]
  Both flash plugins causes flash video to appear have a blue overlay, so remove. 
  
[LIST]
[*]Adobe - flashplugin
[*]Flashplugin - installer
[/LIST]
  Solution (not as functional as adobe flash plug in but it works) 
  
[LIST]
[*]Install lightspark (plus any browser-plugins)  or
[*]Install gnash (plus any browser-plugins)
[/LIST]
  **[B]Possible Fix 1**[/B]

  **Removed:** 
  
[LIST]
[*]gnash browser plug-ins
[*]gightspark browser plug-ins
[*]Video Decode and Presentation API for Unix (libraries) **libvdpau1**
[*]flashplugin - installer
[/LIST]
  **Installed:** 
  adobe-flashplugin  Re-started browser, and it worked for me.
  **[B]Possible Fix 2**[/B]

  **Installed:** 
  
[LIST]
[*]libvdpau1
[/LIST]
  Flash set-up
  
[LIST]
[*]disable HW acceleration in Flash.
[/LIST]
  Open your browser and navigate to a flash video (youtube, abobe flash  site, etc) right click, settings and disable Hardware acceleration.
  If you are unable to disable Hardware acceleration, log in to the Unity 2D environment. 
  BUG: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/968489](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/968489)
  OBS: In case of persistance. Restart the machine.

---

### Post by daslinkard on 2012-09-23
The other quicker solution that might work is as follows:

```
sudo apt-get purge flashplugin-installer
``````
sudo apt-get install adobe-flashplugin
```

---

### Post by DaveMcC on 2012-09-23
Hi daslinkard

Hi Done the bottom one first, I see the colour here in this browser is not what it should be, but here is the ? what happen in Terminal when I ran the above code

```
boss@Boss-desktop:~$ sudo apt-get purge flashplugin-installer
[sudo] password for boss: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libproc-processtable-perl unpaper tesseract-ocr libgraphicsmagick3
  libio-stringy-perl libreadonly-perl libjpeg8 libgtk2-imageview-perl
  libjpeg-progs libmagick++3 transfig libset-intspan-perl
  libextutils-depends-perl libgtk2-ex-simple-list-perl libgtkimageview0 kfind
  tesseract-ocr-eng libgraphicsmagick++3 libgtk2-ex-podviewer-perl pdf2djvu
  libconfig-general-perl cuneiform-common gocr libpdf-api2-perl libtiff-tools
  perlmagick libextutils-pkgconfig-perl djvulibre-bin cuneiform
  libgoo-canvas-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
boss@Boss-desktop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
adobe-flashplugin is already the newest version.
The following packages were automatically installed and are no longer required:
  libproc-processtable-perl unpaper tesseract-ocr libgraphicsmagick3
  libio-stringy-perl libreadonly-perl libjpeg8 libgtk2-imageview-perl
  libjpeg-progs libmagick++3 transfig libset-intspan-perl
  libextutils-depends-perl libgtk2-ex-simple-list-perl libgtkimageview0 kfind
  tesseract-ocr-eng libgraphicsmagick++3 libgtk2-ex-podviewer-perl pdf2djvu
  libconfig-general-perl cuneiform-common gocr libpdf-api2-perl libtiff-tools
  perlmagick libextutils-pkgconfig-perl djvulibre-bin cuneiform
  libgoo-canvas-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
boss@Boss-desktop:~$ 
```

After that I rebooted the computer
I see the Smillies on the right has also now turned blue  "bottom one"

disable Hardware acceleration

That done the trick, "he said hopefully"

Read the link to the other, enought to drive you mad

Thanks daslinkard

Dave

---

### Post by daslinkard on 2012-09-23
No worries....got to love the little tweaks that have to be made to keep the beast running....please mark as solved and enjoy the rest of your day!

---

