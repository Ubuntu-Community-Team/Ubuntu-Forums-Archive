---
title: "[SOLVED] 100% New to Linux: Trouble Partitioning A HDD"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by iron.duck on 2008-11-30
About two weeks ago I created a bootable disc with the latest version of Ubuntu on it. I booted from the disc and proceeded to installing Ubuntu onto my laptop. Everything was going well and I was partitioning my Hard Drive to fit Ubuntu onto a computer which already had Vista on it. In the middle of the partition I was stupid enough to let it run out of power. (It wasn't so much in the middle, just as the partitioning was getting started.) So then I booted again from the CD and tried again. This time I was successful but whenever I start my computer, I have two options of the same Ubuntu OS to start from. How do I get rid of one? 

Thanks for the help, so far Ubuntu is running way better than Vista. hahaha

---

### Post by Mud.Knee.Havoc on 2008-11-30
Are you sure that they're exactly the same?  Ubuntu usually comes up twice in grub... the first one is the one you'd normally pick, the other is a failsafe mode.

EDIT: I should keep answering your question, sorry. :)  Grub is the boot manager that comes up and lets you select one of many operating systems (which you described in your post).  If you do have two duplicate entries in grub, it's easy enough to edit your /boot/grub/menu.lst file and only display the one(s) you want.  The configuration file looks confusing at first, but right at the bottom should be the choices.  Just make sure to save your original menu.lst before editing it (save it as menu.lst.backup or something), just in case you have problems booting after modifying it.

Are you sure that you selected the whole drive to install Ubuntu on?  I'm worried that you might have partitioned it the first time, then by going through again, it may have created a new Ubuntu partition, leaving you with two Ubuntus. :)  Did you select the installation option to use the whole drive?  I have a feeling you didn't do this, and grub may just be confusing you a bit (hopefully!).

---

### Post by EdThaSlayer on 2008-11-30
I hope this helps: [http://ubuntuforums.org/showthread.php?t=997241&highlight=edit+grub](http://ubuntuforums.org/showthread.php?t=997241&highlight=edit+grub)


It is all about editing grub.

Otherwise just 

> gksu gedit /boot/grub/menu.lst 

or
[QUOTE="jacobmp92"]
Check out the the startupmanager package to do GRUB modifications for you. Accessible from System > Administration > Startup Manager.[/QUOTE]

---

### Post by Mud.Knee.Havoc on 2008-12-01
This is a response to your PM.  It's probably best to keep the discussion public, in case anybody else wants to help you out.

Basically, I was told that there were two separate installations of Ubuntu.

So you want to keep Vista on the machine as well as Ubuntu? 

This might take a bit of playing around in order to get it back to normal.  Basically, you could remove one of the Ubuntu partitions (EDIT: using gparted - warning! This is dangerous if you mess anything up - whether or not you play with partitions, please back up everything you need now!) and convert it to free space, then add it to your other Ubuntu partition.  It's hard to describe without seeing it right in front of me, though.  If you're brave, the easiest way may be to download a live partition editor CD ([http://partedmagic.com/](http://partedmagic.com/)), delete everything Ubuntu, and reboot with the Ubuntu disc and make sure you install it to the free space on the drive.

There are actually a few ways you could go about solving your problem.

---

### Post by iron.duck on 2008-12-02
I haven't abandoned you all. Thanks for the help, I think I'm going to remove everything Ubuntu and not mess up during the install this time.

---

### Post by russo.mic on 2008-12-02
Annoying thing i've run into, did you make Vista the LAST partition on the Harddrive?  For some unknown reason (As far as I know), vista and XP bootloader want to reside on the latter part of the disk.  Still don't quite understand why.

Russo.

---

### Post by iron.duck on 2008-12-03
GParted is now installed. So, whenever I start up, I have two options of Ubuntu to start up from. (Plus the recovery mode options). Then, in other operating systems, the only thing that's left of Vista is the recovery kit. 


I thought it would be helpful if I provided an image of a screen shot I took while I used GParted. So, how do I know which partition is for what? I'm completely lost. 

[http://s709.photobucket.com/albums/ww94/iron-duck/?action=view&current=Screenshot.png]("http://s709.photobucket.com/albums/ww94/iron-duck/?action=view&current=Screenshot.png")

Thanks for your patience with such a newbie... :)

---

### Post by Keen101 on 2008-12-03
not to freak you out, but vista probably got wiped by your second install.... ooops. Messing with partitions is slightly dangerous, and is why caution and backups are usually good. If you want to use gparted to wipe ubuntu or start from scratch you will need ubuntu unmounted. Use this if it's not what you are already using.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

EDIT:  never mind. I looked at the picture now. Vista is probably still there, since you have two ntfs partitions. GRUB is probably just not pointing to it. And it only looks to me like there is one ubuntu install, so you should be fine except for the GRUB configuration. **Are you sure the two are exactly the same? Ubuntu sometimes has multiple kernels to choose from.**

/dev/sda3 is probably vista, since it has a boot flag. EXT3 is your main ubuntu partition, and there is only one, so I'm thinking either your GRUB really got screwed up, or you have two kernels which is normal. swap is your Linux swap partition for saving temporary stuff.

Edit #2: well actually vista is probably gone now that i think about it again. You said you could boot the vista recovery, but not regular vista? Well, then vista is probably gone, since only one of your ntfs drives is bootable.

---

### Post by Michael.Godawski on 2008-12-03
[FONT=Verdana]Can yo[/FONT][FONT=Verdana]u please log in into Ubuntu, start the terminal and run this command:[/FONT]
```
cat /boot/grub/menu.lst
```

[FONT=Verdana]and post the output here[/FONT]?

---

### Post by iron.duck on 2008-12-03
Ubuntu 8.10, Kernel 2.6.27-9-generic
Ubuntu 8.10, Kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, Kernel 2.6.27-9-generic
Ubuntu 8.10, Kernel 2.6.27-9-generic (recovery mode)

other operating systems:

Windows Vista / Longhorn (Loader)

This is what I see when I boot up. (My options for OSes). The bottom is what I select for the vista recovery. I might have posted this message twice. I don't know....

---

### Post by iron.duck on 2008-12-03
Thanks for the support everyone, I think I'm figuring this out.

---

### Post by iron.duck on 2008-12-04
> **Keen101 said:**
> not to freak you out, but vista probably got wiped by your second install.... ooops. Messing with partitions is slightly dangerous, and is why caution and backups are usually good. If you want to use gparted to wipe ubuntu or start from scratch you will need ubuntu unmounted. Use this if it's not what you are already using.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

EDIT:  never mind. I looked at the picture now. Vista is probably still there, since you have two ntfs partitions. GRUB is probably just not pointing to it. And it only looks to me like there is one ubuntu install, so you should be fine except for the GRUB configuration. **Are you sure the two are exactly the same? Ubuntu sometimes has multiple kernels to choose from.**

/dev/sda3 is probably vista, since it has a boot flag. EXT3 is your main ubuntu partition, and there is only one, so I'm thinking either your GRUB really got screwed up, or you have two kernels which is normal. swap is your Linux swap partition for saving temporary stuff.

Edit #2: well actually vista is probably gone now that i think about it again. You said you could boot the vista recovery, but not regular vista? Well, then vista is probably gone, since only one of your ntfs drives is bootable.



(For anyone that hasn't yet, look at the screen shot I took while using GParted) 

So, I'm having a hard time wrapping my mind around what I see. What exactly is "sda"? I see an sda1 through sda6. Second, what does "ntfs" mean and what does "unallocated" mean? (Everyone starts stupid at one point, at least I'm willing to change that.)

OH! And I'm not quite sure what it means for something to be mounted. Thanks for your patience, I think I'll get my problem fixed after this. You don't understand how much easier you're making this transition.

---

### Post by handydan918 on 2008-12-04
> **iron.duck said:**
> (For anyone that hasn't yet, look at the screen shot I took while using GParted) 

So, I'm having a hard time wrapping my mind around what I see. What exactly is "sda"? I see an sda1 through sda6. "sda" denotes the first hard drive . Sometimes appears as "hda" depending on kernel version and hardware specifics, like IDE or SATA drives.> Second, what does "ntfs" mean NeanderThal File System....kidding! New Technology File System (Now pushing 2 decades "new"...) > and what does "unallocated" mean? Unallocated space is space on a drive that doesn't have data on it.> (Everyone starts stupid at one point, at least I'm willing to change that.)No. Everybody starts ignorant. Only we happy few are blessed enough to start truly stupid...> 

OH! And I'm not quite sure what it means for something to be mounted. Old Unix maxim say "everything is a file." So everything must be attached (mounted) to the file system at some particular "mount point".> Thanks for your patience, I think I'll get my problem fixed after this. You don't understand how much easier you're making this transition.

Yes, we do. Been there.

;)

---

### Post by iron.duck on 2008-12-05
> **Mud.Knee.Havoc said:**
> If you do have two duplicate entries in grub, it's easy enough to edit your /boot/grub/menu.lst file and only display the one(s) you want.  The configuration file looks confusing at first, but right at the bottom should be the choices.  Just make sure to save your original menu.lst before editing it (save it as menu.lst.backup or something), just in case you have problems booting after modifying it.

I think you're right and I found the Menu, but I don't have permission to edit it. How do I have permission? I was just reading a Linux magazine, and learning about su, sudo, and root... but I obviously don't know enough. Please explain how I would give myself permission. (then take away) However much your willing to explain. Maybe you can point me in another direction to learn more. :D

---

### Post by caljohnsmith on 2008-12-05
> **iron.duck said:**
> I think you're right and I found the Menu, but I don't have permission to edit it. How do I have permission? I was just reading a Linux magazine, and learning about su, sudo, and root... but I obviously don't know enough. Please explain how I would give myself permission. (then take away) However much your willing to explain. Maybe you can point me in another direction to learn more. :D
You could open a terminal (Applications > Accessories > Terminal) and do:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst &
```
The first command makes a backup of your menu.lst, and the second command opens your menu.lst as root user so you can edit it as you wish. If you want help editing your menu.lst, then please post the full contents first and let us know what you want to do with it. :)

---

### Post by iron.duck on 2008-12-08
> **caljohnsmith said:**
> You could open a terminal (Applications > Accessories > Terminal) and do:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst &
```
The first command makes a backup of your menu.lst, and the second command opens your menu.lst as root user so you can edit it as you wish. If you want help editing your menu.lst, then please post the full contents first and let us know what you want to do with it. :)

I can't tell where the commands end. Could you space em out a bit more? thanks.

---

### Post by caljohnsmith on 2008-12-08
> **iron.duck said:**
> I can't tell where the commands end. Could you space em out a bit more? thanks.
Each of those lines is a separate command, so if you copy and paste each line into the terminal, press enter after pasting each one and you should be fine. Let me know if you run into problems though.

---

### Post by iron.duck on 2008-12-12
I love you all, thanks for the help. Problem solved!

---

### Post by caljohnsmith on 2008-12-13
Glad to hear that worked; cheers and have fun with Ubuntu. :)

---

