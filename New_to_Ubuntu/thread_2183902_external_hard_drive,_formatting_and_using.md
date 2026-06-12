---
title: "external hard drive, formatting and using"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by ilovethislinuxstuff on 2013-10-26
Hi-
I am not very knowledgeable with computer systems and computers. I have Ubuntu 12.04 and just bought a seagate 500 gb external hard drive to back up some of my photos and files before I download the newest Ubuntu OS. What are the steps I take to use the external hard drive? Do I just plug it in? It says it is for Windows and doesn't say anything about Linux. Again I know very little about any of this and am below absolute beginner, lol.

---

### Post by ant2 on 2013-10-26
Have you tried just plugging it in? Chances are it will work.

---

### Post by ilovethislinuxstuff on 2013-10-26
> **ant2 said:**
> Have you tried just plugging it in? Chances are it will work.

Ok, if I plug it in, what do I do next?

---

### Post by ant2 on 2013-10-26
> **ilovethislinuxstuff said:**
> Ok, if I plug it in, what do I do next?

 You should probably see it appear in your file manager or a dialogue will appear asking you what you want to do next.

What version of Ubuntu do you currently have installed?

---

### Post by Bashing-om on 2013-10-26
ilovethislinuxstuff; Hi !

If you have any familiarity with the terminal, this is an easy method to do up your hard drive:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
Any uncertainty, by all means post back and we will clear it from your mind.

[INDENT][INDENT]workie great last long time
[/INDENT][/INDENT]

---

### Post by ant2 on 2013-10-26
This is an external USB drive?

---

### Post by ilovethislinuxstuff on 2013-10-26
> **ant2 said:**
> You should probably see it appear in your file manager or a dialogue will appear asking you what you want to do next.

What version of Ubuntu do you currently have installed?

I don't see a file manager anywhere and nothing is asking me what to do next.

---

### Post by ilovethislinuxstuff on 2013-10-26
> **ant2 said:**
> This is an external USB drive?

Yes, this is an external hard drive seagate that I bought with a usb plug in.

---

### Post by ilovethislinuxstuff on 2013-10-26
> **Bashing-om said:**
> ilovethislinuxstuff; Hi !

If you have any familiarity with the terminal, this is an easy method to do up your hard drive:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
Any uncertainty, by all means post back and we will clear it from your mind.
[INDENT][INDENT]workie great last long time
[/INDENT]
[/INDENT]


This seems kinda way over my head...I just want to back up some photos and documents in case I lose them when I update to the newest Ubuntu. I have this external Seagate Hard drive to put those files on and just need to know how to do that. Thanks for the help.

---

### Post by ant2 on 2013-10-26
If you can, open a terminal (Ctrl+Alt D) and type:

```
lsusb
```

Hopefully this will list your external USB so we can see if its detected.

**EDIT:** If your Using a recent Ubuntu release check the USB disk doesn't simply just appear in the launcher on the left of the screen when it is plugged in.

Do you happen to know if the drive is a NTFS format?

---

### Post by ilovethislinuxstuff on 2013-10-26
> **ant2 said:**
> If you can, open a terminal and type:

```
lsusb
```

Hopefully this will list your external USB so we can see if its detected.

I have it plugged in right now into the usb port and the light on the external hard drive is blue and lit up.

But here's what the terminal says:



No command 'lsub' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
 Command 'qsub' from package 'slurm-llnl-torque' (universe)
 Command 'qsub' from package 'gridengine-client' (universe)
 Command 'qsub' from package 'torque-client-x11' (universe)
 Command 'qsub' from package 'torque-client' (universe)

---

### Post by ilovethislinuxstuff on 2013-10-26
also, it shows up in the left side thingies that I can make the pointer make come out.

---

### Post by ilovethislinuxstuff on 2013-10-26
I mean the menu thing that I can make slide out on the left side with the pointer.

---

### Post by ant2 on 2013-10-26
It seems you typed lsub and not **lsusb** in the terminal. 

But, anyway, if it is showing in the launcher '*slide out thing*' it is being recognised.

Can you not just double-click the icon in the launcher. That should launch a file manager window for your USB disk

---

### Post by ilovethislinuxstuff on 2013-10-26
> **ant2 said:**
> It seems you typed lsub and not **lsusb** in the terminal. 

But, anyway, if it is showing in the launcher '*slide out thing*' it is being recognised.

Can you not just double-click the icon in the launcher. That should launch a file manager window for your USB disk

Sorry, You're right. I decided to explore while I was waiting for an answer from you guys and fould a video that I watched about how to install gparted. So I did it. I 'm now at the Gparted window and see that on the drop down menu I see my seagate external hard drive. Should I format it (not that I know exactly what format means other than erase something, but there shouldn't be anything on there). Do I format to NTFS? (I was reading that lots of folks do that). Thanks!

---

### Post by ant2 on 2013-10-26
Did you try opening the USB drive from the launcher by double clicking on its icon? If so did anything happen?

---

### Post by ilovethislinuxstuff on 2013-10-26
> **ant2 said:**
> Did you try opening the USB drive from the launcher by double clicking on its icon? If so did anything happen?

Yes, I just clicked it and what I see is a box with the file folder called seagate and next to that is something called autorun.inf and next to that is  a box called seagateexpansion.ico and then below and on the left is setup.exe

---

### Post by ilovethislinuxstuff on 2013-10-26
maybe I should just use the gparted software. It seems easier than trying to figure out what to click when I open the actual seagate file from the launchpad. It says on the box it's for windows xp, vista, 7, and 8. If if hit the setup or something, it seems like it might be a mistake. it looks like ntfs is already there. can I just start transferring files and if so, how do I do that?

---

### Post by Bashing-om on 2013-10-26
ilovethislinuxstuff: hey;


You must format that usb drive for a file system before you can write anything to it.
You may find ubuntu's GUI partition editor easier and less intimidating to use than the command line tools,

With the USB drive plugged in;
Boot the liveDVD -> try ubuntu mode -> dash, search term "gparted" -> icon;

GParted, upper right of the screen is all the drives GParted can see are listed. Make sure that you are sure of which drive is the USB drive
I would normally expect the internal hard drive to be sda
and the external drive to be sdb ---but, that is not necessarily so ... make sure of what you are working with ( a blank, unallocated space, - device)

Carefully read the help file, being confused and uncertain, we can get you over that - that part is fixable. Messing about with your installed hard drive is a horse of another color. Before you do, be sure .. the partition editor assumes that you know what you are doing, there is no forgiveness of a mistake.
In formatting and partitioning the USB drive, makes little difference if an error is made, at that point one can always go back and redo as there is no data to loose ! Just be sure that you are messing with the USB drive !

That said, using the editor is a piece of cake.
In the work pane right click on that unallocated space, select new device, set the format to ext4 and partition type as "msdos" (as this is a storage device, I suggest you use this older partition scheme, 4 primary partitions max); This step is only done once as it sets up the whole drive.
-Any action from "right click" can also be duplicated from options within the tool bar -

As a storage device you  might consider making up 3 primary partitions, music, videos, data and that fourth as an extended partition and leave it empty for future use.
Once more for each partition you are making right click on the unallocated space, -> new -> and fill in data in the pop up for the size of the partition you are making.

when all done with setting up .. in the tool bar choose "write changes to disk" -> in that pop up, review what the partitioner is going to do, if satisfied -> click the apply button.

[INDENT][INDENT]easier done than said !
[/INDENT][/INDENT]

---

### Post by ant2 on 2013-10-26
That sounds very much like a file manager window has opened and you looking at the contents of your Seagate USB drive that contains some Microsoft Windows specific files that are basically an icon image file (seagateexpansion.ico) a file to install some Windows software(setup.exe) and a file to automatically start the process when the USB drive in connected (autorun.inf). Just ignore these files, or delete them if you don't use Windows, or create a folder to put them in for future use should you not want to delete them. 

 Anyway, you should be able to drag and drop things into that window and they should be copied onto your Seagate USB disk. Formatting is probably not required. The disk is probably NTFS format that will work in Ubuntu and Windows.

---

### Post by ilovethislinuxstuff on 2013-10-26
"That said, using the editor is a piece of cake.
In the work pane right click on that unallocated space, select new device, set the format to ext4 and partition type as "msdos" (as this is a storage device, I suggest you use this older partition scheme, 4 primary partitions max); This step is only done once as it sets up the whole drive.
-Any action from "right click" can also be duplicated from options within the tool bar -

As a storage device you  might consider making up 3 primary partitions, music, videos, data and that fourth as an extended partition and leave it empty for future use.
Once more for each partition you are making right click on the unallocated space, -> new -> and fill in data in the pop up for the size of the partition you are making."

I formatted it already just now. As far as having separate partitions, do I really need them? I just want to transfer these files until I upgrade to the newest Ubuntu, then I will put these files back on my newest Ubuntu. Then I wanted to delete the external hard drive and then use it as a backup for all of my newest ubuntu. What do you think? And thank you all for your quick help. Really nice of you all!

---

### Post by Bashing-om on 2013-10-26
ilovethislinuxstuff;
No there is no hurry about setting up individual partitions. At a future time will make managing your files easier.

For now, copy and paste files to your heart's content, see what happens.

[INDENT][INDENT]my best regards
[/INDENT][/INDENT]

---

### Post by ant2 on 2013-10-26
If you are using the USB drive exclusively for Linux use you are probably best formatting it to ext3 or ext4. FAT32 format is pretty much universally recognised (ie. Windows, Mac, Linux) although there are partition size restrictions (I believe).

If partitioning for music, data,etc seems to much just use separate folders for now. Good file structures always come in useful at some point.

---

### Post by ilovethislinuxstuff on 2013-10-26
> **ant2 said:**
> If you are using the USB drive exclusively for Linux use you are probably best formatting it to ext3 or ext4. FAT32 format is pretty much universally recognised (ie. Windows, Mac, Linux) although there are partition size restrictions (I believe).

Oops. I already formatted to ntfs. Is that ok? Thanks for all of your help! I'm dragging and dropping away right now!

---

### Post by ilovethislinuxstuff on 2013-10-26
> **Bashing-om said:**
> ilovethislinuxstuff;
No there is no hurry about setting up individual partitions. At a future time will make managing your files easier.

For now, copy and paste files to your heart's content, see what happens.
[INDENT][INDENT]my best regards
[/INDENT]
[/INDENT]



Great! That's what I'm doing! Thanks again!

---

### Post by ant2 on 2013-10-26
No thats fine. It probably was NTFS anyway.

---

