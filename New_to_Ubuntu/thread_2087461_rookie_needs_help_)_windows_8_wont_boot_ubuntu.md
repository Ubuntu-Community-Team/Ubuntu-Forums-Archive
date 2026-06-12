---
title: "rookie needs help :) windows 8 wont boot ubuntu"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by jeebuz on 2012-11-23
Hi everyone :) I ve recently bought a amd64 and it came with Windows 8, therefor I´ve been trying these last days to install ubuntu but without any success. I downloaded wubi Windows install and everything goes right untill it gets to the boot ubuntu part.
 
\ubuntu\winboot\wubildr.mbr missing or currupted (the file is there idk whats causing this)
 
I installed wubi on a diferent partition btw, I hope one of u guys knows how to run Linux side by side Windows 8. ty.

---

### Post by edeneen on 2012-11-23
have you tried going into the BIOS and disabling the Windows 8 Secure Boot option before booting to the disc ?   Most Windows 8 machines come with it enabled by default.

---

### Post by jeebuz on 2012-11-23
No I haven´t, thanks for the tip mate :) ill report in soon.

---

### Post by jeebuz on 2012-11-23
Ok mate I´ve disabled Windows secure boot but I still get the same error. I also have kubuntuamd64 1012 on a dvd, im going to give boot from dvd a try now that secure boot is disabled.

---

### Post by jeebuz on 2012-11-23
> **jeebuz said:**
> Ok mate I´ve disabled Windows secure boot but I still get the same error. I also have kubuntuamd64 1012 on a dvd, im going to give boot from dvd a try now that secure boot is disabled.
 
It has succefully booted, now the problem is that kumbuntu keeps loading and loading.... Sugestions?

---

### Post by bcbc on 2012-11-23
> **jeebuz said:**
> Hi everyone :) I ve recently bought a amd64 and it came with Windows 8, therefor I´ve been trying these last days to install ubuntu but without any success. I downloaded wubi Windows install and everything goes right untill it gets to the boot ubuntu part.
 
\ubuntu\winboot\wubildr.mbr missing or currupted (the file is there idk whats causing this)
 
I installed wubi on a diferent partition btw, I hope one of u guys knows how to run Linux side by side Windows 8. ty.

Wubi doesn't work on GPT disks. New Win8 computers with secure boot all use GPT disks.

---

### Post by jeebuz on 2012-11-23
> **bcbc said:**
> Wubi doesn't work on GPT disks. New Win8 computers with secure boot all use GPT disks.
 
So, no Linux for me? : (

---

### Post by oldfred on 2012-11-23
Please see this thread and related links. Just do a full partitioned install.

       Some general info from oldfred and links.
[http://ubuntuforums.org/showthread.php?t=2086883](http://ubuntuforums.org/showthread.php?t=2086883)

    
Do you have the 64 bit version? And are you booting from UEFI, the efi version of Ubuntu,  not the BIOS/legacy/AHCI version?

And what video chip/card do you have. Video issues often cause issues.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by bcbc on 2012-11-23
> **jeebuz said:**
> So, no Linux for me? : (

No Wubi. A normal install works fine. Unless it's a lenovo in which case they hardcoded it to only boot Windows 8 and red hat: [http://mjg59.dreamwidth.org/20187.html](http://mjg59.dreamwidth.org/20187.html)

---

### Post by jeebuz on 2012-11-23
> **oldfred said:**
> Please see this thread and related links. Just do a full partitioned install.
 
Some general info from oldfred and links.
[http://ubuntuforums.org/showthread.php?t=2086883](http://ubuntuforums.org/showthread.php?t=2086883)
 
 
Do you have the 64 bit version? And are you booting from UEFI, the efi version of Ubuntu, not the BIOS/legacy/AHCI version?
 
And what video chip/card do you have. Video issues often cause issues.
 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
Im sorry to be boring u guys with my naabness. What can I say? It seems to boot thru something called GNU/GRUB idk, i think my videocard is onboard the cpu: AMD E1-1200 APU with radeon HD graphics.

---

### Post by jeebuz on 2012-11-23
> **bcbc said:**
> No Wubi. A normal install works fine. Unless it's a lenovo in which case they hardcoded it to only boot Windows 8 and red hat: [http://mjg59.dreamwidth.org/20187.html](http://mjg59.dreamwidth.org/20187.html)
 
bcdc can u please explain to me (nub) whats a normal install? I´m a first timer ^_^

---

### Post by bcbc on 2012-11-23
> **jeebuz said:**
> bcdc can u please explain to me (nub) whats a normal install? I´m a first timer ^_^

Wubi lets you install (and uninstall) easily from within Windows - usually, but not on new computers with secure boot (because of the GPT disks). What Wubi does is to make a 'virtual partition' (actually just a large file that sits on the windows file system) and it dual boots Ubuntu from that virtual partition.

The other 'normal' way to install Ubuntu alongside Windows is by installing to a real partition. This is a little more complex to install - you need to boot from the Ubuntu CD/DVD/USB to install. The installer can do its own partitioning, although some people recommend first making the partitions in Windows and then installing into that. 

If you have secure boot, you have to install with 64-bit Ubuntu.

I would say you should read up on what you need to do to install and then ask questions as needed, but I'd recommend the following first steps:
1. make sure you have a windows repair CD (you can burn one from Window)
2. make sure you have Windows restore disks (you have to create them yourself for most OEM computers, unless you bought the Windows install disks)
3. have a good data backup plan

The other option, is to use a virtual machine from within Windows if you just want to try out Ubuntu.

---

### Post by newb85 on 2012-11-24
A normal/traditional install to a real partition is perhaps a little more complex, but not that much more.

bcbc's three tips are spot-on.  Also, before doing a traditional install, make sure you defragment your Windows partition.

Aside from maybe shrinking the Windows partition, it's not a good idea to do your partitioning from Windows.  (I think you would find Windows incapable of creating an Ext# filesystem, which is what is needed for Ubuntu.)  Creating it from Live media is pretty straight-forward.  Just make sure you are installing alongside Windows.

Edit: Once you have successfully done a real install of Ubuntu, I believe you can uninstall your Wubi install just as you would uninstall any other program in Windows (Add/Remove Programs...)

---

