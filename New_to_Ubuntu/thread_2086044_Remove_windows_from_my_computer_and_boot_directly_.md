---
title: "Remove windows from my computer and boot directly into Ubuntu?"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by MrNewie on 2012-11-19
Hello & thanks in advance. 
I am new to Ubuntu & Linux OS. I would like to learn more & managged to root through a lot of stuff to get this up & running on my laptop. I also read a troubleshoot to fix my broadband wireless card. Thanks to the person who gave the great step by step. I did not get your name but the fix worked & I am working wireless again:)..

I had flash backs to a basic program I wrote in the 6th grade. The last time I worked in a DOS system. I have been a faithful windows person. Until getting an I Phone & now have went to the other side. 

I will use windows because I work the the federal goverment as a VA nurse. Love my job & we use all electronic medical records. I am the local non IT geek to help all the staff use various programs. 

I would like to know if I need to remove windows from my computer. XP.  I can not boot it any more after loading Ubuntu. Which is fine we have several computers. Can I get my computer to but directly to Ubuntu or do I have to go thru the selcetion process. 


I wait for replies while I continue to read posts. Plz leave me any links, ideas or thoughts...Thanks.:guitar:

---

### Post by offgridguy on 2012-11-19
Since you mention the selection process, i assume you have the grub menu.
It should boot auto. to ubuntu, after about a 10-15 sec. pause.  Which you can
shorten.
   I am surprised you don't also have the option for XP.

---

### Post by MrNewie on 2012-11-19
Really I am very New & have no Idea what you are talking about

---

### Post by offgridguy on 2012-11-19
The grub menu consists of several lines at the top of your screen, the first line,
normally highlighted has words to this effect
ubuntu with linux kernal 3.2 generic

Depending on how many operating systems you have they will be listed under
this , if windows xp is there it should show about 5 or6 lines down from the top
if you select that,{highlight} + enter it would boot xp.
 But what is the selection process you were refering to?

edit; probably more to the point, did you install ubuntu alongside windows or did you install over windows
and wipe it?

---

### Post by MrNewie on 2012-11-19
ubuntu alongside windows, When I re start shut down then f10 offered & the asks to choose windows or Ubuntu.

---

### Post by offgridguy on 2012-11-19
> **MrNewie said:**
> ubuntu alongside windows, When I re start shut down then f10 offered & the asks to choose windows or Ubuntu.


edit; afterthought, this sounds more like a choice in the BIOS ?

---

### Post by westie457 on 2012-11-19
Lets find out how you did your installation.

Boot into Ubuntu then go to here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Scroll down the page to 'Getting Boot-Repair' and follow the installation instructions in the '2nd -Option'

When the program starts you will see the the first picture from the link. Go straight to the 'Advanced Options part. In the pop up window un-check every box in every tab that you can access. Only leave the 'Create a Boot Info summary' box checked. Click Apply. No changes will be made to your system and you will be given a URL.

Post that URL here so we can see what you installed and how. Then we can offer better advice to you.

Thank you


ps Welcome to the Fora.

---

### Post by MrNewie on 2012-11-19
[http://paste.ubuntu.com/1371569/](http://paste.ubuntu.com/1371569/)

---

### Post by MrNewie on 2012-11-19
> **MrNewie said:**
> [http://paste.ubuntu.com/1371569/](http://paste.ubuntu.com/1371569/)
[COLOR=#000]

Added But then deleted info too Long....

     [/COLOR]

---

### Post by MrNewie on 2012-11-19
I think I may hooked .. Especially when I lean a little (a Lot More) so that is coding:)

---

### Post by pqwoerituytrueiwoq on 2012-11-19
to delete windows:
open [gparted](apt:gparted)
unmount any ntfs/fat32 partitions
delete the ntfs/fat32 partitions
sudo update-grub
reboot to live cd and resize/move ubuntu to use the max space on the disk using gparted

---

### Post by offgridguy on 2012-11-19
Okay i thought this might be the case.
 
sda1/Wubi: 
You used the wubi install, thats okay, but it's something i have
no experience with, someone else will have to help you, sorry i can't do more.

---

### Post by westie457 on 2012-11-20
As things are at the moment you cannot remove Windows without removing Ubuntu at the same time.
There is however two approaches to achieve what you want. One way is to learn something and move the Wubi to its own partition. See this for guidance. [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

The other way is is using a LiveCD/USB and wipe the HDD and clean install.

Personally I would recommend the learning curve because it will retain Windows for you which you can still use for as long as you want and get rid of when you are fully ready.

---

### Post by YannBuntu on 2012-11-21
westie457 +1

You installed Ubuntu inside Windows (via Wubi) so don't follow pqwoerituytrueiwoq's suggestion (deleting Windows would break Ubuntu).

@pqwoerituytrueiwoq: for future reference, we can see it's a Wubi install by looking at the start of the BootInfo log  ([http://ubuntuforums.org/showpost.php?p=12363516&postcount=8](http://ubuntuforums.org/showpost.php?p=12363516&postcount=8))

---

### Post by linuxman72 on 2012-11-21
If you have a secondary hard drive or flash drive, then it should be easy to delete windows. Just start windows and put all the files you want from there onto the flash drive or hard drive, then do the same for Ubuntu. Then remove the drive and use a Live CD to install Ubuntu. Reatach your hard drive or flash drive and replace you files.

*Please have someone confirm what I am saying before doing it, even though I see no way that it could go wrong.

---

### Post by YannBuntu on 2012-11-21
@linuxman72: that makes sense. And that's the way I would use to migrate from Wubi to a standard install.
In MrNewie's case, that would be simple:
1) backup all documents on an external disk or DVDs (including the hidden files which are in your /home folder)
2) install Ubuntu the standard way ([https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)), choosing "Erase disk and install Ubuntu".

---

