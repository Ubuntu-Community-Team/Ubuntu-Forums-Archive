---
title: "Has anyone used Acronis True Image to *restore* a dual boot system?"
date: 2016-06-11
forum: New to Ubuntu
---

### Post by jake-swensen on 2016-06-11
I installed Windows 10 then Ubuntu 16.04 LTS desktop with dual boot.  To save hours of time in creating users, installing applications, and configuring settings, I would like to take a system backup with both operating systems.  When, not if, I render the system completely inoperable as a result of my experiments with software modules and networking, I want to quickly reset the system state to begin anew.

IMO, since Clonezilla is not *yet* mature for mainstream use and tested as much as some other solutions, I want to use the Acronis True Image 2016 that I have already purchased.  Has anyone had success with backing up *and restoring (and verifying)* a dual boot system image with True Image?

---

### Post by tea for one on 2016-06-11
Good evening

Acronis is a Windows software image system - is that correct?

Can you create an image of Ubuntu with Acronis?

I would consider myself to be very unlucky if I managed to make two operating systems inoperable in one foul swoop?

As you have already purchased Acronis, I would be interested if you could experiment and test if you can image and seamlessly restore both systems?

I only use Linux based systems so I have experimented with Clonezilla (which is mature enough for my use), fsarchiver, systemback and redo backup.

They all create an OS image which can be restored.

I prefer systemback although Clonezilla is often a preferred choice among other forum users.

I doubt if Ubuntu users will purchase Acronis since there are reasonable free software alternatives for Linux users.

Let us know the results of your experiment with Acronis, I would be very interested to read about the outcome.

Best wishes

---

### Post by JayKay3OOO on 2016-06-11
I use the free version of reflect that will image your hard drive from windows while it's turned on. I've restored windows straight back to my hard drive and moved windows to a VM using this tool. I think it grabs the linux partitions too although it has no idea what is in them.

There are linux tools for making images. I think the gnome-disk utility can make images, but not while the system is on, but you may be able to run it from a live image. I do all my testing in a VM and have my VM SSD clean with the work on the backup nas. Since you can snapshot the vm there is no issue if you make a mistake or break the VM and with windows keep the system restore turned on. I've used it reliably in the past.

You can't break linux. You can only be in a situation where it's temporarily unavailable. What is it? ctrl + alt + F1, etc to switch to a console if you break the display manager. sudo is your friend and think twice before running any command with the word 'purge' in it. Windows, well that's fairly indestructible. It's even learnt what idiots some of its users are and won't let you delete certain things with a lot of hard work. Most likely issue you mess up the boot loader so you can't get to one or the other OS, but update grub and there was a tool for windows. regedit, but it allows you to backup before you mess up.

---

### Post by jake-swensen on 2016-06-11
Thanks guys (gender neutral in US).  Acronis upgrade was being offered at a steep discount so I bought it but I wouldn't mind a free alternative.  I will admit that as a novice Linux user, some kind of GUI and easy to understand documentation for system backup does help.

Setting up a virtual machine is next on my list of topics to read about, after learning how to design and secure my basic home network.

As you said, it seems that Systemback and Macrium Reflect will likely be effective at backing up the dual boot system so I will probably try to use them in the future.  In the meantime for the experiment:

1. I backed up the dual boot disk to an external hard drive by using True Image 2016 boot DVD.  The disk included a master boot record, Windows system partition (0.5 GB), Windows main partition (149.5 GB), Ubuntu swap partition (4 GB), Ubuntu main partition (146 GB)

2. Deleted all partitions with Windows 10 boot/installation DVD -- didn't bother to format any

3. Confirmed that even GrUB wouldn't load -- it just showed a command prompt

4. Restored the entire disk with the True Image boot DVD and external hard drive

5. Verified that Ubuntu 16.04 and Windows 10 can be launched from GrUB and they work as expected in terms of internet browsing, ssh to external server, etc.  I did not do a bit level verification.

This backup software, probably like the other backup programs, is also able to restore only one of the partitions in case I damage only one of the operating systems.

---

### Post by howefield on 2016-06-12
Acronis will do as you want, it supports some Linux file formats including ext* but only as far as backing up/recovery. I believe you can browse the Windows based images and restore individual files/folders, that wouldn't be possible with the Linux image.

Clonezilla is certainly mature enough to image partitions or disks, verify the integrity of the image and restore plus a load more, it can't restore individual files/folders, perhaps it's more text based look and feel scares you ?

Nothing wrong with backing up the full drive including both operating systems, but I'd advise also taking an image of each operating system partition, then you can reimage only what you need. Back when I had dual boot systems, I would install Windows and image the disk, then install Ubuntu and image both the disk and the Ubuntu partition. And of course have a plan for files added/created since previous image.

---

### Post by Mark Phelps on 2016-06-12
I have used Macrium Reflect, myself, and it DOES support backup/restore of Linux filesystems -- and it is FREE.

---

### Post by JayKay3OOO on 2016-06-13
> **Mark Phelps said:**
> I have used Macrium Reflect, myself, and it DOES support backup/restore of Linux filesystems -- and it is FREE.

Thanks for that, I thought it did, but did not want to make false claims to the OP.

---

