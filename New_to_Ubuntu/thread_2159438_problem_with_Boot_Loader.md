---
title: "problem with Boot Loader"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by tusharkoshti on 2013-07-03
Hello friends,

I am using Win 7 and Ubuntu 13.04. Currently I tried to install CentOs 5.5. 
For that I shrinked some space from some drive and created new volume. 
But when I restarted my PC it couldnt boot. Message was grub rescue. 
So I created super Grub disk. Now my PC can boot with that CD. But I can use 
only Ubuntu. I cant boot in Win 7. So can anyone tell me how to restore 
my boot sequence so that without grub CD I can use both OS ?

---

### Post by Peptid on 2013-07-03
Does 
----Code-----
sudo apt-get update-grub
----Code-----

solves it?

---

### Post by tusharkoshti on 2013-07-03
@ Peptid :
Error is invlaid operation  update-grub

---

### Post by Dozy Van on 2013-07-03
I would just boot Ubuntu from the Live CD.  Once inside there:


sudo apt-get update || sudo apt-get purge grub || sudo apt-get install grub


_**EDIT: Try the above post first**_

---

### Post by Peptid on 2013-07-03
Right, I'm sorry, the correct code should be

sudo update-grub

---

### Post by tusharkoshti on 2013-07-03
@peptid and Dozy Van : 
I did what u guys told but in vain. problem remained same. 

O/p of the command sudo update-grub : 

   tushar@tushar-VPCEH3AEN:/$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found initrd image: /boot/initrd.img-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found initrd image: /boot/initrd.img-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

---

### Post by Dozy Van on 2013-07-03
> **tusharkoshti said:**
> @peptid and Dozy Van : 
I did what u guys told but in vain. problem remained same. 

O/p of the command sudo update-grub : 

   tushar@tushar-VPCEH3AEN:/$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found initrd image: /boot/initrd.img-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found initrd image: /boot/initrd.img-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

sorry are you saying that its working now or not? as the Update found everything it needed to find.


Or is it still not working and if so what is happening on boot?

---

### Post by tusharkoshti on 2013-07-03
@Dozy Van :

problem remained same. I cant boot without Grub CD. 
Without CD I get following error. 

Unknown filesystem 
GRUB Rescue >

---

### Post by Mark Phelps on 2013-07-03
What is it that you want to do first -- restore Ubuntu boot, or restore Win7 boot?

Running update-grub does nothing to restore the Win7  boot.

---

### Post by wsxadf on 2013-07-03
You need to first check where the boot loader is installed. Can you check using

```
sudo fdisk -l
```

where the /boot is located? If you found it, say if it is in 'sda1', try this command:

```
sudo grub-install /dev/sda1
```

Many recommands that it is safe to run this command through live CD. Hope it works.

After this step, you can hopfully boot without live cd. If the windows does not show up, you may manually add entry for windows.

---

### Post by tusharkoshti on 2013-07-03
@ Mark Phelps : 
My intention is I will be able to choose which OS should I start when I will boot my PC without Grub CD. 
It is happeneing with 1st restoring Win7 loader or Ubuntu loader .... no problem. 
I want both OS to be accessed.

---

### Post by tusharkoshti on 2013-07-03
@ wsxadf : 
Sorry I didnt get where is the boot loader. So I m giving u o\p of the 1st command. 

tushar@tushar-VPCEH3AEN:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66448f75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    23709695    11853824   27  Hidden NTFS WinRE
/dev/sda2   *    23709696    23914495      102400    7  HPFS/NTFS/exFAT
/dev/sda3        23914496   169598204    72841854+   7  HPFS/NTFS/exFAT
/dev/sda4       169614326   976771071   403578373    f  W95 Ext'd (LBA)
/dev/sda5       169614328   362371071    96378372    7  HPFS/NTFS/exFAT
/dev/sda6       362373120   592588799   115107840    7  HPFS/NTFS/exFAT
/dev/sda7       592590848   771971071    89690112    7  HPFS/NTFS/exFAT
/dev/sda8       771973120   874371071    51198976    7  HPFS/NTFS/exFAT
/dev/sda9       935813120   968423423    16305152   83  Linux
/dev/sda10      968425472   976771071     4172800   82  Linux swap / Solaris
/dev/sda11      874373120   935811071    30718976    7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

I just guessed and run following command  

sudo grub-install /dev/sda9

I got following o/p :

tushar@tushar-VPCEH3AEN:~$ sudo grub-install /dev/sda9
/usr/sbin/grub-bios-setup: warning: File system `ext2' doesn't support embedding.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.

---

### Post by tusharkoshti on 2013-07-03
@ wsxadf :

hey I got win7 boot loader is at /sda2 ( by executing command   sudo update-grub ...... u can see o/p of this command above..... I have posted in this thread ) 

tushar@tushar-VPCEH3AEN:~$ sudo grub-install /dev/sda2
/usr/sbin/grub-bios-setup: warning: File system `ntfs' doesn't support embedding.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.

---

### Post by wsxadf on 2013-07-03
Did you choose grub bootloader to be your priority boot loader? If you did copy and paste
```
sudo grub-install /dev/sda
```
within your working system. It will install grub to the mbr of the disk. If that did not work. Try
```

sudo apt-get remove --purge grub-pc grub-common grub (to remove the packages and config files)
sudo apt-get install grub-pc (it installs all needed files)
sudo grub-mkconfig (create new config files)
sudo update-grub (usually there is nothing to update but run it anyway)
sudo grub-install /dev/sda (to install the new version on the MBR)
```

---

### Post by tusharkoshti on 2013-07-04
@ wsxadf :

Dude ... Ur 1st command worked. I got my boot loader back. 
Thank u dude :)

---

