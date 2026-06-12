---
title: "Installing Ubuntu 14.04 on a blank system"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by Paper Pusher on 2014-05-02
I'm trying to install Ubuntu on a computer which had 12.04 on it before.
The install seems to work but when it restarts it comes up as a blank screen.
What am I doing wrong?
I have reinstalled but nothing seems to work.
Thank you for any help that you can give me.

---

### Post by LastDino on 2014-05-02
A blank screen with prompt or just a hard blank screen? GPU?

---

### Post by Bashing-om on 2014-05-02
Paper Pusher; Hi !

A blank screen on a fresh install is often a graphics driver issue.
Try the boot parameter "nomodeset", and once to the desktop, install the recommended driver.

Boot ubuntu, and as soon as the bios screen clears depress and hold the right shift key -> grub's boot menu; with a non-recovery kernel highlighted press the 'e' key for edit mode -> boot parameters screen; arrow down to the line similar to this " linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff " and arrow across to the terms "quiet splash" and insert also the term nomodeset. Key combo ctl+x to continue the boot process.

How to set NOMODESET:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[INDENT][INDENT]big maybe yes
[/INDENT][/INDENT]

---

### Post by Paper Pusher on 2014-05-03
Thank you for all of your suggestions.  You might say the symptoms have changed.  

I have replaced a network router.  Now other network devices, such as my camera, work correctly.  They were broken before.  

The new symptom is that I get a purple screen with nothing written on it.  I reinstalled Ubuntu 14.04  I chose to erase other previously installed versions and install new version.  

I have not had this problem before.  When I installed Ubuntu 12.04 for the system, it booted up as normal.  What am I doing wrong this time?

---

### Post by LastDino on 2014-05-03
The biggest difference between 12.04 and 14.04 are the kernels, so my guess would be that your drivers may not be playing nice with latest kernels. Try installing latest linux compatible 3rd party drivers if you use added GPU.

---

