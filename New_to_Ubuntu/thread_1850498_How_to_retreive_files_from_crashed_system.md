---
title: "How to retreive files from crashed system???"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by suomalainen on 2011-09-26
Ubunteros,

It looks as if my system may have suffered from a non recoverable crash.

I would like to know the following.

1. How can I get my firefox bookmarks

2. How can I get all me Evolution email and contacts?

Thank you very much!

Suomalainen

---

### Post by Lisiano on 2011-09-26
All your Firefox information is stored inside /home/$USER/.mozilla and all Evolution information is stored inside /home/$USER/.config/evolution

You could just re-install Ubuntu and it should detect that you have a home folder and will keep all files intact in there. Or so I heard.

EDIT: You can use a LiveCD/LiveUSB to recover the files.

---

### Post by suomalainen on 2011-09-26
I have a live CD. It's the one that let's you try out Ubuntu before installing it right?

If so how do I use it so that it recovers my files?

Thanks again!

---

### Post by garvinrick4 on 2011-09-26
Put Cd in Tray and boot it (set in Bios to boot cd first) use Try Ubuntu and when
the desktop appears open a Nautilus Window (Home or documents any window)
and on left side or window will be your install click on it to open and go to /home
folder and copy your personals to back up drive. Follow path to anything you
want copys of and copy to backup drive basically.

---

### Post by suomalainen on 2011-09-26
@ garvinrick4

Because my Ubuntu o/s is on an external HDD, that drive appears on the desktop of the bootable Ubuntu USB stick I'm currently using.

I just double clicked on the drive and found the home folder with my user name and then copied the .mozilla and .evolution folder to an external drive.

WAS THIS PROCESS INCORRECT? I ask this cause you want me logged in as root but in the case I just outlined I didn't need to be?

Clarification appreciated.

Thanks

---

### Post by garvinrick4 on 2011-09-26
Yes, as long as a drive is mounted and you can access the file system you are in good
shape.
By the way I would always make backups of bookmarks in firefox in Bookmarks drop down
to show all bookmarks and there you can backup, makes a .json file that you can install
in any Firefox browser with same.

---

### Post by suomalainen on 2011-09-26
@ garvinrick4 Thanks again!

Will I suffer any data loss/problems by copying over the saved folders like .mozilla or .evolution to the new install? For me the big deal is the email.

Also, would you happen to know what I need to pay attention to when doing the re-install. I ask this because my o/s is on a external hard drive that has been partitioned and I don't know how grub is set up etc...

Thanks

---

### Post by suomalainen on 2011-09-26
I ran <sudo blkid> and here is what I got. Not sure where grup is suppose to go?


WITH EXTERNAL DRIVE CONNECTED

paavo@paavo-laptop:~$ sudo blkid
[sudo] password for paavo: 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0B16" TYPE="vfat" 
/dev/sda2: UUID="0EA8C6E9A8C6CF01" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" TYPE="vfat" 
/dev/sdb1: UUID="22b752f7-525e-4ee6-b3ef-fc8978607ae5" TYPE="ext4" 
/dev/sdb5: UUID="f4590d33-c961-49f4-aeab-405f5358703f" TYPE="swap" 
/dev/sdd1: LABEL="Jasper" UUID="64F0E18EF0E166B0" TYPE="ntfs" 
/dev/sdd2: LABEL="Ununtu 10.04 LTS" UUID="51a8859b-9c27-4e9d-b7cf-f17178aefc95" TYPE="ext3" 
/dev/sdd3: UUID="1fb0bff6-e5fa-405c-ba42-f5a8003c90d5" TYPE="swap" 

WITH DRIVE DISCONNECTED

paavo@paavo-laptop:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0B16" TYPE="vfat" 
/dev/sda2: UUID="0EA8C6E9A8C6CF01" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" TYPE="vfat" 
/dev/sdb1: UUID="22b752f7-525e-4ee6-b3ef-fc8978607ae5" TYPE="ext4" 
/dev/sdb5: UUID="f4590d33-c961-49f4-aeab-405f5358703f" TYPE="swap" 
paavo@paavo-laptop:~$

---

### Post by garvinrick4 on 2011-09-26
If you want your boot info to be diagnosed have to run this script and post to your thread
is long so after pasting to your message box highlight whole thing and hit the # sign in upper right of message box and will put in nice box to read from.
Download this scipt to Desktop and then run the code I give you and will put the results
in RESULTS file on your desktop.
Open with archive manager and extract.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
Now open a terminal and:
  	 	 	 	 	```
sudo bash ~/Desktop/boot_info_script.sh
```

---

