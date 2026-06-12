---
title: "32-bit Installer Installs 64-bit?"
date: 2014-07-25
forum: New to Ubuntu
---

### Post by Warren_Wong_Yee_Ke on 2014-07-25
Hi.

I needed to use 32-bit Ubuntu to s-off my phone. I went on to the official Ubuntu site and triple checked to make sure that I downloaded the 32-bit (i386) version of the installer. However, after installing, when I went in to "About This Computer" to check, it says that my OS type is 64-bit and because of this, my program will absolutely not work. Anyone can help me on getting the true 32-bit version?

---

### Post by mastablasta on 2014-07-25
here is the torrent link: [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-i386.iso.torrent)

you can see that 32 bit installer has i386 in image's name. what is your image file name?

---

### Post by Warren_Wong_Yee_Ke on 2014-07-25
> **mastablasta said:**
> here is the torrent link: [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-i386.iso.torrent)

you can see that 32 bit installer has i386 in image's name. what is your image file name?

My image file name is "ubuntu-14.04-desktop-i386" but after installing it shows 64-bit in the OS type field of "About This Computer".

---

### Post by mastablasta on 2014-07-25
open terminal and copy this command to it:

```
uname -a
```

then copy and post the results here

---

### Post by Warren_Wong_Yee_Ke on 2014-07-25
> **mastablasta said:**
> open terminal and copy this command to it:

```
uname -a
```

then copy and post the results here

Before that, one question. Does wubi install in 64-bit?

---

### Post by lisati on 2014-07-25
> **Warren_Wong_Yee_Ke said:**
> Before that, one question. Does wubi install in 64-bit?

If memory serves correctly, WUBI does. Unfortunately, it is no longer supported.

Please [try Ubuntu this way]("http://ubuntuforums.org/showthread.php?t=2230389") before installing it.

For more information, see [this]("http://ubuntuforums.org/showthread.php?t=2229766") thread.

---

### Post by newb85 on 2014-07-25
Ubuntu's support for Wubi was discontinued over a year ago.  I would *not* recommend using it.

---

### Post by Warren_Wong_Yee_Ke on 2014-07-25
> **lisati said:**
> If memory serves correctly, WUBI does. Unfortunately, it is no longer supported.

Please [try Ubuntu this way]("http://ubuntuforums.org/showthread.php?t=2230389") before installing it.

For more information, see [this]("http://ubuntuforums.org/showthread.php?t=2229766") thread.

> **newb85 said:**
> Ubuntu's support for Wubi was discontinued over a year ago.  I would *not* recommend using it.

Thanks guys but I've got it sorted. Before I saw your replies I've already started wubi from command prompt with the argument "--32bit" and now I've successfully installed 32-bit Ubuntu. In fact I'm typing this reply right from my Ubuntu.

---

### Post by dave131 on 2014-07-25
wubi isn't supported for multiple reasons, including if i remember correctly the uefi "stuff".  yes, the wubi installer is on the install media but don't use it - it isn't supported. It was never intended as anything more than to just try ouy ubuntu.

---

