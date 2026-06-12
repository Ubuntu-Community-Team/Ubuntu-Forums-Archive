---
title: "Installing 11.10 Issues"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by spikoley on 2012-03-14
I am having issues installing 11.10.  It will not install from Install Ubuntu, so I went to Try Ubuntu.

When it boots into Unity there are a few errors.  It does not load the Unity launcher and I cannot get to the terminal via Ctrl + Alt + T.

The install shortcut fails to load.

Any ideas on what to do?  Once its installed I should be able to run in Classic Mode without any issues.

---

### Post by HeroOfCanton on 2012-03-14
Is it possible you had a bad burn? Maybe verify the checksum of your iso download too.

If it won't even run in live mode that's not a good sign. Hopefully it was just a bad download or burn.

If not you may have to stick to an older version or switch to an x/l/k distro.

---

### Post by spikoley on 2012-03-14
The md5 was fine and I am using a USB thumb drive.

---

### Post by HeroOfCanton on 2012-03-15
> **spikoley said:**
> The md5 was fine and I am using a USB thumb drive.

Hmm... Maybe you should try the [alternate installer]("http://www.ubuntu.com/download/ubuntu/alternative-download") just to get it on the hard drive, then you can get gnome classic or another DE from there if you're still having problems.

---

### Post by spikoley on 2012-03-15
Figured it out.  I put in a new hard drive that a friend gave me.  For some bizarre reason he installed 10.10 on it as an image with the boot parameter of /cdrom.  It was booting into that instead of my USB drive even though the CD rom was set to boot as second.

Thanks for the help.

---

