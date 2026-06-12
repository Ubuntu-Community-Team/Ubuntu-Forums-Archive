---
title: "initramfs"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by kb7smm on 2008-05-03
Greetings, I just loaded Ubuntu 8.04 from Wubi on my new Gateway laptop. durning installation the program stopped with the command initramfs: type help for a list of commands. Well I didn't get any of the commands to work so I shut down my computuer and rebooted. What is initramfs? if this happens again which command should I use? 

Jim

---

### Post by mrzaius on 2008-05-03
That's a rather odd error - You might just want to retry the installation. That said, check this thread out, too: [http://ubuntuforums.org/showthread.php?t=587168](http://ubuntuforums.org/showthread.php?t=587168)

---

### Post by ocean223 on 2008-05-03
I also went nuts with this when I installed under wubi. Try re-booting windows and letting it start normally. Make sure all your stuff loads before shutting it down. Then re-boot Ubuntu.  I have no idea why but it seemed to work for me.  

I've since re-installed Hardy in it's own partition. Have not had an " initramfs" or otherwise known as "busybox" error since.

Hope this helps.:)

---

### Post by kb7smm on 2008-11-13
/Well this same initramfs re-appears from time to time. but i did figure that i neede to use the command reboot when this happens rather than just shutting down the computer. 

I also keep getting a error 110 message. regardless of posts here  and elsewhere for help this is none. So at this point i may want to uninstall ubuntu. i may reinstall at a later date but its a non-functioning OS from me.

---

### Post by bennachie on 2008-11-13
Interesting - I did not come across this problem when using Wubi (that is, when running XP and installing Ubuntu as a "normal" application within Windows). However, I did experience it when attempting a normal LiveCD installation. In the latter case, the problem was resolved by hitting F6 when the boot dialog appeared, and appending the following commands to the list of parameters that was presented at that point.

all_generic_ide floppy=off irqpoll

This solution has been around in the forum for some time (sadly, I can claim no credit at all for devising it) and seems to work for most people who run into the dynamic duo of "busybox" and "initramfs".

---

