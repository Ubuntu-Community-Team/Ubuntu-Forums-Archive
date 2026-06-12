---
title: "problem partioning for linux mint"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-23
I have already posted this on the Mint forum. So I hope nobody minds me posting it here too.

Hi I am using the linux mint live cd, and attempting to partition the c drive to enable dual booting with linux mint, and windows xp,
I already have xp installed .The drive is in the NTFS file system.
So i clicked install on the live cd desktop.
after questions about region and keyboard layout Oddly, none so far about name or password, I chose the manual option. 
I then right clicked and choose the edit option. But There is no option to choose a size for the linux system. I would like to post a screen image here, but no sucess. I chose upload attachment. it says done, but no sign of the attachment.
anyway the "prepartions" window has in device box /dev/sda, then on the line below that /dev/sda1, then in the type box "ntfs" In the size box it says, it says 240048mb. In the used box, it says "unknown" 
Below that on the third line in under devices it says /dev/sda28 mb in .
I right click  /dev/sda. , new partion, edit partion, and delete partition are greyed out ie not usable. New Partition table is usable.I click "new  partition table" I'm told that choosing this option would remove all current partitions. So assuming that would remove my windows files, I disregard that.
I right click /dev/sda1. I right click and get "use  as -format the partition-mount as". There is no message about entering a number for the linux partition. I know this is an option, as I have seen it when right clicking an external hard drive in the installation menu. But i read that i have to create a partition for Linux on the same drive as Windows is located on. Anyway i disregard this option, as formatting would lose me my windows files.

okay, back on windows now. I looked in disk management, and see the hard disk is marked as primary. There is no option to partion. I should say the disk is 232 gigs with 230 gigs free.
M

---

### Post by bobnutfield on 2008-11-23
It is much easier to install for a dual boot if you prepare your disk first before beginning the install.  You can do that from the Live CD using the Partition Editor.  You will want to shrink your Windows partition first, which I am guessing is currently using the entire disk.  **BUT BE SURE TO DEFRAGMENT YOUR WINDOWS PARTITION AT LEAST THREE TIMES BEFORE YOU ATTEMPT TO RESIZE IT.  FAILURE TO DO SO *COULD* CAUSE YOU PROBLEMS.  **

You need to determine how much space you want for MINT.  If you are only going to have MINT and Windows, you could simply use half for each.  So, a suggested (only a suggestion) partition  scheme would look like this:

Windows /dev/sda1      100GB
MINT  /dev/sda2      15GB
Swap    /dev/sda3        1GB  (depending on your memory)
/home   /dev/sda4      100GB   

This will be the four primary partitions you are allowed to allocate.  This could all be set up with the Partition in the Live CD, and during the install you just choose manual partitioning and assign the already created partitions as above.

---

### Post by Paqman on 2008-11-23
If you're having trouble shrinking the NTFS to make room for Linux, make sure that it isn't mounted. You should be able to right-click on the partition and select "unmount".

---

### Post by kansasnoob on 2008-11-23
I personally prefer using Gparted to do my partitioning in advance like it shows here:

[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

I'll grant you that it shows installing a dual boot with two Linux systems, but otherwise it's the same situation.

Here's some graphic detail of the method you're trying to follow:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

---

### Post by irish66 on 2008-11-23
Thanks for the response folks
I'm actually using this link
[http://linuxgazette.net/136/lazar.html](http://linuxgazette.net/136/lazar.html)
as a guide 

To Bob N, Yes I had been using the partition editor.
Thanks for advice on how to divide up the HD.

To Paqman-Yep, i did have the drive mounted. That was indeed the problem.
I had just rebooted into linux live cd, and allocating space option came up.
That's because I hadn't mounted the volume.
So let's see how things go.
M

---

### Post by irish66 on 2008-11-23
Well, you won't be surprised that I made a hames of it on a number of occassions. THe first time I chose manual, but the program aborted. So i clicked "choose largest free space, and of couse that didn't leave enough for windows to load. So after reinstallig windows, which ended up as a small c drive of about 3gigs and a large f drive of about 230 gigs containg windows files etc etc, i used the live cd installation again.I choose manual. I right clicked the largest size partion ie the one with the windows files on it, AND CHOSE a resize of  10000 mbs. Now the options showing was "do not use this partion" or something like that. So i left it at that. (i can't see, because right now I'm back in windows) But i think it was in the file type option. so i clicked "forward" it partioned. But i was told i had to create a root. So I went back, and tried to undo the partition. But then the main install menu appeared, and  showed in guide option that under 4 gigs was allocated to mint. That was a surprise to me.So i tried undoing  the changes [anybody fall asleeep yet :)]. and booted back into windows, hoping that I hadn't overwritten my windows folder.
I hadn't. But now i had a c drive of 2.31 gigs, an f drive of 7.45 gigs and an allocated drive of 223.12 gigs. Right now I'm formatting that drive in windows disk management.
So when that's all done, I'll try again.
So when the edit drive size comes up, i'll choose choose 20000
I believe that's 20 gigs. I assume that will be for Mint. my first question is what file system, should I use, and I assume this the root, and i choose :/ for that.
Well going to bed now, and will check back tommorrow.
Thanks again folks.
Sorry, yes I know there is information on those links. But it can be a bit overwhelming.
M

---

### Post by irish66 on 2008-11-24
okay so I'm gonna try again, or at least start off.
as noted before my hard drive is now in 3 partitions
c=2484 mbs-1100 used=dev/sda1 ntfs
f=8003 mbs-4000 mb used=devsda5
g=239569 mbs-3200 mbs used=dev/sda3 ntfs

so i right click dev/sada3 as it's the largest
and choose edit partion
i entered 7395 in the new partion size in megabytes box.
I'm choosing ext3 as the file system  
I'm choosing / as mount point
i don't tick box that gives me the option to format partion
pressing "forward"
partions formatting
ok "resizing partion" dialogue on screen, but it seems to be hanging at zero.
I'm going out shortly, but would be interested to know if i have done everything correctly or incorrectly so far.
3 or 4 minutes later, still at zero.
oh dear-when i chose the ext3 file system option-did i tell it to convert the whole g drive to that format, or just the space i freed up.
Well-new message "An error occured while writing the changes to the storage devices. the resize operation
has been aborted"
M

---

