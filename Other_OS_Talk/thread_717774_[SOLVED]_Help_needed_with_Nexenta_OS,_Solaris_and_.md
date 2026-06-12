---
title: "[SOLVED] Help needed with Nexenta OS, Solaris and PC-BSD in VirtualBox"
date: 2008-03-07
forum: Other OS Talk
---

### Post by the8thstar on 2008-03-07
Hello,

I have installed several OSes in VirtualBox for evaluation purposes but I'm having several problems:
[B]
1. Nexenta[/B]

I can install everything just fine. However, after reboot, I had to enter my login and password, which I did. After that nothing happens and I'm stuck with the command line. Is there a way to activate the desktop from there (Gnome)?

[B]
2. PC-BSD[/B]

Sleek install, cool beans. However after reboot, the VM crashes with a critical error. Is there a fix?

[B]
3. Solaris 10[/B]

Install took more than 24 hours. Looks very strange to me, especially when Solaris VM had 20Gb and 1024Mb RAM allocated to it. Then the OS runs but is slowwwwww. Is this normal?

As always, your feedback will be very appreciated.

---

### Post by igknighted on 2008-03-07
Never used VB... did you search for compatibility with these OS's first?  I know in VMWare you have to tell it what OS you will use, as settings need to be changed.  VB might have something similar.

Also, Nexenta isn't worth much.  Most apps don't really work right.  Also, I don't know if ported the VB video driver, might explain why you only get a terminal and no xserver.  If you really want to try Solaris, the OpenSolaris Project Indiana is the only thing going right now that has real promise as a Desktop OS.

---

### Post by jinx099 on 2008-03-08
> **the8thstar said:**
> Hello,

I have installed several OSes in VirtualBox for evaluation purposes but I'm having several problems:
[B]
1. Nexenta[/B]

I can install everything just fine. However, after reboot, I had to enter my login and password, which I did. After that nothing happens and I'm stuck with the command line. Is there a way to activate the desktop from there (Gnome)?


Try "gnome-session &" on the command line.  I might try this out later in VBox, if I do I'll let you know if I can help any more.

> 
[B]
3. Solaris 10[/B]

Install took more than 24 hours. Looks very strange to me, especially when Solaris VM had 20Gb and 1024Mb RAM allocated to it. Then the OS runs but is slowwwwww. Is this normal?


What are your system specs?

---

### Post by p_quarles on 2008-03-08
PC-BSD (based on FreeBSD) currently does not work with Virtualbox. It says so right on Virtualbox's home page.

---

### Post by the8thstar on 2008-03-15
Thanks guys for your replies. Since this topic seems to be heading in the same direction as another I opened recently, I invite you to follow the discussion here :

[http://ubuntuforums.org/showthread.php?p=4521319#post4521319]("http://ubuntuforums.org/showthread.php?p=4521319#post4521319")

--END--

---

