---
title: "Hi all - typical newbie question follows........"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by stelfy on 2012-05-22
Installed 12.04 over the weekend on my old dell mini 10 after 4.5 years of running windows it deserves a break from all the necessary periodic reinstalls of OS and AV software

Installed using WUBI, all went well, dual boot  with old windows OS, applied the fix for the Wifi card driver (Broadcom), installed VLC and a couple of games with no issues

Question is.... having now established there are no hardware issues (except Wifi card)

A) If I now take the plunge an reinstall 12.04 from scratch using CD does the installation process give me the option to go back to a single partition (currently have 3, windows, old dell/norton/windows recovery and now 12.04) or will I have to use windows recovery and fdisk

B) Does WUBI use information from windows when it installs to identify hardware, and will I be left with a whole load of work to do 

All help appreciated!

Aaron

---

### Post by roelforg on 2012-05-22
1. Depends, do you want to wipe out windows completely? Then just do with option 1 (single partition).
2. Wubi doesn't use windows hw detect, it's ubuntu itself that does the detecting.

---

### Post by ryantierp on 2012-05-22
I suggest you take the plunge. Since you installed using wubi ubuntu is placed on top of the preexisting format of windows wich I have found to slow down Ubuntu to some degree. 
Reinstall fresh from a CD and let Ubuntu use all of the drive.

---

### Post by stelfy on 2012-05-22
Thanks..

Can live without windows on this machine, will miss itunes, but there are other PC's in the house I can use 

Thanks for clarifying the hardware detection process - was worried that 12.04 might have used windows hardware information, because even little things like the function (fn) key and hotkeys for volume/mute, screen brightness, battery condition all function as they should

---

### Post by nothingspecial on 2012-05-22
> **stelfy said:**
>  because even little things like the function (fn) key and hotkeys for volume/mute, screen brightness, battery condition all function as they should

Linux is cool isn't it ;)

---

### Post by philinux on 2012-05-22
> **stelfy said:**
> Thanks for clarifying the hardware detection process - was worried that 12.04 might have used windows hardware information, because even little things like the function (fn) key and hotkeys for volume/mute, screen brightness, battery condition all function as they should

That's all made to work by the linux hardware detection and the kernel modules.

Better explained here. [http://blogas.sysadmin.lt/?p=141](http://blogas.sysadmin.lt/?p=141)

---

### Post by stelfy on 2012-05-22
> **philinux said:**
> That's all made to work by the linux hardware detection and the kernel modules.

Better explained here. [http://blogas.sysadmin.lt/?p=141](http://blogas.sysadmin.lt/?p=141)

Jeez now I know I'm a newbie :)

I tried Redhat a few years ago, downloaded Fedora (redhat 9/10?) bought the giant SAMS book with the intention of becoming a linux convert but the antiquated (win95/98) era laptop I had wasn't the most reliable machine to start with and had no end of problems getting it to work

A few years down the line and it all seems too easy.. almost too good to be true!

Thanks for the input

---

### Post by philinux on 2012-05-22
> **stelfy said:**
> Jeez now I know I'm a newbie :)


Not any more.  :P

---

