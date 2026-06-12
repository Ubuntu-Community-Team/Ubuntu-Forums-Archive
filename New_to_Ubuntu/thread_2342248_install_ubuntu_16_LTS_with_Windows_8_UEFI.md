---
title: "install ubuntu 16 LTS with Windows 8 UEFI"
date: 2016-11-05
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2016-11-05
Well, every system is unique, so I am posting the same question.

And I have doubts , so let me begin.

A windows 8 user(Enabled of UEFI, Secure boot, fast boot) thought to install ubuntu.

As precaution, installed along with windows 8 , installation smoothly done with support of this forum .

succesfully I got a problem , it directly booted to windows 8 , without showing boot for ubuntu options.

now i am planning to install ubuntu fully on C: partition alone so remaining partition don't get affected 

Am struck to do this on 3rd step in installation of ubuntu, because clicking on the wrong partition may wipe out the data

also i am confused of terms and giving space to home and swap , is that must ?? 

System Tech Spec:

RAM:4GB , hard disk:250GB, MOTHERBOARD: ASUS H81MCS


what shoud i do now ?

apologies if any wrong in qn. from a newbie

---

### Post by RobGoss on 2016-11-05
Hello and welcome, I'm a bit confused by your post are you trying to dual boot this machine? and if so I know you mentioned you already have **Ubuntu 16.04** installed along side Windows 8, what other OS are you thinking about installing or are you wanting a single boot?

---

### Post by ajgreeny on 2016-11-05
See Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and tell us what partitions and bootloader situation you have at present.

Without that information we will be struggling to help you, apart from telling that it is preferable, if not essential, as far as I'm aware, to turn of **Fast startup** in Windows and to disable **Secure Boot**, at least while installing.

---

### Post by weirdygeekpsych on 2016-11-06
as a newbie i could face some problems, so i tried installing ubuntu along with windows 8.. just like i though i got a problem on windows UEFI, fast boot. now i disabled those and installed ubuntu alone. thanks for your reply.

---

### Post by weirdygeekpsych on 2016-11-06
hello ajgreeny

I have installed ubuntu 16 alone, by partitioning 75 gb for home, and dedciated 8gb for swap. now it is working fine. 

at first boot after installing ubuntu , ubuntu didnt load due to boot priority order changed in boot. later i changed and its working fine. is there anything i am missing on installing or after installing ?

---

### Post by RobGoss on 2016-11-06
I'm assuming if you had to change the boot order to get your machine to boot into Ubuntu you're not seeing the **Grub **menu which allows you to choose Windows and Ubuntu

---

### Post by weirdygeekpsych on 2016-11-07
I have deleted windows and install ubuntu , now ubuntu is directly loading without any trouble

---

