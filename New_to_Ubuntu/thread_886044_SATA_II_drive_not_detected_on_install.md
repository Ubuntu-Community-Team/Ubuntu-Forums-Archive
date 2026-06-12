---
title: "SATA II drive not detected on install"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by demon-fox on 2008-08-10
Hello All,
wanted to experience the world of linux, hence got myself a new SATA 2 drive (hitachi 400GB)
HAve read around the web and wanted to dual boot with ubuntu on the new hard disk and vista present on the old one.
i got a 64bit intel dual core processor and tired installing ubuntu with little sucess.
its gives me a couple of revalidation errors and continues with the install, the problem is when it comes to the partition. it doesnt give me any options, its blank. i can safely conclude that the cables are good, well connected and the hard disk is functional. The partition mananger on the live session doesnt want to recognise any drive either.
I succesfuuly manager to install ubuntu on a older machine of mine with no problems.
Would be gratful for any suggestions or solutions.
Many thanks

---

### Post by Crafty Kisses on 2008-08-10
Post the output of ```
sudo fdisk -l
```

---

### Post by demon-fox on 2008-08-14
> **Codename said:**
> Post the output of ```
sudo fdisk -l
```
thank you codename,
i've been pondering on how to run sudo fdisk -l for a while.
as you know i cant seem to install the hard disk cause it ubuntu does not want to recognise it. Tried running the command from the live session user and there was no output, just jumps to the next line.
Intresetingly i have been trying to install both ubuntu versions, the 64 bit or 32 bit neither worked and gave me similar revalidation errors.
Just as a final slog i tired the 32 bit version and it recognised the hard disk the next day, i hadnt changed anything, well completed the installation and ubuntu boot loader kicks in when i start the computer.
but sadly the systems just hands when i ttried to boot from the new hard disk with ubuntu.
any thoughts, pr do you think novices like me should just bear with windows :)

---

### Post by power.supply on 2008-09-02
I have the exact same problem. I am running an Intel Core 2 Duo E7200 with a Seagate 160GB SATA II HDD, Gigabyte GA-EP45-DS3L motherboard. Any help would be great. I don't know if this is an issue but I am using an IDE Sony DVD Burner along with this drive. Could this be causing a conflict?

---

### Post by Crafty Kisses on 2008-09-03
Personally if you are novice at Linux and want to use it, stick with it. If you don't want to cope with the learning curve, maybe Linux isn't for you.

---

### Post by brentoboy on 2008-09-03
1st thing:  Check the BIOS to see if the drive is recognized by the system at all.  If BIOS doesn't see it, it is not going to work with any operating system.  You can get into the BIOS by hitting F2 or DEL or F1 or... depends on the motherboard you have which button takes you to BIOS.  But look for the message to "click ___ to enter setup." 

Anyway, pop out the drive and read the fine print.  There is probably a jumper you can put across a couple of pins that makes it compatible with the older SATA. I know that there was a jumper that makes a SATA 3.0 behave like a SATA 1.5 for older motherboards, perhaps there is a similar jumper on your HDD.

Either way, it wont show up in ubuntu until it shows up in the BIOS.

If it shows up in the BIOS but not in ubuntu, you might have a really new SATA chipset, and it might not be supported until the next round of ubuntu.  I had a sata cdrom drive that didnt work until breezy came out.

---

### Post by Liviu-Theodor on 2008-09-03
First check in your BIOS (when you start-up your PC, after detecting the video card, before detecting the IDE drives, is a message [FONT="Century Gothic"]Press <key> to enter setup...[/FONT] - press that [FONT="Courier New"]<key>[/FONT]) if the SATA connection are enabled, and if they are used as SATA, not RAID devices.

---

### Post by zavalita on 2008-09-04
> **Codename said:**
> Personally if you are novice at Linux and want to use it, stick with it. If you don't want to cope with the learning curve, maybe Linux isn't for you.

Hello, I have a related issue, my SATA RAID drives from my Abit MB aren't seen when I play the Live CD. I have a hardware RAID, of course. Ubuntu sees the other two 'normal' drives,even automount them (that was cool) but not the ones connected by RAID. 
Also a funny one : I've installed Opera, the best internet tool ever;) and though the installation worked like a charm , I couldn't find the shortcut or even the program itself at all. I've searched the whole damn Ubuntu, and all the applications and my Opera was nowhere to be found. Very strange ! And I need that browser !

---

### Post by cariboo on 2008-09-04
Have you tried Alt-F2 or a terminal to start opera? Most applcations get installed in /usr/bin. to find an installed program in a terminal type:

```
locate opera
```

After you have located the program you can manually create a link to it in the main menu.

Jim

---

### Post by Liviu-Theodor on 2008-09-05
> **zavalita said:**
> Hello, I have a related issue, my SATA RAID drives from my Abit MB aren't seen when I play the Live CD. I have a hardware RAID, of course. Ubuntu sees the other two 'normal' drives,even automount them (that was cool) but not the ones connected by RAID. 
Also a funny one : I've installed Opera, the best internet tool ever;) and though the installation worked like a charm , I couldn't find the shortcut or even the program itself at all. I've searched the whole damn Ubuntu, and all the applications and my Opera was nowhere to be found. Very strange ! And I need that browser !

This is a very known issue, and probably you have a "fake RAID", integrated on the motherboard. This means you must have a software for RAID, and the CPU does the work (not the RAID controller). You can find help on [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto").

---

### Post by Liviu-Theodor on 2008-09-05
> **zavalita said:**
> Hello, I have a related issue, my SATA RAID drives from my Abit MB aren't seen when I play the Live CD. I have a hardware RAID, of course. Ubuntu sees the other two 'normal' drives,even automount them (that was cool) but not the ones connected by RAID. 
Also a funny one : I've installed Opera, the best internet tool ever;) and though the installation worked like a charm , I couldn't find the shortcut or even the program itself at all. I've searched the whole damn Ubuntu, and all the applications and my Opera was nowhere to be found. Very strange ! And I need that browser !

If you want to use the software ubuntu RAID, make sure you back-up any data on the fake RAID before, as it will wipe out any data on it. And it is better to use for it the "ubuntu alternate live CD" or the "ubuntu dvd" (or kubuntu, or xubuntu, or edubuntu). And you can search for answers also on the [https://help.ubuntu.com/]("https://help.ubuntu.com/").

And from there I reccomend the following pages:
    [https://help.ubuntu.com/community/Installation/FileServerWithRAID]("https://help.ubuntu.com/community/Installation/FileServerWithRAID")
    [https://help.ubuntu.com/community/Installation/RAID1]("https://help.ubuntu.com/community/Installation/RAID1")
    [https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

---

