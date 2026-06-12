---
title: "Help Please! Kernel Panic and Invalid Op Code"
date: 2016-03-08
forum: New to Ubuntu
---

### Post by bonzo2 on 2016-03-08
Hello,

I'm panicked as black screen packed with text just popped up on my PC. I couldn't get a screen grab, but did see these phrases: 
[INDENT]
[B]Invalid op code: 0000 [#2] [11427.908676] --- end trace 61a458bb863d7f0f ]---
Kernel panic - not syncing: attempted to kill the idle task[/B]!
[/INDENT]

I believe the only programs running at the time of the error were:[INDENT]
Firefox 44.0.2
Thunderbird 38.5.1
Clementine (I couldn't figure out version number)
[/INDENT]

Can  anyone tell me how much trouble I'm in with this? I moved from Windows  to Ubuntu 14.04 (and from Outlook to Thunderbird) about a year ago. I  had never used a Linux program prior to that and still consider myself a  total novice. I'm panicked because my entire life is saved on the  laptop and I'm not sure which Ubuntu and Thunderbird files to copy if I  need to do so.

Thank you

---

### Post by grahammechanical on 2016-03-08
You have identified three likely suspects. Now, you have to try to reproduce the problem under controlled conditions. For example, Don't use Clementine. Use the original User Interface - Unity.

You could also install another web browser and use that while waiting to see if Unity triggers the kernel panic. If it does not then open Firefox or Thunderbird. Use a process of elimination.

Do you remove your emails from the ISP's server when you open them in Thunderbird? Do you have /home on a separate partition? You could create another partition and start transferring your data over to it. 

If you suspect the kernel itself, then use Grub menu Advanced options for Ubuntu to load into an earlier kernel and run with that for a while.

Regards.

---

### Post by bonzo2 on 2016-03-08
Hi grahammechanical: ):P

Thanks for your reply. I'm not quite proficient enough yet to execute your suggestions without a little assistance. If you could provide a little guidance, that'd be greatly appreciated. Please see my replies/questions below in red. 	 	 		>  			 				
"You have identified three likely suspects. Now, you have to try to  reproduce the problem under controlled conditions. For example, Don't  use Clementine. Use the original User Interface - Unity."

Is Unity the default interface in Ubuntu 14.04 LTS? How would I know if I have something different?
>  
You could also install another web browser and use that while waiting to  see if Unity triggers the kernel panic. If it does not then open  Firefox or Thunderbird. Use a process of elimination.
Thanks. I just installed Chromium. 
>  
Do you remove your emails from the ISP's server when you open them in  Thunderbird? 
I have some on the server and some have been downloaded to the local files on Thunderbird. 


Do you have /home on a separate partition? You could create  another partition and start transferring your data over to it. Are you asking whether I have separate partitions for my data and program files?  If so, I believe I do not have a separate data partition.  In addition to my personal date contained in /home, it also contains program files (such Gnome, Mozilla, KDE, etc). The results of the commands "lsblk" and "sudo fdisk -l" are listed below.

Do they indicate whether I have an available partition to which I can move my data??
```

abc@123:~$ lsblk
NAME                           MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                              8:0    0 931.5G  0 disk  
&#9500;&#9472;sda1                           8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                           8:2    0     1K  0 part  
&#9492;&#9472;sda5                           8:5    0 931.3G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)          252:0    0 931.3G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root (dm-1)   252:1    0 915.4G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1 (dm-2) 252:2    0  15.9G  0 lvm   
sr0                             11:0    1  1024M  0 rom   

abc@123:~$ sudo fdisk -l
[sudo] password for abc: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0000cd00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   83  Linux

Disk /dev/mapper/sda5_crypt: 999.9 GB, 999945142272 bytes
255 heads, 63 sectors/track, 121569 cylinders, total 1953017856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 982.9 GB, 982851256320 bytes
255 heads, 63 sectors/track, 119491 cylinders, total 1919631360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 17.0 GB, 17045651456 bytes
255 heads, 63 sectors/track, 2072 cylinders, total 33292288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table


```
> 
If you suspect the kernel itself, then use Grub menu Advanced options  for Ubuntu to load into an earlier kernel and run with that for a while.

I don't know enough about kernels to know when I should be suspicious of one! ;)  I'm up-to-date on my Ubuntu system files and have never experienced this panic error before, so perhaps the kernel is a suspect. 

Thanks for your time and any feedback you might have.


Bonzo

---

