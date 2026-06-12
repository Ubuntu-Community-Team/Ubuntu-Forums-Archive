---
title: "Installation help"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by redbeard45 on 2011-10-08
I am trying to install Ubuntu on a non branded Desktop computer (Pentium 4, 1 gig RAM,120g HD) that was previously running Windows XP. I just want to replace Windows, not dual boot. The Installation process starts, but when it gets to the Allocate Drive Space screen, I don't have any options. The Device for Boot Loader installation has  /dev/sda. If I click Install Now, I get a 'No root file system is defined - Please correct this from the partitioning menu'. Being a total newbie, I have no idea where the Partitioning Menu is, but I found Disk Utility in System Settings. I try using Disk Utility which shows Partitioning is Unknown Scheme which I guess is part of the problem. If I try any options, apart from the fact many have so many choices of which I have no idea what to choose, I can't do anything as it comes up with a 'daemon is inhibited' message. 
I'm not aware of missing any steps so why is this so difficult?

---

### Post by roger_1960 on 2011-10-08
Presumably you are running a Live CD and then trying to install.

Suggest you boot to the live CD and then delete the existing partition(s) on the hard disk before trying to install. This can be done by unmounting the drive and then  selecting the existing partitions in gparted (which is in system settings in the dropdown at top right (assuming you are using Natty)  Then use install using whole disk option.

This will of course completely wipe the hard drive (whether or not the installation works)

---

### Post by Quackers on 2011-10-08
Select the "use the whole disc" option from the installer menu.

---

### Post by redbeard45 on 2011-10-08
I really appreciate your help but there are things as a newbie you are saying I still can't quite follow or understand?

'Presumably you are running a live CD and then trying to install"

I Googled Ubuntu and followed the instructions on the page there.
I downloaded ubuntu-11.04-desktop-i386.iso, burnt this to CD and am trying to use this. 
Was this not the right thing to do?

I didn't want to TRY Ubuntu, I wanted to use it as I want to get rid of Windows 7 out of a small school I work in with a few desktops and notebooks - the IT support costs are killing the school's budget. But if they are all going to be this difficult, I'm having second thoughts!

If I use TRY Ubuntu, I only got black squares where the menus were so I guess there is an issue with the graphics card so I can't do anything because I can't see the menus in the trial version?

I have booted from the CD I made and choose Install Ubuntu. Excuse my ignorance but is this 'booting to the live CD"?'

You say to unmount the drive. If this was Mac or PC, I would be able to do this, but as a Linux newbie???

I cannot use GParted in Control Center as I get 'failed to run /usr/sbin/gparted as user root. Unable to copy the user's Xauthorization file'.

I have downloaded and run GParted on disk and deleted the partition so that now it shows Not Partitioned. Device shows /dev/sda

Still nothing shows on the Allowcate drive space???

The only thing that makes me feel slightly less than stupid is the fact so many other people seem to have troubles with the same thing???

Thanks again for your help in trying to get me through this very frustrating process!

---

### Post by Quackers on 2011-10-08
The ubuntu desktop iso file should be burned as an image to a disc (or flash drive). If your graphics card was supported you would get a screen which gives you the choice of trying Ubuntu or installing Ubuntu. Trying Ubuntu then loads a normal ubuntu desktop that you can use to see how it runs on your system.
As you can't see those screens you may need to use a boot option when booting from the cd.

What graphics card/chip is your system using?

---

### Post by roger_1960 on 2011-10-08
Hi

"Try" ubuntu means booting from the live CD.  This runs the OS from the CD without using or altering the hard drive on the PC.  It should all appear normal but will run very slowly as its from CD.

Install ubuntu runs the installer from the live CD.  As it is not using the hard drive it is able to erase it/write to it etc.

I guess you have burned the gparted iso and have deleted the old partition.

You should be able to now "try" ubuntu and then select the install ubuntu option from an icon on the desktop.  You should be able to choose the "use whole disk" option for installation.

As Quackers says, if the "try" ubuntu option doesn't work, there is probably an issue with hardware compatibility.  Its unusual as most older systems work.

---

### Post by redbeard45 on 2011-10-08
I followed the instructions on the Ubuntu page and burnt the iso file to CD which is what I am using to Boot from. I can't see anything wrong with what I have done here.
I have booted from the CD, I can see the options, and I chose Install Ubuntu, which is what I am trying to do. The only time I have had any difficulties with the black squares for menus is when I choose Try Ubuntu Without Installing, which I used in an attempt to get around the installation problem - this is not the main issue and we're getting off on a side tangent here.
The fact I can see the desktop and have not had any issues with menus etc when trying to Install Ubuntu means that the graphic card is not a problem for installing at least. It is failure to be able to find anything to install on when it comes to the Allocate Drive Space which has been there from when I first tried to install, (and is a problem to a number of others) that is driving me crazy???
Cheers and thanks

---

### Post by Quackers on 2011-10-08
Nobody is suggesting that you have done anything wrong :-)
When you selected the "try Ubuntu" choice what exactly happened? Did the screen go black or did the Ubuntu desktop load ok?
Has this hard drive ever been used in a Mac? Has it been used in a RAID array?
What is your graphics card?

---

### Post by roger_1960 on 2011-10-08
Hi again

If you don't get these options at allocate drive space:

    1 Erase Ubuntu Natty and reinstall
    2 Upgrade Ubuntu Natty to 11.04
    3 Erase everything and reinstall
    4 Some thing else.

(No. 3 should work)

Then I think perhaps you could try using the "alternate CD" from here [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download) 
instead of the normal Live desktop CD.   This means downloading the ubuntu iso again, burning a new disk and trying again.  The alternate CD has a text interface rather than graphical but can sometimes work where the graphical one does not.  Do answer Quackers questions as he may have a better idea...

---

### Post by redbeard45 on 2011-10-08
Quackers...

Loading try Ubuntu now...
Ubuntu splash screens with red dots/white dots...
Got Applications / System / and I think Firefox icon in top left corner. As soon as I click on Applications, turns into black squares and if I move the mouse, I can see the submenus flick for a nano second, and then black squares where the drop down menus have been remain.
The menus in each corner are also just coloured blocks which if I try clicking on them, I just end up with black squares everywhere.

History of computer is unknown (just started working at the school this year and anyone who would know has now moved on - the previous IT support person left Christchurch in New Zealand where the school is because of the earthquakes we have been having down here - a good one yesterday just when we think things are calming down!)  But as it has just been in a classroom, I can be very certain it has never been in a Mac or been used in a RAID array.

The computer has an Intel D865GLC board so according to what I have been able to find, as it is using the in built graphics card, it will use the Integrated Intel Extreme Graphics 2?

Roger_1960
Sorry - being a newbie, I have no idea what Natty is (I have seen references to it) let alone working out how to Erase, reinstall and Upgrade as suggested in point 1 and 2
In point 3, what do you mean Erase everything and reinstall? I haven't managed to install anything yet so I can't work out what you mean???

My thinking is that there is a problem with the boot sector on this disk? Would it help if I removed the drive and reformatted on a Mac as a Fat 32 or on another PC?

Thanks again for your help and apologies my frustration is coming through!

---

### Post by Quackers on 2011-10-08
Thanks. When booting from the cd, at the first purple screen (with the little man icon at the bottom) press any key. Choose your language then on the next screen select "check for errors" and see if any errors are found.

Did you check the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you go to system > admin > gparted dows that program start? Can you get that far? If so what does it show?

It could be that the partition table is corrupt. This would explain why the installer sees no partition table. It may help if you can put that drive in a system which is known to be working and see what a partitioning utility says about the partitions on it.

---

### Post by Lisiano on 2011-10-08
You can also just erase the partition table and make a new one using the Installer. Instead of using Use whole disk or anything else, pick Manual and press Create new partition table (This will wipe the current table making you lose every partition on the disk. Use with caution), then go back and pick Use whole disk.

While the Try Ubuntu problem you are experiencing is troubling and might point to problems after you install, it might be a false alarm (My first ever time trying any Linux distro (Kubuntu) didn't go well since it didn't like the Install option, worked more or less fine on Try then Install).

---

### Post by redbeard45 on 2011-10-08
Downloaded another iso disk, checked MD5sum in Terminal on Mac - hashes matched

Checked disk for errors - had already done this but no use trying again - no errors detected

Not sure where to go to get System Admin? I can go to System Settings - System - Gparted but I get a Failed to run / usr/sbin/gparted as user root - unable to copy the user's Xauthorization file - presumably as I am only a temporary user for installing - forget what it is officially called.

Later.....

Removed the drive and put in an external hard drive - Mac came up with message that couldn't recognize the disk! Repartitioned on Mac as FAT 32 and we've now got a partition to format and we're away.
Thanks for all your help. Hope I don't have to go through all this with the other computers in the school
Cheers and thanks

---

### Post by Ms. Daisy on 2011-10-09
> **redbeard45 said:**
> If I use TRY Ubuntu, I only got black squares where the menus were so I guess there is an issue with the graphics card...

As soon as I click on Applications, turns into black squares and if I move the mouse, I can see the submenus flick for a nano second, and then black squares where the drop down menus have been remain.
The menus in each corner are also just coloured blocks which if I try clicking on them, I just end up with black squares everywhere.


I know exactly what caused that problem if you encounter it again on the other school computers.  The graphics card isn't sufficient to run Unity, which is the GUI for Ubuntu 11.04 (version 11.04 is nicknamed Natty Narwhal).  You mentioned it was an on-board graphics card which exactly matches my solved problem.  I installed a used graphics card I got for $15 in a PCI port.  Of course I had to disable the on-board graphics through BIOS.  Then Ubuntu ran perfectly.  :KS  Good luck on the rest of the computers.

---

### Post by redbeard45 on 2011-10-09
There were two problems - the partition on the hard drive and the graphics card. I got Ubuntu installed okay but now I can't use it because of the lack of support for Unity - and this is a common Intel graphics card? I can't afford the time I have spent on this if all the computers are going to cause issues like this - far too much work to do - this is supposed to be my holiday . Might change my thinking and find some old Macs. They are less hassle and more reliable - build and forget!

---

### Post by Ms. Daisy on 2011-10-09
> **redbeard45 said:**
> There were two problems - the partition on the hard drive and the graphics card. I got Ubuntu installed okay but now I can't use it because of the lack of support for Unity - and this is a common Intel graphics card? I can't afford the time I have spent on this if all the computers are going to cause issues like this - far too much work to do - this is supposed to be my holiday . Might change my thinking and find some old Macs. They are less hassle and more reliable - build and forget!

I understand your frustration with the installation.  I have found the learning curve rather steep to really understand Linux systems- I just started a few weeks ago myself. But the GUI in Ubuntu is really user-friendly, I can navigate around it intuitively.  All OSs have their pros and cons.  I don't know about the "build and forget" part- absolutely every piece of software ever created has to be maintained and routinely updated.  

Have you looked into hiring someone to do the installations?  Seems like maybe a knowledgeable Linux user could find and fix the problems you're encountering in a fraction of the time it takes a newcomer.  I'm willing to spend that time because I want to immerse myself in Linux- that doesn't seem to make sense in your situation.  Surely one of your local computer repair shop could help.

---

### Post by Lisiano on 2011-10-10
I might suggest installing 10.04 as it's a LTS (Better in a school environment since LTS is generally more stable) and since in 10.04 Unity was not implemented yet which would give you a normal Gnome desktop. Or wait and try again with 11.10 (Or test it with a beta CD) which is not a LTS but seems to have Unity more or less perfected, it should come out in a few days or a few weeks, some confusion on the correct date.

---

