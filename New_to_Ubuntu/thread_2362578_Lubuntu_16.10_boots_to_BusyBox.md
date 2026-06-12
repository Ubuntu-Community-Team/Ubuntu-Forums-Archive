---
title: "Lubuntu 16.10 boots to BusyBox"
date: 2017-05-30
forum: New to Ubuntu
---

### Post by thestormborn21 on 2017-05-30
Hi,

New to Linux and Ubuntu. Was attempting to load Lubuntu 16.10 onto my old 2008 eMachine-250 Netbook. It has an Intel Atom processor, 1GB of RAM, and 250GB HDD.

I had issues with the ISO file. First it had a problem with the encryption and swapping partitions. I did the sudo swapoff --all fix, which corrected the issue.

Then the installer said it could not load due an error. I am writing this from memory, but it was a pretty generic error message. Did some searching on here and found the sudo apt-get lvm2 fix, which corrected the issue. 

Now it correctly installed, and I am booting to busybox. I tried searching on here and can only find fixes pertaining to other ubuntu distros that don't seem to exactly match my kernel files exactly. From what I can deduce, Lubuntu is having a hard time finding where it installed the OS. 

I hardboot and hold shift, to get the Lubuntu boot menu. I did all the ls commands and have found the partitions. However, no partition has any sort of indication of what files are stored. Example; 

ls (hd0,1)
(Paraphrasing) File system found, 512mb used, 247000000 free (roughly)

I also forget exactly how, but I found a thread where a user was having similar issues and was told to reboot with boot disk in. Try Lubuntu. Get to command terminal and do a sudo su command in order to view the files on the partitions. This also did not indicate any Lubuntu files. There was an sdb1 with Lubuntu on it, however when I tried to do the mount /dev/sdb1/mnt command it told me that it could not locate sdb1. Since I do not have two hard drives, I assumed that this was my USB stick. I then tried to mount the sda1, and sda5 partition for shits and giggles, and got the same error message. So my humble interpretation of this, is that Lubuntu is having a hard time recognizing any of my partitions.

There is an msdos1 partition and msdos5 partition that no matter how hard I try, I am unable to remove. I am a nub, so I did not format the machine prior to install. The reason being that Microsoft would not let me. It told me that formatting the partitions without an OS would cause system failure, and that because of this it could not let me format the partitions. I could not find much on Google about how to bypass this on Windows 7 Starter, so I chose to do a full cleanse upon installation of Lubuntu, including free disk space, encrypting all.

I tried editing the kernel myself with the "nomodeset" fix after quiet splash, which gets it to start to boot, but eventually says it's missing echo, and other files I cannot recall. However, those files are present in the kernel, and on the boot drive.

Can anyone help me? When I am home I can provide specific line answers, however I am not at my netbook at the moment and was hoping this was a good enough start for someone to point me in the right direction.

Looking forward to the help! Thanks to all for the wonderful support that the community provides. It got me this far, which for a complete Linux beginner, it made me feel quite accomplished even though I was not successful in my endeavors.

---

### Post by RobGoss on 2017-05-30
Hello and welcome to the forums, Seeing you're new to Ubuntu / Linux, I would suggest trying to install a lightweight distribution like** [Lubuntu]("http://lubuntu.net/")** it requires less resources to run, I notice you have only 1-GB of Ram on that machine. **16.10 **will be coming to it's end of life next month meaning it will no longer be supported

If I were you I would stick with the LTS releases they have the longest support and are the best choice for those that really want to enjoy what Ubuntu has to offer

---

### Post by poltiser2 on 2017-05-31
I can install and run on Acer AspireOnePro: Ubuntu Gnome (slow), Fedora Gnome (slow), Manjaro Gnome (slow), Kali (medium) 
Antix (clasic and MX - very good), Calculate (good) and, my favorite, simplify Xfce-ubuntu (as fast as lubintu)...

Good luck.

---

### Post by thestormborn21 on 2017-05-31
Rob,

I'm not sure how I misunderstood that 16.10 was not the newest version. 16.04 LTS installed fine. 

 /feelsbadman

Thanks for the help!

---

### Post by yancek on 2017-05-31
> I had issues with the ISO file.

It is always a good idea to verify the iso download with an md5 checksum.

> Then the installer said it could not load due an error

Always a good idea to make a note of any errors because there are many 'generic' errors and posting them will help members to help you.  

If you are at the grub prompt (grub>), try either/both of these commands:  ls /   OR ls /boot
They should show the directories in the root of the filesystem or if you have a separated boot partition, the boot files and Grub directory.
The command you posted:  ls (hd0,1) won't give you that information.

If you can boot the install media (DVD/flash drive) do that and open a terminal and run the command:  sudo fdisk -l(Lower Case Letter L in the command) and post that output here.
That should show the drives (including the usb) and partitions on both the harddrive and usb drive and you should be able to tell which is sda and which is sdb by the size shown in the output.

> 
There is an msdos1 partition and msdos5 partition that no matter how hard I try, I am unable to remove. 

The "msdos1" does not mean it is a windows partition so you don't need to delete anything.  It is probably your boot partition.

---

### Post by Rocky_Bennett on 2017-05-31
> **thestormborn21 said:**
> Rob,

I'm not sure how I misunderstood that 16.10 was not the newest version. 16.04 LTS installed fine. 

 /feelsbadman

Thanks for the help!



Ubuntu 17.04 is the newest version but 16.04 is LTS, which provides a more stable environment for a longer period of time.

---

### Post by RobGoss on 2017-05-31
> **thestormborn21 said:**
> Rob,

I'm not sure how I misunderstood that 16.10 was not the newest version. 16.04 LTS installed fine. 

 /feelsbadman

Thanks for the help!

That's quite alright, I just wanted you to be aware of it because I know we spend hours configuring our systems only to have to do it all over again in a few months

---

