---
title: "Can't play movie file in ubuntu ?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Ahmed28 on 2008-11-05
I installed VLC in ubuntu, but everytime I use VLC or Totem Gstreamer, to play divx/xvid avi, wmv, mpg, etc, the VLC and Totem autoclose themselves, what's wrong with them ?





Thanks

---

### Post by m_duck on 2008-11-05
Have you installed the codecs for playing these files? If you install the ubuntu-restricted-extras package via synaptic or in  terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
This should install most of the codecs you need for common media files. For DVD playback etc see [here](https://help.ubuntu.com/community/RestrictedFormats) for info on playing other media types.

---

### Post by Ahmed28 on 2008-11-05
Euh, 357 megs, But I run it via live cd, is it okay ? will it write to HDD ?

---

### Post by m_duck on 2008-11-05
Sorry, I'm not sure what you mean? I don't think the ubuntu-restricted-extras package is on the CD so it would have to be downloaded. It should be possible to just download the packages you need to play each type of file (as ubuntu-restricted-extras is a meta package which refers to a load of other packages to install) but I don't know which package is for which.

---

### Post by Bölvaður on 2008-11-05
These 2 are the ones you are looking for:
gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll

libdvdread3   (I think it is dvd playback only)

liblame0 (not sure what it is)


I also have gstreamer0.10-alsa, gstreamer0.10-gnomevfs, gstreamer0.10-pulseaudio (this is actually something you might need), gstreamer0.10-x

try add one by one or all of those and check if it works.

---

### Post by philinux on 2008-11-05
> **Ahmed28 said:**
> Euh, 357 megs, But I run it via live cd, is it okay ? will it write to HDD ?
No.

Even if you sort this out so it works, the next time you boot up the live cd you would have to go through the same process again.

Maybe this might help you.
[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

---

