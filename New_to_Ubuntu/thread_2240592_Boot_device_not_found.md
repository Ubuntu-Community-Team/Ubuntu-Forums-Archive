---
title: "Boot device not found"
date: 2014-08-21
forum: New to Ubuntu
---

### Post by tom_kelly2 on 2014-08-21
[SIZE=2]Hey, running latest LTS version of Ubuntu, worked fine yesterday but failed to boot this morning.

I've tried boot repair with no success, still getting the following error on startup: [/SIZE][h=1][SIZE=2]"Reboot and select proper boot device or insert boot media"[/SIZE][/h][SIZE=2]
[http://paste.ubuntu.com/8104048/](http://paste.ubuntu.com/8104048/)

Please help[/SIZE]

---

### Post by Jonathan Precise on 2014-08-21
Hi tom_kelly2. Welcome to the forums!

[QUOTE=tom_kelly2 in pastebin]Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
**Perhaps it was corrupted** -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?

                                                                          
[B]Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.[/B][/QUOTE]

Looks like something messed up your install. Are you using UEFI or BIOS?

Do you have too many files in your install? If you don't, fire up GParted from your Ubuntu DVD, and create a new partition table using GPT for UEFI or ms-dos for BIOS (in all cases **WIPING ALL DATA**), apply the changes, and re-install Ubuntu.

---

### Post by yancek on 2014-08-21
The most common reason I have seen for that error is having a non-bootable medium in the drive while that drive is set to first boot priority.  If it is a CD/DVD drive, the system would usually skip it and go to the hard drive.  First thing to check.

After viewing your boot repair script, I guess the above is not the problem.  Your 1TB drive shows as a Linux (ext4) filesystem but it doesn't show the other details it usually does such as boot files on the partition.  If you read further down, it tells you your GPT table is corrupt.  It does show a separate EFI boot partition but not the files usually shown in the script.  Also, you seem to be using LVM.  If this is a new install you might be better off and find it easier to reinstall.

---

### Post by tom_kelly2 on 2014-08-21
Thanks for the response guys, I saw the GPT error but I don't know what it means or what to do about it. I assume I'm using BIOS but I don't know, how do I check that?

I'm confused because this computer has been running fine for months (and rebooted with updates just a few days ago). Do you think it's a recent update causing this?

As far as I know, there aren't any CD/DVDs booting. If there is only the two internal hard drives (second one mounts in BIOS, my colleague set it up and it's worked for months) I get the error and no boot. I've booted the "Boot Repair" tool from a USB which returned no errors repaired and the  output linked above. Sorry for being a newbie guys, does this mean I need to boot/reinstall from a USB? Will this lose data? I have back ups of crucial thesis-related data but I would like to avoid losing my large raw data files if possible.

Thanks again.

---

### Post by tom_kelly2 on 2014-08-21
I did set up the boot repair USB on a windows 7 machine, would that be why msdos is mentioned in the GPT error? Thought I'd downloaded the ubuntu version, that would explain a few things but not the initial spontaneous boot failure.

---

### Post by sotiris2 on 2014-08-21
the msdos mentions in your pastebin don't have anything to do with the version of bootrepair so don't worry. You mention **two** hard drives. Your pastebin output shows one and what must be a usb stick. Did you really have two hard disks? If so do you remember in which you installed ubuntu too?

---

### Post by tom_kelly2 on 2014-08-21
Oh, well spotted, yes it's a usb stick and [COLOR=#000000]35b16da8... is the second mounted drive, the original drive running ubuntu isn't there. So is it a hardware problem?[/COLOR]

---

### Post by grahammechanical on 2014-08-21
This says it all really,

> No OS has been found on this computer.

[COLOR=#666666]===================[/COLOR] Recommended repair
Recommended-Repair

This setting will not act on the MBR.

No change has been performed on your computer.

---

### Post by sotiris2 on 2014-08-21
So you are missing a drive if I undestand correctly. And that drive had your ubuntu installation? That would explain the no OS found on this computer. 
The disk totally missing is a bit suspicious but it may actually mean its less damage than you fear. 

Typically disk that fail can't boot or mount but they do show up. I mean failing disks usually become unreliable and corrupted.They don't just work one day and then disappear. They tend to hang the system during post (some test during boot up. If you get a manufacturers logo when you boot, its going on undercover) but if they are connected they probably do show themselves. 

So I suggest you open the case (with the PC turned OFF) and look at the hard drives. Check that their cables (both data and power) are well connected. Check that the other ends are connected to the motherboard. Maybe plug the drive in a different power cable. And try rebooting. Maybe it works maybe it doesn't but do run boot-repair again to check if the disk appears.

---

### Post by Jonathan Precise on 2014-08-21
> **tom_kelly2 said:**
> ... the original drive running ubuntu isn't there. So is it a hardware problem?

:( Seems like it is. That's why I recommend doing backups. To prevent these types of situations.

There still is a chance though. I've worked with PCs with very weird BIOSes, that all of a sudden detect a non-existing flopy drive, don't detect the HDD or the DVD drive, and worse yet, don't let BIOS upgrades, as they abort with an error "Divide by zero". Maybe your BIOS is going crazy now.

See if you can update your BIOS (using an ISO to burn to disc), and see if it fixes the problem. If it returns an error like mine, then assume it's a faulty BIOS. If it updates and it still doesn't recognize the HDD, assume it's a faulty HDD. If your BIOS is up to date, then assume nothing (buy a new HDD, insert it, and depending if it works or not, it's either a faulty HDD or a faulty BIOS).

---

### Post by Jonathan Precise on 2014-08-21
grahammechanical and sotiris2, +1

---

### Post by sotiris2 on 2014-08-21
Well yes before giving up he can try running the system with the disk connected to a different sata slot on the motherboard, alone (no other hard disk) , resetting bios to default/failsafe etc. 

To OP. Did you never encounter any issues with the hard drive before? Corrupted files? Too slow to open big files ? Maybe with mini lock ups? 

Also the other drive may have some issues, or it may be that the tools are not suitable for disks for LVM and report bad data.

---

### Post by Jonathan Precise on 2014-08-21
I can also add that from time to time I have to clean those PCs inside as they get dusty. That dust piles up and it slowly makes the power supply stop working. That happened to me once, and I had to replace the power supply.

Who knows? It may cause malfunctioning disks in your case too.

---

### Post by Jonathan Precise on 2014-08-21
Oops! This was an automatic duplicate post.

---

### Post by tom_kelly2 on 2014-08-21
The PC is pretty clean, my colleagues built it with fresh parts in April. Only the second hard drive is reused from an old machine. No hard-drive related lockups before that I can recall.

Switching power supply and SATA cables isn't helping much. One drive plugged returns the error the other triggers UEFI settings menu.

So next step, boot from a usb drive and configure mount order? Is it new hard drive time or is there a way to salvage it?

---

### Post by Jonathan Precise on 2014-08-22
> **tom_kelly2 said:**
> The PC is pretty clean, my colleagues built it with fresh parts in April. Only the second hard drive is reused from an old machine. No hard-drive related lockups before that I can recall.

Switching power supply and SATA cables isn't helping much. One drive plugged returns the error the other triggers UEFI settings menu.

So next step, boot from a usb drive and configure mount order? Is it new hard drive time or is there a way to salvage it?

Have you tried upgrading the BIOS firmware? That *might* fix it.

If not, then it's new HDD time

---

### Post by sotiris2 on 2014-08-22
Which drive triggers the uefi menu? Does it say anything or just throws you there? When you say it didn't work you mean the pc just didn't boot? Did you check in live cd if it can see the drive at all now? Does uefi actually list the hard disk? 

Can you try it on another pc (not as boot)?

---

