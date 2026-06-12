---
title: "Booting problem"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by tiawulf on 2012-12-05
I finished building my first pc today, i'm still very new to working with hardware but i managed to get everything working together without setting anything on fire. I tried installing 11.10 to it and everything seemed to work fine, no error messages or anything of the sort, but when i restarted it, there was only the CD drive option available in the boot menu. I'm very new and have no idea where to start in term of fixing this, can someone help me please?

---

### Post by StinkySQL on 2012-12-05
I know that the people who are about to come along and solve this for you are going to ask:
1) How did you install? Was it a CD that prompted you for installation as an option? A new install from a distribution? Etc.
2) Is it just Gnu/Linux? That is, is this intended to be a dual-boot,etc.
3) Some information about your hardware might also help.

This will help them get you a better answer quicker.

---

### Post by FormatSeize on 2012-12-05
It's difficult to discern what you are talking about. What do you mean when you say boot menu? Also, have you set up the computer to boot from something other than the CD drive?

---

### Post by boogerama on 2012-12-05
I hope I'm not over simplifying things but did you remove the CD/DVD from the drive? :)

---

### Post by tiawulf on 2012-12-05
> **StinkySQL said:**
> I know that the people who are about to come along and solve this for you are going to ask:
1) How did you install? Was it a CD that prompted you for installation as an option? A new install from a distribution? Etc.
2) Is it just Gnu/Linux? That is, is this intended to be a dual-boot,etc.
3) Some information about your hardware might also help.

This will help them get you a better answer quicker.
right then, let's see
i installed from a live CD, 11.10. I do not intend to dual boot. the hardware is from a barebones kit from tiger direct, more specificaly: MSI 760GM - P23 (FX) AMD series socket AM3 MB, AMD athlon II X3 445 3.1GHz OEM CPU, seagate barracuda st1000dm003 1TB 7200 RPM 64MB cache SATA 6.0GB/s hard drive -bare drive.
I'm new to working inside computers and as I said before I just finished building it today, I've done nothing to it other than trying to install ubuntu 11.10

---

### Post by tiawulf on 2012-12-05
> **FormatSeize said:**
> It's difficult to discern what you are talking about. What do you mean when you say boot menu? Also, have you set up the computer to boot from something other than the CD drive?

that's exactly what i'm talking about, when selecting a device to boot from, the hard drive is not there.

also, yes i did take the live cd out, and when i do that it tell me that there's no valid drive to boot from.

---

### Post by tiawulf on 2012-12-06
I realize this is probably not an ubuntu problem, but I'm looking for an ubuntu solution, mainly because i cant afford windows. When I tried to format the hard drive to certain formats using gparted or disk utility, it would give me an error "deamon is inhibited" Also, I'm not sure if i need to mount the drive for it to be bootable (though through my software experience it seems like i would need to) and i get the same deamon error when i try to mount it.

---

### Post by arpanaut on 2012-12-06
Boot up the live cd and choose the "Try" option, this will give you a live session.
When you are at the Desktop press ctrl+alt+t this will get you to a terminal window.
Now copy and paste this ```
sudo fdisk -lu
``` into the terminal window, then copy and paste the result of this command into your post here.

That will show us how the system is seeing your HDD, if at all.

---

### Post by tiawulf on 2012-12-07
for the sake of updating: I can no longer boot from disk either. when my pc enters it's boot selection screen, it imediantly comes up with an X64 exception error 000000000003!! I dont know the exact number of 0's. there are half a dozen other lines that all give miscelanious abreviations and values but I dont know what any of them mean. this first happened when the head IT at my work suggested that I make sure my HDD was plugged into SATA1 or 0, which I had. It was not and when I switched it out to 1 and started it up, this exception started coming up and has every boot atempt since.

---

### Post by oldfred on 2012-12-08
It really should not matter which SATA port. BIOS should show drives.

Some with ASrock boards have something called ASmedia ports that have caused issues. And some have had issues with the newer SATA3 6GB/sec ports. Better to check and use standard SATA2 3GB/sec ports if you are not.

---

### Post by Bartender on 2012-12-08
> **oldfred said:**
> It really should not matter which SATA port. BIOS should show drives.

In most cases this is probably true.  However, we're running an HP dc7800 at home.  It's a hand-me-down from the IT dept. at work.  The dc7800 is a "corporate" model.  The manual clearly states that it will not boot from any SATA port but the first two.

A couple of years ago I built a PC for my Dad.  My first experience with an UEFI motherboard.  There was a different controller on the motherboard for the "first" SATA ports than the second bunch.  Every time we started it, the PC would boot, but not before announcing that it couldn't find any bootable devices on the secondary SATA ports.  I had to go back into UEFI and turn OFF the second SATA controller as a boot device.  

It's probably a long shot, but maybe the OP should check to see if he has more than one SATA controller, and if either one of them is disabled in the Boot Devices menu?

Another thing to try, just as part of the trouble-shooting process, is unplug all HDD's from the motherboard and see if the "x64" error goes away.

Try plugging in a blank SATA HDD to SATA 0 or 1.  Boot, see what happens.

Who knows?  Maybe the SATA controller is toast, or the HDD, and it has nothing to do with software.

The OP's comment that BIOS doesn't see the HDD at all is a show-stopper right there.  Gotta figure out why that is.  Bad or loose cable?  Power supply problem?  Bad HDD?  Until the BIOS sees the HDD you're not goin' anywhere...

The OP has never tried to build a PC before.  That adds several possibilities right there.  Have you checked to make sure that all power connections are snug to the motherboard?  Do you hear the HDD spin up when you first turn it on?  Is the RAM firmly seated in the correct slots?  Etc. etc.

Nobody wants this to happen, expecially on your first build, but the power supply, motherboard, RAM, or HDD could be gunny-sack right out of the box.  Some things are easy enough.  Power supply is easy to swap out if you have a spare, or you have a really good friend who's willing to take that kind of chance with their parts.  RAM can be checked with a memtest CD.  HDD?  Probably the most straightforward thing to do is plug it into someone else's PC and see if their BIOS fails to see it.  If it doesn't show up in someone else's rig, then you've got about 100% certainty that the HDD's bad...

---

### Post by tiawulf on 2012-12-10
the first SATA port worked. I took it apart friday night and put it back together from the beginning and the X64 exception went away and it booted right up from the HDD. Thanks for all the advice and help everyone.

---

