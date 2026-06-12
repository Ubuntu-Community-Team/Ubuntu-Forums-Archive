---
title: "Acer netbook won't boot into Ubuntu"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by law086 on 2012-09-27
Hi folks,

I have an Acer Aspire One netbook currently running Windows 7.  I just installed Ubuntu using the Windows installer.  The first time I booted into Ubuntu the bottom of my screen was black and the top 1/2 sort of showed the desktop, but had very bad mouse ghosting.  So I rebooted and now after the purple boot screen, the LCD just goes black and I'm stuck.  All reboots after this do the same thing.  I tried to wipe the installation and install again, same result.  Seems like something with a video driver, but I wouldn't even know where to start to fix this with Linux.

I'm a pretty seasoned PC guy, but don't know much about Linux, so any help would be appreciated.

Thanks!

---

### Post by snowpine on 2012-09-27
Welcome to the forums!

A good troubleshooting step is to boot Ubuntu in "Live" mode (try without installing) and use it for a while to identify any problems with video, wifi, etc. Give that a try and post back.

It would also be helpful if you identified which model Acer you have, as the Aspire product line has several different models.

---

### Post by TenPlus1 on 2012-09-27
This link may help with your graphics problem:

[http://ubuntuforums.org/showthread.php?t=1204386&page=2](http://ubuntuforums.org/showthread.php?t=1204386&page=2)

---

### Post by mikewhatever on 2012-09-27
Looks like you have a GMA500 based machine. Check out [the wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") for workarounds.

---

### Post by law086 on 2012-09-27
Hi folks, thanks so much for the replies.

I have a ZA3.. if that helps.  I'll try what was suggested and post back!

---

### Post by snowpine on 2012-09-27
Unfortunately I have no experience with the GMA500 so I'm out of suggestions, good luck! :)

---

### Post by law086 on 2012-09-27
> **mikewhatever said:**
> Looks like you have a GMA500 based machine. Check out [the wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") for workarounds.

OK, trying to follow the steps on the wiki.

Tried to execute this command:

gksudo gedit /etc/default/grub

... and got "gksudo: 2060: Gtk-WARNING **: cannot open display:

I should mention that I got to the terminal window by doing CRTL-ALT-F1.  I hope that was the right way to enter it.

Any help?

---

### Post by snowpine on 2012-09-27
No, you cannot use graphical apps (like gedit) in a TTY window like CTRL-ALT-F1.

You need to be in a graphical environment and then you can press Alt+F2 to type the command, or if you prefer, open a terminal from Applications->Accessories->Terminal or Ctrl+Alt+T.

---

### Post by mikewhatever on 2012-09-27
> **law086 said:**
> OK, trying to follow the steps on the wiki.

Tried to execute this command:

gksudo gedit /etc/default/grub

... and got "gksudo: 2060: Gtk-WARNING **: cannot open display:

I should mention that I got to the terminal window by doing CRTL-ALT-F1.  I hope that was the right way to enter it.

Any help?

After getting "to the terminal window by doing CRTL-ALT-F1", you are supposed to restart Xserver with 'sudo service lightdm restat'.

That should bring you back to a functional graphical desktop, where you can run 
'gksudo gedit /etc/default/grub' and apply the permanent workaround.

---

### Post by law086 on 2012-09-28
Thanks for the help folks, sorry to the newbieness.

I was able to solve my issue.  I pretty much followed exactly what this thread suggests:

[http://ubuntuforums.org/showthread.php?t=1970278](http://ubuntuforums.org/showthread.php?t=1970278)

---

### Post by law086 on 2012-09-28
BTW (and maybe I should start a different thread for this) - performance is pretty poor and that's very unexpected.  In fact, I'd say Windows 7 runs faster than Ubuntu is running.  I'm not sure if there's anything I can do to solve that, but I'm open to suggestions.

---

### Post by mikewhatever on 2012-09-29
Unexpected? Why so? Of cause W7 works better on GMA500, Intel provides a working graphics driver for it. It should be possible to improve responsiveness by disabling suff, but that wouldn't help much if you were planning to use Ubuntu on that netbook for video playback. Ulimately, it's all up to the usage.
Gma500 netbooks could have been realy nice multimedia machines, if only there had been a decent driver support.

---

### Post by snowpine on 2012-09-29
Based on everything I've heard about GMA500 (I've never tried it personally) I would seriously consider whether Windows is capable of meeting your needs.

---

