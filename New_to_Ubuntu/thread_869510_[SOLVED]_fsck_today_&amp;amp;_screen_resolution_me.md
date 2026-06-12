---
title: "[SOLVED] fsck today &amp;amp; screen resolution messed up"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-07-24
When starting up this evening, my system did a fsck which I allowed to proceed but when the system finally booted up I got a screen about Ubuntu running in low graphics mode & asking if I wish to configure it.
I understand new ATI linux drivers were released today but aren't part of repositories so I haven't been trying them.
My question:  Why did the fsck cause my screen resolution to revert to low?
I have ATI x1400 & using the proprietary drivers and I can't seem to get back to proper higher resolution.
Thanks.

---

### Post by iaculallad on 2008-07-24
> **flyingsolo said:**
> My question:  Why did the fsck cause my screen resolution to revert to low?

Possible reason for fsck to cause your low resolution could be corrupted video configuration files/settings.

Try the terminal command below to rewrite your /etc/X11/xorg.conf file. Make sure you choose the correct driver when asked. Or you could just press the Enter key to accept default settings:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by flyingsolo on 2008-07-24
Thanks for the suggestion but nothing has changed--still running in low res.  My system had been stable until this & I hadn`t changed anything lately so not sure why this would occur.

Hey!  I fixed it myself--what a surprise.  A while ago I had installed Envy but it messed things up & so I removed it.  Just a few days ago the auto updates included an update to 
fglrx-kernel-source-envy
which I just now removed and all is fixed again.
Thanks for help anyway.

---

