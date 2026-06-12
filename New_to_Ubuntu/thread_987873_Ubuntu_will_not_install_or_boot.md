---
title: "Ubuntu will not install or boot"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by eezip on 2008-11-20
Hi everyone, I am new to Linux but I want to give it a try so I tried to install 8.10. I downloaded both 32-bit and 64-bit ISOs and burned them to disc using ImgBurn. I am using all the hardware of my main Windows computer in my signature except the hard drive. Then:
1. Shutdown, unplugged Windows drive, plugged in old Seagate 7200.7 80GB. Restarted with 64-bit disc in drive.
2. I get to the Ubuntu screen. I check CD integrity - all good.
3. If I go to either Install or Try Ubuntu, the orange bar bounces back and forth a bit, moves left to right once, the screen blinks, the cursor blinks for a few seconds in the upper left hand corner, and then the screen goes blank. After about 30 seconds I hear the DVD drive spin up briefly and then quiet down. And then nothing. After about 5 minutes of no activity I give up and shut it down.
4. I swapped to my WD SE16 640GB drive but can't Install or Try Ubuntu either - the exact same series of events happens.
5. I pop in the 32-bit disc, also with the exact same result.
6. I moved the drive from SATA4 to SATA3 port (where the Windows drive had been). Same result.

I can install Windows XP and Vista onto either the Seagate or WD drive when they're plugged into SATA4 port. I can't figure out what could possibly be wrong. All the hardware seems good, the disc appears to be fine, I get to the splash screen but nothing else.

So, I took the 7200.7 80GB drive and the 64-bit disc to work. I plugged the HDD into a computer at work and popped in Ubuntu. It installed like a champ and was running just fine. So, it's definitely something in my hardware setup. I plug the HDD in to every single SATA port and I have the same sequence as before - the orange bar bounces back and forth, loads left to right once, then the screen blinks, I see a cursor for a moment, and then it's all black. This one is baffling me!

The only thing I can think of is that the computer at work had the HDD connected the SATA0. My board starts with SATA3. Could that possibly have anything to do with it if the drive is apparently seen when booting (I get the Ubuntu splash screen with the HDD plugged in but Ubuntu doesn't boot)??

So, I tried the Ubuntu 8.10 alternate install. It went all the way through, so I thought I might have a winner. But, no dice. The same thing as before: orange bar bounces around, sweeps from left to right once, the cursor blinks, and then the screen blinks and that's all she wrote.

GRUB was reporting a USB enumeration problem, but I couldn't read the message. So I went into BIOS and turned off all hardware and features and then unplugged all USB devices (I don't have any cards in the board other than graphics) that I didn't absolutely need to run the PC. Same result.

I upgraded the BIOS from v1.8 to v1.9 and tried to start with the default values. Nope.

I wondered if setting the ATA devices option in the BIOS would make any difference (manual v1.2 page 51, but that is for an older BIOS version). Right now I have it set to 'SATA' but maybe it should be 'AHCI'? I believe AHCI causes more problems than it is worth, but who knows - apparently the latest Linux kernal has intrinsic support. I switched the RAID setting from IDE to AHCI (the other option is RAID, which I don't want). Nothing.

I pulled out one pair of RAM, so I was down to 1GB + 1GB, and that didn't help either. The exact same results.

If it is just this board, what are some options for good motherboards that will work in Ubuntu 8.10 with all the rest of my hardware? The P45/ICH10R Asus boards look good and the Asus boards I've had always ran well.

MSI P35 Neo2-FR | Core 2 Duo E8400 | MSI GeForce 9600GT 512MB | 4x 1GB DDR2-800: G.Skill + Corsair | WD 640GB WD6400AAKS, Samsung 1TB HE103UJ | Lite-On LH-20A1S | 2x Samsung 206BW | Yamaha RP-U100, B&W LM-1 | XP Pro x86 SP3, Vista Ultimate SP1 x86

---

### Post by Crafty Kisses on 2008-11-20
First, make sure you don't have the server edition. Then when you're at the black screen, try running the following command:
```
startx
```
See if you get any errors.

---

### Post by caljohnsmith on 2008-11-20
When you boot the Ubuntu Live CD and get the first menu, press "F6" for "other options", and although I don't remember exactly the choices you have after that, the bottom line is you want to try adding "acpi=off" to your kernel boot line. See if that helps, and sorry I can't be more specific about the exact steps (been a while since I did that procedure). Let me know if that allows you to boot into Ubuntu.

---

### Post by eezip on 2008-11-28
Thanks to both of you for your replies!

Codename,

I don't have the server edition. Where do I go to type 'startx'? I am at a blank screen with no cursor or prompt and the computer isn't responding to any inputs. :(

caljohn,

I booted into Recovery Mode and ran through fsck, dpkg, and xfix without any resolution. I got into where I thought I could edit the boot commands, but I wasn't able to enter 'acpi=off' after I added a new line. Of course, this was with the Seagate HDD that has an installation. I will try the Live CD on another HDD now and see if that gets me anywhere.

---

