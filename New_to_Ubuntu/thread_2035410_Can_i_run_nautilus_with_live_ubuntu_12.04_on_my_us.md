---
title: "Can i run nautilus with live ubuntu 12.04 on my usb ?"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by bluecristals on 2012-07-30
if yes then how i do it.
 
after a bsod i want to recover some files on my hard and i don't know how,
in ubuntu 10.04 i see it's possiblee. in ubuntu 12.04 i can't find places buton i did not find any youtube tutorial.
 
best regards

---

### Post by Sandertje on 2012-07-30
second button on the left menu is "home folder". This opens nautilus.

Alternatively, you can open a terminal and just type ```
nautilus
```

---

### Post by mlentink on 2012-07-30
Yes.

Click on the ubuntu icon on the launcher-bar on the left. Start typing 'nautilus'. You will see the icon for the nautilus launcher appear.

Good luck

---

### Post by NikTh on 2012-07-30
Hi , 
if you want to transfer files to an external drive then i think is better to run 
```
gksudo nautilus
``` 
from a terminal (Ctrl+Alt+t). 

When window open , find your files and transfer them where you want .
Be aware that hidden files revealing by pressing Ctrl+H . 

Thanks

---

### Post by audiomick on 2012-07-30
+1 the last post. I have found in the past that I have needed an instance of Nautilus with root privileges to get at files belonging to another user than the one I am currently. Bear in mind that the files may belong to root after copying, and may need to have their permissions changed to be able to be accessed by a non-root user.

---

### Post by bluecristals on 2012-07-30
Thanks, i've manage to open nautilus and after click on f3 i had 2 windows.
in the left upper corner i can see my 2 XP-sp3 partitions 20 and 60 gb.
after i click on the first one all my folders are shown in the left window of nautilus.
i drag and drop one of the xp folder in the right nautilus window and it show that the folder is being copy to the ubuntu. 
when finished an icon of my xp folder it's shown in the right window of nautilus.
so all seems to be ok.
 
STILL AFTER I SHUT DOWN AND LOOK INTO THE UBUNTU USB FOR MY XP FOLDER IS NOTHING THERE.
WHAT CAN I DO. I HAVE ONLY ONE USB UNIT AND DVD IS WORKING NO MORE AFTER THE BSOD.

---

### Post by bluecristals on 2012-07-30
Hi,
after a bsod i want to recover some files on my hard and i don't know how,
in ubuntu 10.04 i see it's possiblee. in ubuntu 12.04 i did not find any youtube tutorial.
i've manage to open nautilus and after click on f3 i had 2 windows.
in the left upper corner i can see my 2 XP-sp3 partitions 20 and 60 gb.
after i click on the first one all my folders are shown in the left window of nautilus.
i drag and drop one of the xp folder in the right nautilus window and it show that the folder is being copy to the ubuntu. 
when finished an icon of my xp folder it's shown in the right window of nautilus.
so all seems to be ok.

STILL AFTER I SHUT DOWN AND LOOK INTO THE UBUNTU USB FOR MY XP FOLDER IS NOTHING THERE.
WHAT CAN I DO. I HAVE ONLY ONE USB UNIT AND DVD IS WORKING NO MORE AFTER THE BSOD.
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]BEST REGARDS
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by NikTh on 2012-07-30
> **bluecristals said:**
> 
STILL AFTER I SHUT DOWN AND LOOK INTO THE UBUNTU USB FOR MY XP FOLDER IS NOTHING THERE.
WHAT CAN I DO. I HAVE ONLY ONE USB UNIT AND DVD IS WORKING NO MORE AFTER THE BSOD.

Hi , 
I think this is not going to happen . Things not working that way.
You cannot store files or folders to an Ubuntu Live usb. Ubuntu Live helps you to find your files and move them (or copy them) to an external usb or drive . To another Usb or external drive , not the same Usb. 

To do that you should created a usb with persistent (space) but even that has a limit (4GB) i think.

So what you must do is to boot from Live Usb and plug in **another **usb or external Drive and drag n drop your files and folders there.

Thanks

---

### Post by bluecristals on 2012-07-30
> **NikTh said:**
> Hi , 
I think this is not going to happen . Things not working that way.
You cannot store files or folders to an Ubuntu Live usb. Ubuntu Live helps you to find your files and move them (or copy them) to an external usb or drive . To another Usb or external drive , not the same Usb. 
 
To do that you should created a usb with persistent (space) but even that has a limit (4GB) i think.
 
So what you must do is to boot from Live Usb and plug in **another **usb or external Drive and drag n drop your files and folders there.
 
Thanks
 
Hi NikTH,
 
You seem to be a life saver.
I have two 16 gb usb. I thought myself at what you have said still i was'nt sure it's working becouse i have only 512 mb RAM and ubuntu has 700 mb.I quess is not  all of that 700 mb loaded into RAM in the same time still didn't want to take the chance. 
DO YOU THINK THAT WILL WORK ?
 
If not do you think is no way to make another folder into the usb live ubuntu in which i can put my files ?

---

### Post by anewguy on 2012-07-30
If you are running ubuntu off a usb flash drive or something similar, when you created that usb media you had two things that needed to be addressed - you can probably re-create the usb media (via unetbootin or perhaps startup disk creator) with the following in mind:

- the usb media should be at least 8gb - preferably more

- when installing ubuntu to the usb media, you must enable persistence and set up a size for the persistence data.  Without that, anything you do while booted on the usb media will disapear as soon as you reboot.

---

### Post by bluecristals on 2012-07-30
> **anewguy said:**
> If you are running ubuntu off a usb flash drive or something similar, when you created that usb media you had two things that needed to be addressed - you can probably re-create the usb media (via unetbootin or perhaps startup disk creator) with the following in mind:
 
- the usb media should be at least 8gb - preferably more
 
- when installing ubuntu to the usb media, you must enable persistence and set up a size for the persistence data. Without that, anything you do while booted on the usb media will disapear as soon as you reboot.
 
 
Thanks anewguy,
 
I have the ubuntu live into 16 gb usb.
Do i can enable persistence in ubuntu display (if yes than how) or i must re-create ubuntu live usb with persistence enabled and how i do this ?
God for me is happend that you are  on earth right now.

---

### Post by oldfred on 2012-07-30
I have never done a persistent install. With a 16GB flash you can do a full install and still have room for data. I have a full install in a 8GB partition on my 16GB flash and 8GB for data.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I did copy this from another post on how to convert an install to persistent.

> This is how I made a Unetbootin install to 4 GB flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw", (optional)
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.
Backtrack with persistence and grub legacy
[http://www.backtrack-linux.org/wiki/index.php/Persistent_USB](http://www.backtrack-linux.org/wiki/index.php/Persistent_USB)


---

### Post by bluecristals on 2012-07-31
Thanks MASTER,
 
Seems like a piece of cake. I'l try it in spite that for sure I will bother you with questions about some steps you have posted.
On the other hand I have one spliter with 3 heads for my only usb unit. Can I put my live ubuntu usb into one head and another usb into another in which to put my files and by-pass all that long procedure you have shown to me ?

---

### Post by mlentink on 2012-07-31
It seems you have more than one USB port available to you, so there is a far easier method to backup your data. 
- plug your Ubuntu Live-usb stick in port1
- plug another USB-drive with enough free space in port 2
- boot up with the Ubuntu live-usb
- copy the necessary files with nautilus to the usb- drive with the free space, NOT to the Ubuntu Live-usb (which is not persistent)
Done.

---

### Post by audiomick on 2012-07-31
The advice that NikTh gave you is correct. Have you tried that?

I don't think the amount of RAM is an any way relevant.

As NikTh pointed out, it is possible to make a Live USB with persistance, i.e. with an amount of file storage space where you can put stuff that you want to have when you boot from that stick. I don't know that the space is limited, but NikTh may well be right about that too.

If your USB installer doesn't have persistance, I think the easiest way for you is to use one of the other USB sticks that you say you have and store the files you want to retrieve off to that.

---

### Post by Elfy on 2012-07-31
Please do not post duplicates, it dilutes community effort. Threads merged

---

### Post by bluecristals on 2012-08-01
Thanks for all your god advices,
I've done it with the usb spliter. I had the transfer speed  smaller but in the end my files are saved now.
And also thanks to UBUNTU.

---

