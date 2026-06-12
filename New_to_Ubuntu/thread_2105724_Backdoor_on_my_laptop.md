---
title: "Backdoor on my laptop?"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by joco1500 on 2013-01-16
Hello all.

I have a old-ish Dell laptop and put Ubuntu 11.10 on it. Works great. It is as fast as my windows 7 laptop that i use for school. But i let my friend use my Ubuntu laptop and he is kinda a douche. He is a computer guy and i think that he put a backdoor on my laptop. I keep finding things lost and other things downloaded and things in other folders when i go to use them. 

I just want a way to find it and i don't want smart-*** responses.
I just want to get my computer fixed and maybe i might put a backdoor on his windows xp set up.

---

### Post by Gster4 on 2013-01-16
did this guy have root access?
use the system monitor and look for weird proccess running.

---

### Post by CharlesA on 2013-01-16
Did he use the machine under your user or as guest?

If he logged in as your user, he could run anything as your user and mess with anything in your home directory.

---

### Post by drawkcab on 2013-01-16
reinstall.

---

### Post by squakie on 2013-01-16
> **drawkcab said:**
> reinstall.

+1.  Your description makes it sound like a lot of things are screwed up - there isn't a single answer we can give you.  I would suggest you back up any data you want to save, then do as drawcab said and resintall - perhaps even with 12.04lts.

---

### Post by hydn79 on 2013-01-16
+1 reinstall AND tired of saying this to people... enable the BIOS password guys!!!

I don't use Linux password, just BIOS password which pops up BEFORE it boots from any drives, or boot media.

---

### Post by offgridguy on 2013-01-16
> **drawkcab said:**
> reinstall.
+1

---

### Post by d4rk0wl on 2013-01-16
> **hydn79 said:**
> I don't use Linux password, just BIOS password which pops up BEFORE it boots from any drives, or boot media.

Agreed, it is a good measure of security that way nobody can boot off of a USB and tamper with various system files on drive.

---

### Post by mastablasta on 2013-01-17
> **hydn79 said:**
> 
I don't use Linux password, just BIOS password which pops up BEFORE it boots from any drives, or boot media.
 
 
that's just silly! basically you closed your computer so noone bot you can boot it. on the other hand once you boot into it you opened up to internet and malware. 
 
linux password is there to identify to computer that the person with admin rights is trying to change system files and not some malware. as you removed this security layer you basically "said": "anything can automaticly run on my mashcine, even malware. it doens't need my permission. and i give it full root access to my computer and data."
 
does that seem like a good idea?
 
win98 was running like that and most newer preinstalled windows do that by default the result is - plenty of infections in that OS.

---

### Post by NikTh on 2013-01-17
[mastablasta]("http://ubuntuforums.org/member.php?u=964486") , maybe **hydn79 **means that he/she is using the autologin feature (in login screen). Because I'm not very sure , but I think you cannot even install Ubuntu if you don't set a password. 

Password is needed to install software and you cannot leave the password blank , because you will have problems. On the other hand , if you are an experienced user and you hacked the sudores file with NOPASSWD , then is up to you. 

As for the BIOS password and/or root password , these are extra security that someone can take against a guy that he/she not trust with the PC powered on,  in his hands.  
BIOS password will prevent him to boot from a live media and root password will prevent him to boot into recovery mode and use the root console. 

As for the OP , well... we don't know how much damage did this guy , so better would be to re-install.

---

### Post by Warren Hill on 2013-01-17
Backup and re-install.  If you don't have a password then this guy had root access and could have done anything.

Make sure you have a password that's not easy to guess on any account that has sudo access.  This includes the first account.  You can set your computer not to require your password to logon and only use it when you want to update and make changes if you wish but a password is essential if you want any security.

Personally I would require the password on start-up: that way you use it regularly so won't forget it when you really need it.  If other people need to use your computer give them their own account without sudo privileges. 

Remember physical access is root access so don't give your computer to anyone you don't trust.

Depending on your computer you may be able to set a BIOS password so that its required on every boot, or just to change boot order.

Finally you can prevent recovery console if you give root a password.

---

### Post by hydn79 on 2013-01-17
> **NikTh said:**
> [mastablasta]("http://ubuntuforums.org/member.php?u=964486") , maybe **hydn79 **means that he/she is using the autologin feature (in login screen).

Thanks NikTh, I didn't think I would have to explain that, Sorry. :/ My user is hydn and I su into root, personally I don't see the point for having another password "prompted" again after the BIOS password is entered. I've never tried installing Linux that way actually. I use Ubuntu on our desktop home PC. But I type this on my ArchLinux laptop, both have BIOS passwords and autologin, so I use su when needed.

---

