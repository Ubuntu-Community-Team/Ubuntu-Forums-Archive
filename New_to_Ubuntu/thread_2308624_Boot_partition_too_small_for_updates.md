---
title: "Boot partition too small for updates"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by dipper2 on 2016-01-04
I'm not totally new to Ubuntu but I am relatively inexperienced.

I purchased an HP computer with Ubuntu pre-installed. It has a separate boot partition which is only 210MB. After a couple of updates it was full so with a bit of help from searching these forums I found that I could remove old kernels using Synaptic Package Manager. However, the partition has slowly filled until I no longer have enough space to update despite removing all old kernels. This is /boot as shown in the terminal.

```
jonathan@jonathan-HP-280-G1-MT:~$ ls /boot
abi-3.13.0-73-generic                  initrd.img-3.13.0-68-generic.old-dkms
autoexec.bat                           initrd.img-3.13.0-70-generic.old-dkms
command.com                            initrd.img-3.13.0-71-generic.old-dkms
config-3.13.0-73-generic               initrd.img-3.13.0-73-generic
DPC14WWDORL602.ini                     initrd.img-3.13.0-73-generic.old-dkms
fdconfig.sav                           kernel.sys
fdconfig.sys                           memtest86+.bin
grldr                                  memtest86+.elf
grub                                   memtest86+_multiboot.bin
grub.exe                               splash.gz
hp                                     swsetup
initrd.img-3.13.0-65-generic.old-dkms  System.map-3.13.0-73-generic
initrd.img-3.13.0-66-generic.old-dkms  SYSTEM.SAV
initrd.img-3.13.0-67-generic.old-dkms  vmlinuz-3.13.0-73-generic
jonathan@jonathan-HP-280-G1-MT:~$ 

```

What can I remove from these to create more space and how (in simple terms please) do I do it? There is currently 63MB free space and the next update requires just over 62MB. I feel that is too close for comfort.

Many thanks.

---

### Post by Josquin69 on 2016-01-04
Dear dipper2,  The easiest solution for removing old kernels is installing Ubuntu Tweak. It has a janitor tab which offers options for cleaning your system including removal of old kernels. See [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) for more information. You can (but do not have to) install the latest version of the program by adding a PPA: See [http://www.unixmen.com/after-a-fresh-install-of-ubuntu-1010-maverick-meerkat-configuration-made-easy-with-ubuntu-tweak/](http://www.unixmen.com/after-a-fresh-install-of-ubuntu-1010-maverick-meerkat-configuration-made-easy-with-ubuntu-tweak/) for more details.  Open a terminal and enter the following commands:   ```

sudo add-apt-repository ppa:tualatrix/ppa 
sudo apt-get update
 sudo apt-get install ubuntu-tweak  
```       Kind regards, Josquin

---

### Post by westie457 on 2016-01-04
Hi dipper2
How did you manage to get some Windows .exe and some other non-standard files into your /boot partition?

---

### Post by grahammechanical on 2016-01-04
You only have 1 valid Linux kernel but you also have files remaining from the kernels that you removed. These are the files you keep if you wish to still be able to load Ubuntu.
[SIZE=2]
> [/SIZE]abi-3.13.0-73-generic; config-3.13.0-73-generic;
System.map-3.13.0-73-generic; vmlinuz-3.13.0-73-generic;
initrd.img-3.13.0-73-generic

These also you should keep

> memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin

I cannot say anything about the other files as I do not know why they are there & I do not have a separate boot partition myself. 

Does the next update include an upgrade to the kernel? If it does not then it should not be putting anything in this partition.

Regards.

---

### Post by mörgæs on 2016-01-05
Have you tried 
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```?

---

### Post by dipper2 on 2016-01-05
> **westie457 said:**
> Hi dipper2
How did you manage to get some Windows .exe and some other non-standard files into your /boot partition?

I have no idea. I assume HP put them there. There is only Ubuntu installed. It's not dual booting with Windows.

---

### Post by dipper2 on 2016-01-05
Thanks for all the suggestions. I'll give these a go and let you know how I get on.

Is there a reason the boot partition is so small? HP did exactly the same on my previous computer which crashed on an update. I managed to wipe the drive, repartition it using a youTube guide and reload Ubuntu. It ran faultlessly after that. I only upgraded because the processor was too slow. I tried to wipe the drive on this computer when I bought it but HP have somehow protected it. I would prefer to do that. This tiny boot partition is a pain.

Edit - I'll do a back-up first!

---

### Post by Tadaen_Sylvermane on 2016-01-05
Would highly advise re partitioning if possible and just leaving everything in a single partition. maybe a partition dedicated to /home or /data or something. there is zero reason for home users to have complicated partition structures. it usually leads to this exact problem in my experience. "My boot partition is full" is a regularly occurring topic on these and many other linux forums.

---

### Post by ian-weisser on 2016-01-05
> **dipper2 said:**
> Is there a reason the boot partition is so small?

Yes. Ubuntu cannot boot from LVM or encrypted partitions. If you choose those during install, you get a small non-LVM, non-encrypted /boot partition.
The bug for /boot filling with old kernels is [LP #1357093]("https://bugs.launchpad.net/bugs/1357093"). It's in process of getting fixed.

The basic theory of what's happening is simple:
Aptdaemon queues package actions. Autoremove is at the back of the  queue. Any failure in a package action (like 'no space left on device')  aborts the entire remaining queue.

So regularly, before your /boot is full, run autoremove. Every two  weeks. Every day. Whenever, but regularly. Or enable the unattended-upgrades setting  to run autoremove daily for you.

Since your /boot is full, use dpkg -S to figure out which package one of those old kernel-dkms files belongs to. Use dpkg to remove that old package, freeing enough space for the queued apt  install to complete, then autoremove can run and happily remove all the  rest of the obsolete packages.

---

### Post by dipper2 on 2016-01-05
> **mörgæs said:**
> Have you tried 
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```?

Neither of these had any effect I'm afraid.

---

### Post by dipper2 on 2016-01-05
> **ian-weisser said:**
> Since your /boot is full, use dpkg -S to figure out which package one of those old kernel-dkms files belongs to. Use dpkg to remove that old package, freeing enough space for the queued apt  install to complete, then autoremove can run and happily remove all the  rest of the obsolete packages.

Thanks for the link to the bug. That makes sense even to me.

I tried using dpkg -S but I must have done something wrong as I just got an error message.

---

### Post by dipper2 on 2016-01-05
> **grahammechanical said:**
> Does the next update include an upgrade to the kernel? If it does not then it should not be putting anything in this partition.

Regards.

I assume it does as it warned me there wasn't enough space to update.

---

### Post by ian-weisser on 2016-01-05
> **dipper2 said:**
> I tried using dpkg -S but I must have done something wrong as I just got an error message.

dpkg -S /full/path/to/file

Example: dpkg -S /boot/initrd.img-3.13.0-65-generic.old-dkms

---

### Post by dipper2 on 2016-01-06
> **ian-weisser said:**
> dpkg -S /full/path/to/file

Example: dpkg -S /boot/initrd.img-3.13.0-65-generic.old-dkms

Thanks. I'll give that another go.

---

### Post by dipper2 on 2016-01-06
> **ian-weisser said:**
> dpkg -S /full/path/to/file

Example: dpkg -S /boot/initrd.img-3.13.0-65-generic.old-dkms

I tried them all from 65 through to 73 and got a similar message for them all:

```
dpkg-query: no path found matching pattern /boot/initrd.img-3.13.0-65-generic.old.dkms
```

---

### Post by dipper2 on 2016-01-06
> **Tadaen_Sylvermane said:**
> Would highly advise re partitioning if possible and just leaving everything in a single partition. maybe a partition dedicated to /home or /data or something. there is zero reason for home users to have complicated partition structures. it usually leads to this exact problem in my experience. "My boot partition is full" is a regularly occurring topic on these and many other linux forums.

I wanted to wipe my hard drive clean and repartition it myself but HP have set up the computer so that I can't do that. I'm sure there will be a way round this if I can't clean the boot directory.

---

### Post by ian-weisser on 2016-01-06
> **dipper2 said:**
> dpkg-query: no path found matching pattern /boot/initrd.img-3.13.0-65-generic.old.dkms
Never rm files that were placed by the package manager...but the response indicates that those files were not placed by the package manager. rm them. 
Don't rm the .dkms file that corresponds to your current kernel.

---

### Post by dipper2 on 2016-01-07
> **ian-weisser said:**
> Never rm files that were placed by the package manager...but the response indicates that those files were not placed by the package manager. rm them. 
Don't rm the .dkms file that corresponds to your current kernel.

Brilliant. That worked. Thanks very much.

To summarise in case anyone else has this problem:

Use dpkg -S to see which .dkms files were not placed by the package manager

```
dpkg -S /full/path/to/file
```

The response I got was:

```
dpkg-query: no path found matching pattern /boot/initrd.img-3.13.0-65-generic.old.dkms
```

This indicated that that file (and others with a similar response) could be deleted. Keep the .dkms file that corresponds to the current kernel.

Delete the unwanted files with

```
sudo rm /full/path/to/file
```

I ended up with 134MB free space (36.1% full) in my boot partition. After updating it went to 72MB free (65.7%) so it was quite a large update relative to the size of the partition.

Many thanks again to ian-weisser and to the other contributors. Even if a suggestion didn't work, I learnt a little bit more about Ubuntu. I have marked the thread well and truly solved.

---

