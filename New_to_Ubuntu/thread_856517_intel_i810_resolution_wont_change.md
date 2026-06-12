---
title: "intel i810 resolution wont change"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by tactix on 2008-07-11
im using a onboard intel i810 grfx but after i did my first system update i can no longer change the screen resolution via system preferences screen resolution when i try to change the resolution it just stays the same and ask if i want to keep or discard the settings.

so ive had to use  gksu displayconfig-gtk to change the res but when i restart the comp the resolution is back to some silly high res in both the desktop and the log in screen.

any help would be great im still a linux noob unfortunately

---

### Post by hung0702 on 2008-07-11
This thread should help.

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

I remember using this on Feisty Fawn. Haven't needed it in Hardy Heron, but it should still work.

Also, check your xorg to make sure you have the right driver for your integrated gfx. If you're using a widescreen display, you may need to either update your driver or (the following isn't recommended without extensive forum-lurking) use a home-brew driver or one that isn't intended for your specific device, but has been shown to be compatible.

---

### Post by tactix on 2008-07-11
cheers for the reply will take a look im not running wide screen i only want to run at 1024x768

---

