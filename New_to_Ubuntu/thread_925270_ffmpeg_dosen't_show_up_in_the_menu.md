---
title: "ffmpeg dosen't show up in the menu"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Falc7 on 2008-09-20
Hi
I have been following this guide to install ffmpeg 
[http://tombuntu.com/index.php/2008/05/22/easily-convert-videos-with-winff-and-ffmpeg/](http://tombuntu.com/index.php/2008/05/22/easily-convert-videos-with-winff-and-ffmpeg/)
But ffmpeg dosen't show up in my applications -> sound and video menu. I am sure it is installed.

---

### Post by pHreaksYcle on 2008-09-20
It's not a program with a GUI. A GUI is controls you can see and click and the like. I'm sure that ffmpeg is a command line only program. Google for this "GUI for ffmpeg" should turn something up.

EDIT: I followed the link you provided and it says right in there! Use WinFF as the GUI. So find WinFF in your menu, that's it.

---

### Post by sayakb on 2008-09-20
```
sudo apt-get install ubuntu-restricted-extras
```
That'll allow you to play all media.

---

### Post by JDorfler on 2008-09-20
Also try [WinFF]("http://code.google.com/p/winff/") which is a front end for FFMpeg.

---

### Post by pHreaksYcle on 2008-09-20
Like I said....

> EDIT: I followed the link you provided and it says right in there! Use WinFF as the GUI. So find WinFF in your menu, that's it.

---

### Post by Falc7 on 2008-09-20
ah yes, thanks for that link, i had installed ffmpeg but hadn't installed winff, now i have installed winff i can see it in the menu. Will ubuntu automatically update winff? I have added deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free to the list of software repositories.

---

### Post by benerivo on 2008-09-20
Yes. All repository entries (including manually entered ones) will be updated automatically.

---

### Post by Dr Small on 2008-09-20
ffmpeg is a command line utility. You won't find it in the menus.

---

### Post by Falc7 on 2008-09-21
When trying to convert a flv file to 3gp, i get this error message, could someone help me?

[http://img90.imageshack.us/my.php?image=screenshotpl9.png](http://img90.imageshack.us/my.php?image=screenshotpl9.png)

---

### Post by JDorfler on 2008-09-21
> **Falc7 said:**
> ah yes, thanks for that link, i had installed ffmpeg but hadn't installed winff, now i have installed winff i can see it in the menu. Will ubuntu automatically update winff? I have added deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free to the list of software repositories.

No, it won't.  It will auto update ffmpeg, but not winff.  You have to keep an eye on WinFF on google for updates.  When you do find an update, use synaptic to uninstall the older WinFF before installing the new one.

---

### Post by angelsguitar on 2008-09-21
> **Falc7 said:**
> When trying to convert a flv file to 3gp, i get this error message, could someone help me?

[http://img90.imageshack.us/my.php?image=screenshotpl9.png](http://img90.imageshack.us/my.php?image=screenshotpl9.png)

Seems that you have a missing codec for AMR files.  I believe that codec is on the Medibuntu repositories.  I would suggest you to follow the multimedia guide on the following post; it explains how to enable the necesary repositories and other thing multimedia related:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

That should get your computer ready to handle most multimedia types out there.

---

### Post by Falc7 on 2008-10-15
I followed part 1 of that guide but i still get the same error message, is there anything else i can try?

---

