---
title: "Can I upgrade to a 64 bit version easily?"
date: 2013-11-19
forum: New to Ubuntu
---

### Post by kkelly77 on 2013-11-19
I am currently running a 32 bit version of Ubuntu 12.04 LTS.

I have recently discovered that my CPU is actually a 64 bit Core™2 CPU T5600 (D'oh!)

Is it possible to upgrade to a 64 bit version of Ubuntu 12.04 without having to do a full reinstall?

I have my boot partition on a seperate partition to my /home. See gparted screenshot. Thanks for the advice.

[IMG]http://i39.tinypic.com/16hp935.jpg[/IMG]

---

### Post by Frogs Hair on 2013-11-19
The short answer is no it requires an installation of the 64 bit ISO. The main advantage to 64 is it accommodates of more memory. Most processors are 64 bit now days.
 
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by Allavona on 2013-11-19
Swap broken?:lolflag:

---

### Post by kkelly77 on 2013-11-19
> **Frogs Hair said:**
> The short answer is no it requires an installation of the 64 bit ISO. The main advantage to 64 is it accommodates of more memory. Most processors are 64 bit now days.
 
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

So I can't just install on the "/" partition and leave my home partition intact?

---

### Post by kkelly77 on 2013-11-19
> **Allavona said:**
> Swap broken?:lolflag:

Thought that might require a seperate thread :P

Got a fix for it?

---

### Post by philinux on 2013-11-19
> **kkelly77 said:**
> So I can't just install on the "/" partition and leave my home partition intact?

Yes you can. At the partitioner choose manual and tell it to use the partitions as ext4 as they are now but only choose to format / and or /boot.

---

### Post by kkelly77 on 2013-11-19
> **philinux said:**
> Yes you can. At the partitioner choose manual and tell it to use the partitions as ext4 as they are now but only choose to format / and or /boot.

Oh right, so I can do that?

Do I **have** to format the /boot?

---

### Post by philinux on 2013-11-19
> **kkelly77 said:**
> Oh right, so I can do that?

Do I **have** to format the /boot?

I've never had a /boot partition.

---

### Post by kkelly77 on 2013-11-19
> **philinux said:**
> I've never had a /boot partition.

I only have it because I used this 'how to' dual boot guide -  [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/)

---

### Post by philinux on 2013-11-19
I dual boot win 7 and have no problem.  I have / /home and a swap partition.

---

### Post by kkelly77 on 2013-11-19
> **philinux said:**
> I dual boot win 7 and have no problem.  I have / /home and a swap partition.

Good to know.

TBH I don't need the /boot partition as I only use LTS versions of Ubuntu. Only put it on because the how to guide said so.

Will I need to reinstall applications etc if I just install the 64 bit version on the "/" partition?

---

### Post by philinux on 2013-11-19
> **kkelly77 said:**
> 

Will I need to reinstall applications etc if I just install the 64 bit version on the "/" partition?

Yep it'll be a clean install. I must write a script to install what I usually do.

---

### Post by deadflowr on 2013-11-19
> **kkelly77 said:**
> 
Will I need to reinstall applications etc if I just install the 64 bit version on the "/" partition?

Even if you could simply run the apps you have, I would advice purging them and installing the 64-bit version of the apps anyway.
Though running 32-bit in 64-bit isn't a major problem, running apps native to the system arch is best.
(most of the time)

---

### Post by oldfred on 2013-11-19
You want to extract a list of installed apps. If same version there should be few issues. But a major upgrade may have old apps you do not want or need to reinstall as they have changed like from OpenOffice to LibreOffice.
It is just a text file & you may want to remove anything that is specifically 32 bit also. If part of default install, it will not reinstall it even if listed again.

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

My backup is just to do a new install and restore system to as it was.
      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

   mySql Install & backup -  LHammonds
[http://ubuntuforums.org/showthread.php?t=1983344&p=11951852#post11951852](http://ubuntuforums.org/showthread.php?t=1983344&p=11951852#post11951852)

---

