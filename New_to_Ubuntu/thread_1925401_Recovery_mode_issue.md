---
title: "Recovery mode issue"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by tetrisalphabet on 2012-02-14
BACKSTORY: Okay, in Ubuntu 10.10, I was screwing around with CompizConfig because I'm a graphics ***** and I like transparency. Somehow I managed to make every single thing 100% transparent, meaning I couldn't see anything to make it un-transparent again, so I restarted and used Recovery Mode to boot up with just basic graphics.

Only now that I've fixed the Compiz problem, I can't get back to the previous graphics settings I had. Which isn't really a huge, world-ending issue, but it's still bothering me. Mainly the thing that's bothering me is being unable to switch my ~desktop environment~ from "No visual effects" back to "Normal visual effects". Also anything that's supposed to be partly transparent (libnotify popups, etc.) doesn't display properly either. And yes, I've turned the system off and back on, booted up in normal (non-recovery) mode, and it's persisted.

Wat do

---

### Post by tetrisalphabet on 2012-04-07
Still haven't solved this, for the record. I've been stuck with "No effects" on my "desktop environment", which while not a pressing matter is rather annoying.

---

### Post by kazztan0325 on 2012-04-07
Hi tetrisalphabet,

I would like to ask you...

Have you tried to install and use **"Simple Compizconfig Settings Manager"** (its package name is **'simple-ccsm'**) on your 10.10 machine?

---

### Post by tetrisalphabet on 2012-04-07
I just tried that and it doesn't seem to be a solution. When I try opening the program, the command line spits this out at me:

```
/usr/bin/simple-ccsm:40: DeprecationWarning: Use the new widget gtk.Tooltip
  Tooltips = gtk.Tooltips()
/usr/bin/simple-ccsm:182: DeprecationWarning: Use the new widget gtk.Tooltip
  Tooltips = gtk.Tooltips()
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
/usr/bin/simple-ccsm:415: DeprecationWarning: Use the new widget gtk.Tooltip
  Tooltips.set_tip(self, _("Disabled"))
/usr/bin/simple-ccsm:412: DeprecationWarning: Use the new widget gtk.Tooltip
  Tooltips.set_tip(self, _("Enabled"))

```

And the process freezes up and I have to kill it.

I don't know if the CompizConfig thing is really the issue? I mentioned it for backstory as to how I got into this situation, but I think what's happening is the computer thinks it should be in recovery mode and I can't make it not be anymore.

---

### Post by wildmanne39 on 2012-04-07
Hi, I would reinstall the graphics driver and reset compiz.

Here is a link for resetting compiz.
[http://askubuntu.com/questions/36163/how-can-i-reset-compiz-to-the-default-settings](http://askubuntu.com/questions/36163/how-can-i-reset-compiz-to-the-default-settings)
Thanks

---

### Post by tetrisalphabet on 2012-04-08
Here's where I admit I'm a complete moron, but how do I reinstall the graphics driver?

---

### Post by winh8r on 2012-04-08
Depending on what you have there are a couple of links here for Radeon ATI drivers and for Nvidia drivers:


[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")


Hope this helps.

---

