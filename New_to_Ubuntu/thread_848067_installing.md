---
title: "installing"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by sbloomfield on 2008-07-03
i have downloaded the desktop edition 8.0.4 and burnt the image to CD.  i'm trying to install it onto VMWare version 6.04 which i understand there are some issues due to the new kernal in this version of ubuntu.  it seems to install to the point where i get a login prompt but what is the username and password for the account to finish installing?  i've done a bit of hunting around the net and it looks like i should be logging in using the sudo command but i haven't got a clue. any idea's??

---

### Post by hakko on 2008-07-03
On installing it should have asked you to set your username and password.  I think if you entered your name as "John" during installation, your username would be the same "John".  

You can also login as "root" and try entering any passwords that you setup on installation.

---

### Post by plucky on 2008-07-03
> **sbloomfield said:**
> i have downloaded the desktop edition 8.0.4 and burnt the image to CD.  i'm trying to install it onto VMWare version 6.04 which i understand there are some issues due to the new kernal in this version of ubuntu.  it seems to install to the point where i get a login prompt but what is the username and password for the account to finish installing?  i've done a bit of hunting around the net and it looks like i should be logging in using the sudo command but i haven't got a clue. any idea's??

It should not ask you for a username and password until you reboot after the installation.

You should re-burn the ISO at the lowest speed no more than 4X and check the integrity of the CD by booting it and selecting the check CD option.

Also did you MD5SUM the downloaded ISO to make sure it is OK?

You should do these steps to save you problems later on.


Good Luck

---

### Post by jbenuntu on 2008-07-06
I get the same problem. The ISO CD is correct via Checksum, and I burned it using two seperate programs Infrarecorder, and Nero, both at 4x speed or lower. And I still can not log on. Wubi installation does not work either.

---

### Post by sbloomfield on 2008-07-08
Hi,

tried burning the image again and checking it.  it all seems to be OK.  the only thing i'm asked when trying to install it is the language which it assumes is English and then if i want to run it without changing anything on my PC, install ubuntu and a couple of other options.  i'm wondering as i tried looking about the forums if i've actually used the correct ISO image, there seems to be several depanding on the processor of the PC.  i'm using a intel centrino Duo, which i think means that i should use the i686 ISO.  could anyonly confirm?

---

### Post by plucky on 2008-07-08
> i'm using a intel centrino Duo, which i think means that i should use the i686 ISO. could anyonly confirm? 


Is that a 64 Bit processor?


For a PC there are two versions of Desktop Ubuntu.One for 32 Bit processors and one for 64 Bit processors.The 32 Bit (X86) version can be used on both type of processors,while the 64 Bit version (AMD64)can only be used on 64 Bit processors.

Assuming you have downloaded the 32 Bit version,that should work on any AMD or Intel PC,but you should make sure the download is checked using the MD5SUM on the ISO file and then burn to CD or DVD at no more than 4X speed.Then boot the CD and select the check CD option to make sure the CD is OK.

Good Luck

---

### Post by jbenuntu on 2008-07-26
still unable to log on........I have ordered and recieved the Ubuntu disk: Ubuntu 8.04 LTS Desktop Edition. I STILL get the username and password screen and i STILL cannot log on. WTF.

system: Microsoft Windows XP
Home Edition
Version 2002
Service Pack 2
eMachines
T6212
AMD Athlon(tm)64 Processor
3200+
1.99 GHz, 384 MB of Ram

---

