---
title: "[SOLVED] Ubuntu dual boot"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by polymath on 2008-07-17
Ok, i had windows XP installed, but I used the Ubuntu live 8.04 CD to completely reformat the Disc, so that I would no longer have XP.  Then, since I wanted to dual boot with Puppy Linux 4, I popped that live cd in and ran it from RAM, opened up GParted, created a new partition, so now I have:

   /dev/hda1: ext3 Ubuntu
   /dev/hda2: Extended with internal Linux Swap Area
   /dev/hda3: ext2 Blank

I then shut down puppy and saved my session and all of the files to hard disk at partition /dev/hda3.  Everything worked.  Shut the computer down, but then when I booted from hard disc with GRUB it did not give me a dual boot option but went straight to Ubuntu.  Can someone explain why this is and help me correct it so i can dual boot?

---

### Post by wolfen69 on 2008-07-17
it appears that you did not actually install puppy. you will need to do this in order for ubuntu's grub to recognize it.

---

### Post by polymath on 2008-07-17
Then what do I need to do?  I followed the instructions on shutdown to save puppy files to hard disk partition?  Sorry for being stupid, but I am new to linux (just started yesterday).

Thanks for the quick response.

---

### Post by snowpine on 2008-07-17
Hi Polymath, I am not a Puppy expert (so take my advice with a grain of salt) but I think what you did is to "dock" Puppy rather than install it. If you boot up with the Puppy Live CD again, can you see the files you saved last time? Live CD distros (like Puppy) have this clever feature to let you save your session without actually installing a bootable OS to the hard drive.

If you look around a bit, you should find an option for a full installation so that you can boot Puppy from the hard drive without using the Live CD. Wish I could help you but I am not a Puppy man. :)

---

### Post by polymath on 2008-07-17
Thanks for all of your help.

I wiped my ext2 partition and opened up puppy and reinstalled there.  I then went into puppy and found the "Puppy Universal Installer" and chose full installation.  I then chose to update an existing GRUB (my GRUB from Ubuntu).  It gave me three lines of code to insert into GRUB's menu.lst file.  I temporarily mounted my ext3 Ubuntu hard disk and went into /boot/grub and found menu.lst, and inserted the lines of code as it told me too right after the lines that displayed the different kinds of Ubuntu (recovery mode, generic, etc.).  After editing GRUB I unmounted the Ubuntu drive, shutdown without saving my session, and rebooted the computer (after taking out my puppy CD.  Expecting to see the same screen as my XP/Ubuntu dual boot on my other computer (choose an OS to run:  ubuntu... ubuntu... ubuntu... winNT...winXP), my setup seemed to bypass that screen and proceed to ubuntu-generic automatically.  So my new question:

How do I set ubuntu and grub to display the menu??  I found these lines of code in menu.lst and I am wondering if all I need to do is remove hiddenmenu.  I'm not sure and don't want to make a change before I am sure:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

If you need to see the rest of menu.lst I can supply.  Please help me finish!  I know I am almost there!

EDIT:  I tried to comment out hiddenmenu and ubuntu got smart on me and wouldn't let me.  I don't want to have to go back into puppy with the boot disc because I am worried it will overwrite my install, or it won't let me in.

---

### Post by polymath on 2008-07-17
I finished.  All I had to do was reboot puppy, mount my hard disk, comment out menu.lst, change the timeout to 10 seconds (3 seconds is pretty hard to react), and reboot my computer!  This post was posted in SeaMonkey (Puppy's web brouser).

---

