---
title: "[SOLVED] Flash and how to get it?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by cocodaclown on 2008-08-25
Hi all ....

I installed Ubuntu today and so far I am enjoying the experience. However, ive hit a little minor brick wall in my progress. Ive tried to install Flash and it doesnt seem to work.

I went to the Flash website, got given a choice of 3 linux versions of Flash. I dl'ed the .exe version first. I cant seem to get it to open and it has a little icon of a padlock on top of the file. I dl'ed the other 2 files and they refused to open with a "error" message, in effect to I dont have the right application to open that file. 

TBH, i'm using Ubuntu because im trying to learn it ready to install on my childrens computer. My kids are only interested in YouTube and Flash/Shockwave based games like Habbo so finding bigger games with more content isnt an issue, just getting flash is. 

All help and advice is so gratefully recieved that I could snog you all :lolflag:

---

### Post by WRDN on 2008-08-25
You can get flash from the repositories. It can be found in Synaptic/ Add/ Remove, and you can use the Terminal to install it:

```
sudo apt-get install flashplugin-nonfree
```

An .exe file is a Windows executable. You would need to download the .tar.gz file (tar is used for file compression).

I would recommend you install the flash player through the repositories because, if the file is updated in the repositories, then the update will appear in the Update Manager so you can easily install it.

---

### Post by gjoellee on 2008-08-25
the easiest way to install it will be via "apturl" simply click on the link below and wait to a window appears and click on "yes" and flash will download and install automatically:
[apt://flashplugin-nonfree](apt://flashplugin-nonfree)

---

### Post by cocodaclown on 2008-08-25
TY, I love you both  :cool:

---

### Post by tuxxy on 2008-08-25
Take a look at the ubuntu-restrcited-extras package this is great for a fresh install, allows flash, mp3, dvd playback amongst other things

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

