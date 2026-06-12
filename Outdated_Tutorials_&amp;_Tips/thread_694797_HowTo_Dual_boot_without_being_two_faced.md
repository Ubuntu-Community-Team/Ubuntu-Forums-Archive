---
title: "HowTo: Dual boot without being two faced"
date: 2008-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by NipitMaster on 2008-02-12
This is a Guide to make dual-booting between Windows and Linux a much more enjoyable experience.

Following this guide will allow you to:

1) Allow Windows to read and write to your Linux file system.
2) Keep your desktop files static between Windows and Linux.
3) Keep your firefox sessions and bookmarks static across Windows and Linux.
4) Keep your media folders static too.

The entire process will be done from Windows. I will assume you are using Vista, but you can still follow this tutorial on XP, and 2000. I will aslo assume your username for both Windows and Linux are Nipit. Use your username instead.

**1.========Installing Ext2,3 Driver========**

First download (SAVE!) and install an Ext2 driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) It's even signed for us x64 Vista users! It's important to keep this installer because it must be reinstalled from time to time; mainly when you change your partitions.

For the sake of this tutorial I will pretent you set your linux drive as U: (for Ubuntu)

[B]2.========Move files to your linux home folders=========
[/B]
Open your user folder. ("C:\Users\Nipit" for Vista "C:\Documents and Settings\Nipit" for other win OS) You should see your desktop folder, music, documents etc... Move all the contents out of Desktop, Documents, Music, Pictures, Videos and any other folder you want into the coresponding folder in the linux home folder. Then delete the now empty folders in your windows user folder.

NOTE: Your media libraries such as iTunes and Windows Media Player will remain intact as long as you don't open them before step 3.

**3.========Create Symbolic links/Junctions===========**

WARNING: YOU NEED SPECIAL PROGRAMS TO DELETE A JUNCTION WITHOUT DELETING IT'S TARGET!!!
USE THE METHOD DESCRIBED IN THE "REVERTING CHANGES" SECTION.

In your start menu goto All Programs >> Accessories >> Comand Prompt. Right click on "Command Prompt" and "run as Administrator".

Now it is different for each win OS:

----Vista(Symbolic Links):

Type: mklink /D C:\Users\Nipit\Desktop U:\home\nipit\Desktop
repeat this for each folder you deleted in step 2.

-----XP(Junctions):

IF THIS DOESN'T WORK USE WIN 2000 METHOD.

Type: cd "C:\Documents and Settings\Nipit"
Type: Desktop U:\home\nipit\Desktop
repeat this for each folder you deleted in step 2.

----2000(Junctions):

go here: [http://www.microsoft.com/technet/sysinternals/FileAndDisk/Junction.mspx](http://www.microsoft.com/technet/sysinternals/FileAndDisk/Junction.mspx)
Scroll to the bottom and download junction
extract junction.exe to your home folder (C:\Documents and Settings\Nipit)
navigate there in command prompt (cd "C:\Documents and Settings\Nipit")

Type: junction Desktop U:\home\nipit\Desktop
repeat for each folder you deleted in step 2.

**4.======Firefox==========**

Install Firefox on both OS if you havn't already.

You will only use your Linux bookmarks and sessions. If you'd rather start from your windows bookmarks and sessions, copy the folder C:\Users\Nipit\AppData\Roaming\Mozilla\Firefox\Profiles\????????.default to U:\home\nipit\.mozilla\firefox\ and use the copied folder in the details below. (you may want to write the number down)

press win + r on your keyboard to open the run command. Type "firefox.exe -ProfileManager"

press "Create Profile" then "Next"
Pick any name (I used Ubuntu)
Then "Choose Folder..."
Select U: >> home >> nipit >> .mozilla >> firefox >> ????????.default
Then hit "Finish"

If you copied you windows profile to your linux drive do the following from linux:
	press alt + F2 to open the run dialog.
	Type: firefox -ProfileManager
	press "Create Profile" then "Next"
	Pick any name
	Then "Choose Folder..."
	Select / >> home >> nipit >> .mozilla >> firefox >> ????????.default (the one you copied)
	Then hit "Finish"

**5.=======Congrats======**

Pat yourself on the back, you can now switch OS without switching your life :D






**X.*********Reverting changes************

-------Removing a Junction------
If you did not do the following in step 3 do this now:
	go here: [http://www.microsoft.com/technet/sysinternals/FileAndDisk/Junction.mspx](http://www.microsoft.com/technet/sysinternals/FileAndDisk/Junction.mspx)
	Scroll to the bottom and download junction
	extract junction.exe to your home folder (C:\Documents and Settings\Nipit)

navigate there in command prompt (cd "C:\Documents and Settings\Nipit")

Type: junction -d Desktop
repeat for each junction you created in step 3.

Create all the folders you deleted in step 2 by browsing to your user folder (C:\Documents and Settings\Nipit) and right clicking and hitting create folder.

Then move all the contents you moved in step 2 back to the respective folder.

-------Removing Symbolic Links (Vista)--------
Simply browse to your user folder (C:\Users\Nipit) and delete all the links you created in step 3. This will not 

delete the targets of the links.

Vista will recreate the Desktop, Documents, Music, Pictures and Videos Folders, but it can take a while, so 

creating them manualy may be faster. All other folders you deleted in step 2, will need to be recreated manualy by 

right clicking and creating new folder.

Then copy all the contents you moved in step 2 back to the respective folder.

-------Firefox-----------
press win + r on your keyboard to open the run command. Type "firefox.exe -ProfileManager"

select default and hit launch firefox.

repeat in linux if you copied your Windows profile to linux AND want to revert it.

-------Removing Ext2&3 Driver--------
IF YOU DON't DO THIS LAST YOU CANNOT MOVE YOUR FILES BACK TO YOUR USER FOLDER.

Open Control Panel and open "Programs and Features" (Vista) or "Add/Remove Programs" (XP,2000)
Find the program starting with "Ext2 IFS" Select it and press Uninstall.

---

### Post by lex1 on 2008-02-17
If you have a spare minute i wonder if you might tell me how you partitioned your disk for the three os 

I have a intel imac and am going to have ubuntu on one partition the 2nd then xp on the third. OS x tiger is on the first thats my plan

thanks for any feedback

lex1

---

### Post by NipitMaster on 2008-02-17
What I suggest you do is pick one partition as your main partition for personal files. Make sure all OS you install can read and write to it. I don't know what formats OSX can read or write to so its up to you.

If you want to use a nonlinux partition as your main partition for personal files, you would want to use the "ln" command in step 3 to have you linux folders point to another partition. Make sure that whatever partition you are pointing to will be mounted at boot by adding it to your fstab.

ln -s {target} {pointer}
example:
ln -s "/media/XP/Documents and Settings/Nipit/Desktop" home/nipit/Desktop

You will probably also want to append /home/nipit/.config/user-dirs.dirs with the new locations.

Your particular partition sizes will depend on you. I use Have a 10GiB fedora partition, and the rest of my drive split even between Ubuntu and Windows. All my media files are stored on my Ubuntu partition which is why it gets almost half, and Windows has my games and work applications wich is why it also gets almost half.

Just think ahead to what you will be installing and storing on each partition.

I will be chillin with my friend tonight who uses a mac, so I'll see if I can figure anything out for you.

---

### Post by rosegarden78 on 2008-02-18
> **NipitMaster said:**
> This is a Guide to make dual-booting between Windows and Linux a much more enjoyable experience.

Pat yourself on the back, you can now switch OS without switching your life :D


What about VirtualBox virtual PC?  It's free and so easy.  Sometimes you have to Chown the program directory at the terminal.  Then you don't have to switch use both at same time.  Except Winmodem probably won't work if you need fax capability dual-boot.  Otherwise VirtualBox is perfect for me.

P.S.  Just max out your RAM with 1 Gb (512 MB for host system / 512 MB for virtual) because each "virtual computer" running needs it's own memory.

---

### Post by NipitMaster on 2008-02-18
OSX uses the same ln command to create the symbolic links. Since OSX doesn't natively support writing to NTFS and doesn't support ext3 at all, you could find a third-party application that can read & write to one of them or have another partition in FAT32. Finding a third party app would be the option that I would prefer, because having a lot of partitions can get aggravating when one gets full.

---

### Post by NipitMaster on 2008-02-18
> **rosegarden78 said:**
> What about VirtualBox virtual PC?  It's free and so easy.  Sometimes you have to Chown the program directory at the terminal.  Then you don't have to switch use both at same time.  Except Winmodem probably won't work if you need fax capability dual-boot.  Otherwise VirtualBox is perfect for me.

P.S.  Just max out your RAM with 1 Gb (512 MB for host system / 512 MB for virtual) because each "virtual computer" running needs it's own memory.

Virtual machines are great, but not for everyone. My personal reasons for not using it, is that I'm a 3D animator and wouldn't be able to handle the performance while rendering.

Not to knock you or anything, but some of us have to dual boot. This just makes it less painful.

---

