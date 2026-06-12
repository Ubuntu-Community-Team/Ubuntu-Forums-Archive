---
title: "Cant install Ubuntu 8.04"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by reeksy on 2008-05-24
Hi

I've just downloaded the ubuntu-8.04-desktop-i386.iso, run md5sum on it, burnt it to DVD and then rebooted my computer.

When i select 'install' from the CD boot menu i receive the following error:

```

(initramfs) [ 95.48.1814] 8139cp 0000:02:05:0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip

[ 95.481887] 8139cp 0000:02:05.0: Try the "8139too" driver instead.

[ 95.520905] hda: drive not ready

```

I cant even run the 'live' aspect of the CD - i get the same error.

Does anyone know how i get around this to install Ubuntu? Ive run the previous version without any issues on the same computer

Regards,
Jon

---

### Post by Kevbert on 2008-05-24
Seeing as you've been able to run previous versions without problems, it's probably a CD/DVD problem.  There should be a CD check that you can run when you boot it up.  If you get errors it may be due to trying to burn the CD too quickly.  The slower speed you burn it the better.  If the ISO checksum is correct then the ISO file can be reused.

---

### Post by reeksy on 2008-05-24
OK, thanks - I'll try re-burning it and try again.

---

### Post by reeksy on 2008-05-24
... burnt at 8 speed with no luck. I'm going to try an old install of Ubuntu or a different distro i think. I've been running Ubuntu for a few years without any problems. But since upgrading, I've had no end of trouble -like not being able to eject my DVD drive and regular crashes!

Thanks for your help.

---

### Post by arluijen on 2008-05-26
No good here, had the exact same error after installing Ubuntu 8.0.4 server. Ubuntu client used to work fine on this machine.

Did a cd check and this seemed to be ok. One thing I noticed when searching the Bug database was this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222722]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222722")

..and to my surprise: there was no /etc/mdadm dir nor /etc/mdadm.conf.

Right now I'm reinstalling again....

---

### Post by arluijen on 2008-05-26
hmmm, after reinstall no more messages about 8139... but not exactly working:

If I start up, no error messages but still the system reboots in a shell kind of mode (no gui at all) where I'm suppused to login and that's that.

Again, I can't find the /etc/mdadm dir nor /etc/mdadm.conf.

---

### Post by Kevbert on 2008-05-28
It looks like the bug report you quoted may be closed.  I'd raise a new one in launchpad.  By the look of it your mdadm raid package hasn't been installed.

---

