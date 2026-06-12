---
title: "intel_rng: FWH not detected"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by mkbecker on 2008-08-19
When booting up Hardy Heron on my Dell Inspiron 6000 laptop I get the message under Hardware Drivers "intel_rng: FWH not detected".  then, once I have logged in, I immediately have a box pop up to inform me "The application 'nm-applet'(usr/bin/nm-applet) wants access to the default keyring, but it is locked'.  I then enter my former password, which is still the password to my Netgear wireless router, and everything resolves and my wireless internet connection is completed.  I think these two things are connected.  How do I resolve this issue?  I have searched the forum and found nothing here or in the wiki.  My apolgies to the Administrator for sending him/her an email on this before I figured out how to start a new thread.

---

### Post by jpeddicord on 2008-08-22
Not a tutorial. Moved to Absolute Beginner Talk.

---

### Post by Cheesehead on 2008-08-22
They are **not** connected.

intel_rng is an old Intel random number generator.
see: [http://www.linuxquestions.org/questions/linux-hardware-18/intelrng-fwh-not-detected-546360/](http://www.linuxquestions.org/questions/linux-hardware-18/intelrng-fwh-not-detected-546360/)

Your system functions just fine without it.

If you want to get rid of the error message, do:
```
sudo gedit /etc/modprobe.d/blacklist 
```

Add the following at the bottom of the file:

```
# prevents minor boot message 'intel_rng: FWH not detected'
blacklist intel_rng
```

Reboot, and success! The message is gone.

But nm-applet requesting your password is still there.

---

