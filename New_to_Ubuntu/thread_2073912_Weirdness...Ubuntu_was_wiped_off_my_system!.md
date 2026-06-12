---
title: "Weirdness...Ubuntu was wiped off my system!"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by pandacookie on 2012-10-20
Last night when  I shut my computer down, things seemed fine. But this morning was a disaster...Ubuntu was wiped from my computer. All I got was a message about Grub recovery on a black screen, with a cursor to type commands. I had to reinstall Ubuntu 12.10 all over again. It was a real inconvenience. My question is how this could happen??? I thought it wasn't possible for Linux to get viruses, yet this behaviour certainly sounds like a virus corrupted things! I added a few repositories last night, but that was all I did! Could that have done it? I'm so confused...

---

### Post by Windoze Refugee on 2012-10-20
> **pandacookie said:**
> Last night when  I shut my computer down, things seemed fine. But this morning was a disaster...Ubuntu was wiped from my computer. All I got was a message about Grub recovery on a black screen, with a cursor to type commands. I had to reinstall Ubuntu 12.10 all over again. It was a real inconvenience. My question is how this could happen??? I thought it wasn't possible for Linux to get viruses, yet this behaviour certainly sounds like a virus corrupted things! I added a few repositories last night, but that was all I did! Could that have done it? I'm so confused...

This sounds like it might be whats happened to mine. Anyone know anything about a linux virus capable of wiping ubuntu completely?

---

### Post by pandacookie on 2012-10-20
Oh, I'm not saying it WAS a virus. But it sure seems weird that I woke up and my operating system was gone. When I went to install Ubuntu 12.10 again, it even said there was no operating system on the computer in the options where you can choose to install Ubuntu or do something else!! It's sooo weird!

---

### Post by Lisiano on 2012-10-20
First thing first. Ubuntu was probably NOT wiped. But grub was modified. This might happen under these reasons:
[LIST]
[*]You installed a GRUB tweaker which wiped /boot/grub and didn't recreate it
[*]You did something wacky to your system, like moving around the root filesystem (or /boot)
[*]You played around with DD (Disk Destroyer)
[/LIST]

Now the virus angle
[LIST]
[*]Viruses typically don't destroy data, they typically want your data for other reasons or they want to control your system, meaning they don't want to destroy your data.
[*]A locally run virus will only be able to modify files you own, unless run by root
[*]Launchpad PPAs don't contain viruses
[*]Viruses are not common on Linux, but they DO exist (A handfull).
[/LIST]

EDIT: Since you say Ubiquity reported you having no OS installed, then there is a chance you actually might have wiped your system. Could you tell us what programs you installed/ran yesterday?

---

### Post by Mr.Dunham on 2012-10-20
I agree it's weird. Did you try a Live CD to see if the system was there or not? A boot failure would say the system is gone even if the system was there. Of course in that case it's easier to install it again than trying to recover the whole thing.

---

### Post by pandacookie on 2012-10-20
Before I upgraded to 12.10, I DID do some tweaking to Grub. That was when I had a dual boot system. I used to have Windows. But then I decided to just wipe out Windows and have just Ubuntu, so I reinstalled 12.05. Then 12.10 came out and I upgraded...hope you can follow all this...then this happened. Could what I had done in the past been the reason for all this? And why is it, when I went to reinstall 12.10, it said I had no operating system?

---

### Post by pandacookie on 2012-10-20
> **Mr.Dunham said:**
> I agree it's weird. Did you try a Live CD to see if the system was there or not? A boot failure would say the system is gone even if the system was there. Of course in that case it's easier to install it again than trying to recover the whole thing.

That's what I forgot! It DID say it was a boot failure. Then I got the message about grub. So I reinstalled it. I DID try a Live CD and that's when I found out there was no OS.

I'm so worried now that this will happen again.

---

### Post by Lisiano on 2012-10-20
Am I right in the following?[LIST=1]
[*]You have Ubuntu 12.04
[*]Reinstalled Ubuntu 12.04 with a disk wipe to get rid of Windows
[*]Performed an Upgrade from Ubuntu 12.04 to 12.10
[*]System no longer boots.
[/LIST]

Or did the following happen?[LIST=1]
[*]You have Ubuntu 12.04
[*]Reinstalled Ubuntu 12.04 with a disk wipe to get rid of Windows
[*]Performed an Upgrade from Ubuntu 12.04 to 12.10
[*]Booted into Ubuntu 12.10 and installed new repositories
[*]System no longer boots.
[/LIST]

Also, what repositories did you add?

---

### Post by pandacookie on 2012-10-20
> **Lisiano said:**
> 
EDIT: Since you say Ubiquity reported you having no OS installed, then there is a chance you actually might have wiped your system. Could you tell us what programs you installed/ran yesterday?

Now that I remember (and am calmer), I installed [FONT=Arial][COLOR=#FF0000][FONT=monospace]libdvdcss2, so I could play DVDs. I tried to install some stuff on [this page]("http://apcmag.com/how-to-play-blu-ray-in-linux.htm") to try to play blu rays[/FONT][/COLOR][/FONT]. And I added a few repositories. And I used Firefox. That's it.

---

### Post by pandacookie on 2012-10-20
> **Lisiano said:**
> Am I right in the following?
[LIST=1]
[*]You have Ubuntu 12.04
[*]Reinstalled Ubuntu 12.04 with a disk wipe to get rid of Windows
[*]Performed an Upgrade from Ubuntu 12.04 to 12.10
[*]System no longer boots.
[/LIST]

Or did the following happen?
[LIST=1]
[*]You have Ubuntu 12.04
[*]Reinstalled Ubuntu 12.04 with a disk wipe to get rid of Windows
[*]Performed an Upgrade from Ubuntu 12.04 to 12.10
[*]Booted into Ubuntu 12.10 and installed new repositories
[*]System no longer boots.
[/LIST]

Also, what repositories did you add?

It was the second instance. As for the repositories, I don't remember. Could that have done it? Could installing repositories cause a complete wipe??

---

### Post by Lisiano on 2012-10-20
Hmm. Judging by that link, not from that.
No, installing a repository can't do any damage, installing software from a repository can. Unless you can remember what repository you added, we can't tell you if the fault was because of that repository.

Hmm. I am now starting to think that it might have been your hard drive. It might have bad blocks and a few (Unluckily) appeared in the MBR.

To check for bad blocks, open up the Disks utility in Dash, press the Options button (Gears) on your HDD and select SMART Data and Tests. This will tell you the state of your HDD, also, please run the Extended self test, this way you will find out if there are any problems with the disk.

---

### Post by pandacookie on 2012-10-20
> **Lisiano said:**
> Hmm. Judging by that link, not from that.
No, installing a repository can't do any damage, installing software from a repository can. Unless you can remember what repository you added, we can't tell you if the fault was because of that repository.

Hmm. I am now starting to think that it might have been your hard drive. It might have bad blocks and a few (Unluckily) appeared in the MBR.

To check for bad blocks, open up the Disks utility in Dash, press the Options button (Gears) on your HDD and select SMART Data and Tests. This will tell you the state of your HDD, also, please run the Extended self test, this way you will find out if there are any problems with the disk.

It doesn't have any options for a SMART test or Extended test. I clicked on the gears and there are options to format, edit patition type, edit filesystem label, edit mount options, create disk image, restore disk image, and banchmark volume. It does say disk is okay in the assessment, though.

---

### Post by Windoze Refugee on 2012-10-20
With mine I was aware of some bad blocks on the HD and in fact backed up everything on that drive to another HD.
Are you saying that failing blocks might produce the same results?
I ran rescatux and had it 'find all OS's". It only managed to find windoze.
It used to be i could select from a bunch of OS options at grub boot and it was only my current Ubuntu which would fail (go back to flashing cursor). it wold still boot into windoze.
Now i don't even get the grub boot options.

Any ideas about how to do a clean install of ubuntu on a new HD and then copy everything across for the back up location? (I mean progs and all, not having to do it literally file by file)?

WR

---

### Post by grahammechanical on 2012-10-20
All we know for sure is the Grub is still in the MBR of the hard disk and it was unable to boot an linux image. So, it gave you a Grub prompt so that you could investigate. It might have given you some error messages.

You could have tried booting into recovery mode from the Grub menu.

What is the basis for saying you had to re-install? But you did re-install. Is it working now?

Changes to the system, especially changes to boot processes do not get noticed until the next boot.

Regards.

---

### Post by Lisiano on 2012-10-20
The test is in the SMART Data and Tests, click the Start Self-Test button.

---

### Post by Windoze Refugee on 2012-10-20
weirdly I can't even get Ubuntu to run in live mode from the CD either

---

### Post by pandacookie on 2012-10-20
I just installed GSmartControl from the Software Center. Running tests now..will edit with results...

EDIT: Short self test showed no errors. Doing extended test now just to make sure. That won't be done for a while, though.

---

### Post by Lisiano on 2012-10-20
> **Windoze Refugee said:**
> weirdly I can't even get Ubuntu to run in live mode from the CD either

Please create a new thread and don't hijack other threads.

---

### Post by pandacookie on 2012-10-20
> **grahammechanical said:**
> All we know for sure is the Grub is still in the MBR of the hard disk and it was unable to boot an linux image. So, it gave you a Grub prompt so that you could investigate. It might have given you some error messages.

You could have tried booting into recovery mode from the Grub menu.

What is the basis for saying you had to re-install? But you did re-install. Is it working now?

Changes to the system, especially changes to boot processes do not get noticed until the next boot.

Regards.

I didn't know how to boot into recovery. I reinstalled because I didn't know what else to do. I'm still new to Linux. I've only been doing this for two weeks.

EDIT: I forgot to add that the computer is working now, yes. But could it happen again?

---

### Post by Windoze Refugee on 2012-10-20
> **Lisiano said:**
> Please create a new thread and don't hijack other threads.

Didn't think I was highjacking, as its part and parcel of the same problem...

---

### Post by Lisiano on 2012-10-20
> **Windoze Refugee said:**
> Didn't think I was highjacking, as its part and parcel of the same problem...

Your problems differ in the aspect the OP wants to know what happened and his system is currently up and running, while yours is not and according to you, not booting in a Live session, making your problem separate from this one.

---

### Post by squakie on 2012-10-20
I don't know where such things are held on the disk, but perhaps somehow the partition table is getting screwed up?

---

### Post by pandacookie on 2012-10-20
> **squakie said:**
> I don't know where such things are held on the disk, but perhaps somehow the partition table is getting screwed up?

If Ubuntu is the only OS on the computer, I don't see how. Unless it's from all my past tinkering. But the reinstall supposedly wipes everything off the disk, right? 

I don't know. The extended self test will tell us more. Only two more hours to go! :)

---

### Post by pandacookie on 2012-10-20
Extended test result completed without error. So I guess it's not the hard drive. Any other ideas?

---

### Post by pandacookie on 2012-10-21
Anyone?

---

### Post by pandacookie on 2012-10-22
I'm still wondering...perhaps we'll never know? It's been two days and the computer runs fine.

---

### Post by black veils on 2012-10-23
if it happens again, you could boot a live cd/usb stick and get log files etc for information, and keep a list of ppa's and other software installed.

so people, what files would they want to collect for such data, if this situation happens again? or anything else i might not have thought of.

---

### Post by mastablasta on 2012-10-23
> **pandacookie said:**
>  But the reinstall supposedly wipes everything off the disk, right? 

 
no. if you just reinstall then it just overwrites old files with files on the image. if you had any additional files that cause your grub to get corrupted then they would stay there.
 
however if you reinstalled and during reinstall chose to format the drive that should erase everythign on it.
 
if you get only grub problem they can be solved with boot repair tool: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
no need to install the whole OS just to fix the grub.
 
i doubt it was a virus in this case but then again rootkits are OS independent and hard to remove, so if you picked one on windows....

---

