---
title: "ubuntu + mandriva"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by djallalnamri on 2008-10-10
*hello all
*my wish is that i could install ubuntu and mandriva on the same pc with what they call double or dual boot in order to have a microdia webcam working on both systems or on one of them
*what i would really like is to be able to have both systems working on my pc because i like very much free and open source softwares
*thanks in advance :)

---

### Post by SuperSonic4 on 2008-10-10
Fair enough :). You can install them in the standard way and then configure the bootloader. Install the distro who's bootloader you want last. I picked mandriva's last since I prefer it to ubuntu's one in terms of editing.

I'm dual booting kubuntu and mandriva :D although on two separate physical drives (**far** easier than using the same disc lol)

---

### Post by Kevbert on 2008-10-10
This should be easily done. I haven't used mandriva but it's just another version of the Linux platform.  Install mandriva using half your hard disk.
Next install ubuntu and when asked about partitioning use guided (use free space option).  Ubuntu is good at detecting another linux distributions and will set up the boot menu automatically (hopefully, barring any problems) for you.

---

### Post by SuperSonic4 on 2008-10-10
The biggest problem I could see is selecting the mandriva option at boot and being taken to that bootloader, always seems to give nasty error 21 when I do it.

---

### Post by Orange_and_Green on 2008-10-10
Hello. Thank you for your interest in Ubuntu and in open source.

There is absolutely no problem with having multiple OSes installed (I have Ubuntu and OpenSUSE :) ). Just follow these steps:

1)Install your "second choice" OS first. Partition manually, and allocate the disk space so there is enough free space for the other OS*
2)Go through the install and set up the OS correctly
3)Install the other OS onto the space you had left free, and let it install the boot loader.

Yes, it's that easy! Have lots of fun :KS

*A possible setup might be something like:
/dev/sda1  -->Mandriva's "/" partition, 4GB minimum, more if you have the space
/dev/sda2  -->swap, around 1GB
/dev/sda3  -->Ubuntu's "/" partition, 4GB minimum, more if you have the space

(and possibly)
/dev/sda4 can be a logical partition that contains some extra logical disks, if you have the space of course, for mount points like /home for both systems

---

### Post by djallalnamri on 2008-10-10
*hello again
*thanks very very much for quick replies
*i have a 160 gb hd
*so the best solution should be a manual partition,ok i hope i will be able to do it
*thanks a lot and see you after the installation):P

---

### Post by djallalnamri on 2008-10-10
*hello again
*i have a question:did i make a mistake using all drive space while installing ubuntu...because this is what i did and something is telling me that i am going to have trouble installing mandriva:(:confused:
*thanks again

---

### Post by overdrank on 2008-10-10
> **djallalnamri said:**
> *hello again
*i have a question:did i make a mistake using all drive space while installing ubuntu...because this is what i did and something is telling me that i am going to have trouble installing mandriva:(:confused:
*thanks again

Hi and I would recommend installing mandriva first then Ubuntu. :)

---

### Post by AdamWill on 2008-10-10
Either way around should work these days - Mandriva's installer has been able to detect and configure Ubuntu in its bootloader since 2008 Spring.

---

### Post by handydan918 on 2008-10-10
> **djallalnamri said:**
> *hello again
*i have a question:did i make a mistake using all drive space while installing ubuntu...because this is what i did and something is telling me that i am going to have trouble installing mandriva:(:confused:
*thanks again

I find it easiest to partition the harddrive first, making notes about what partitions are where. I once had 12 different O/S's on one 120GB drive. 
GRUB rocks!

:guitar:

---

### Post by kansasnoob on 2008-10-10
> **overdrank said:**
> Hi and I would recommend installing mandriva first then Ubuntu. :)

Absolutely!

Whether it's Mandriva, Open Suse, Fedora, etc. - installing Ubuntu last is always best!

Only Ubuntu seems to understand simplicity of installation and how to "auto-grub".

RANT: If it's not Ubuntu based don't bother! You'll be disappointed!

Ubuntu rocks!

---

### Post by bodhi.zazen on 2008-10-10
See this thread for tips on how to configure GRUB :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by djallalnamri on 2008-10-11
*hello
*in fact it was better to install mandriva first then ubuntu,this is i was compelled to do and it works....
*now i am testing both systems and especially video on ubuntu
*many thanks for help

---

### Post by djallalnamri on 2008-10-11
*hello again
*i seem to have trouble with "root" password:is it the one we use when we start ubuntu...
*thanks for help

---

### Post by bodhi.zazen on 2008-10-11
> **djallalnamri said:**
> *hello again
*i seem to have trouble with "root" password:is it the one we use when we start ubuntu...
*thanks for help

In Ubuntu we use sudo

    [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

for a root shell, use 

```
sudo -i
```

For graphical applications use gksu

```
gksu nautilus
```

the password is the same as your log-in password.

---

