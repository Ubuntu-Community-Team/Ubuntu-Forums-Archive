---
title: "Kernel Havoc? 386/Generic"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by choboja on 2008-10-24
Hi,
I noticed my machine was slow and on checking found that I have only one CPU reported. I looked at the logs and found that there was a comment about NR_CPUS set to maximum 1 and so second was ignored. I was booting into 2.6.24.21-386 and apart from the speed and the lack of any sound, pretty much everything worked.
I tried to boot into the 2.6.24.21-generic and it boots fine and reports two cpus and my sound icon isn't showing muted - grrreat.....except my desktop (gnome/compviz) is completely dead. Occasionally I can click on a desktop item, but it soon dies. If I switch to a another terminal (ctrl-alt-f<n>) and back, I get the background image and top and lower panels, but no icons - not even on the desktop.
Please help!
Where do I start looking??
TIA

MoBo: Gigabyte GA-G31M-S2L
Grphx: MSI NV8400GS (Nvidia)
Disps: [DVI]LCD Vx2255wmh + [VGA]CRT Generic

---

### Post by choboja on 2008-10-26
Looks like this may have been a problem with the nvidia drivers not being compiled for the kernel. Ok for 386 (supplied binary).
Nvidia's site supplied an install script whcih needed X to be off (sudo /etc/init.d/gdm stop did the trick) and nicely compiled a new binary for me.
Did all this on a clean machine, so I now have to see if I can reclaim my old box!

---

### Post by handydan918 on 2008-10-26
Thank you so much for posting back with the solution. You have done well.
How embarrassing that no one replied in that time...

---

### Post by jespdj on 2008-10-27
> **handydan918 said:**
> How embarrassing that no one replied in that time...
What do you mean?

Don't forget that people who are answering questions here are volunteers from all over the world, and not employees who are paid to provide support here. Nobody has any obligation to answer any questions. You can't claim any right to get an answer within a certain amount of time. Nobody can be embarrassed because a question is not answered.

---

### Post by choboja on 2008-11-01
Just an update....
I had problems transferring my solution back to my original system. 
I compiled the new driver configured and installed it and could run the desktop fine from the generic kernel. However, when the system was rebooted I had startup problems and if I did get the desktop running, it would fall over pretty quickly.
Looking at dmesg I had a message that the Nvidia API did not match those of the module and it seems that the old driver was being reloaded.
After quite a bit of uninstalling and deleting anything restricted / nvidia I finally got the new driver to 'stick'.

---

### Post by Crafty Kisses on 2008-11-01
> **jespdj said:**
> What do you mean?

Don't forget that people who are answering questions here are volunteers from all over the world, and not employees who are paid to provide support here. Nobody has any obligation to answer any questions. You can't claim any right to get an answer within a certain amount of time. Nobody can be embarrassed because a question is not answered.

Very good point, and it isn't embarrassing because the original poster has now solved his problem and has probably helped a lot of other people, not sure why you would say "embarrassing".

---

