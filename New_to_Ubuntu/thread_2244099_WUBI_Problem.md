---
title: "WUBI Problem?"
date: 2014-09-13
forum: New to Ubuntu
---

### Post by D_Torr on 2014-09-13
I tried to put Ubuntu on my USB, But there was no "boot with usb" option in BIOS or Boot Manager, So I decided to use WUBI. The only problem is, the install finishes saying "Permission Denied", here are the errors

[http://pastebin.com/2MRdA4Jj](http://pastebin.com/2MRdA4Jj)

---

### Post by hakuna_matata on 2014-09-13
> **D_Torr said:**
> 
The only problem is, the install finishes saying "Permission Denied"
IMHO this should be the reason: [http://askubuntu.com/a/64864](http://askubuntu.com/a/64864)

Current version of Wubi needs Ubuntu 14.04: [ubuntu-14.04-desktop-amd64.iso]("http://releases.ubuntu.com/trusty/ubuntu-14.04-desktop-amd64.iso")

If you want to download and install point release 14.04.**1** ([ubuntu-14.04.1-desktop-amd64.iso]("http://releases.ubuntu.com/trusty/ubuntu-14.04.1-desktop-amd64.iso")) a new **isolist.ini **is necessary. More information is [here]("http://ubuntuforums.org/showthread.php?t=2236857&p=13117094#post13117094")

---

### Post by yancek on 2014-09-13
Wubi is no longer supported but it might work.  It might help someone to help you if you indicated which release of windows you are using.  According to the Ubuntu site, it will not work with windows 8/8.1.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by hakuna_matata on 2014-09-13
> **yancek said:**
> It might help someone to help you if you indicated which release of windows you are using.
IMHO "Windows 7 Home Premium" according to [http://pastebin.com/2MRdA4Jj](http://pastebin.com/2MRdA4Jj):
> ```
09-13 18:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
```

---

### Post by Impavidus on 2014-09-13
In principle wubi should work on Win7, although it's pretty old, unsupported and was never much more than an extended trial mode. But in this case it doesn't work. So the question is whether you want to troubleshoot the failed wubi install or the failed live disk boot. I'd try the latter.

All recent (less than, say, 7 years old) computers should be capable of booting from usb. If it can't, it should have an optical drive and you should be able to use that.

Note: [http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

