---
title: "installation on new hard drive.  No prior OS"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by john18 on 2012-11-03
I just built a new computer to dedicate to linux and Umbutu in particular.  This computer consists of all new components that have never see another operating system.  I have changed the bios to look to the optical (dvd) drive first.  When I start the computer and put in an installation disk I only get to is the "What language" and the "try Umbutu or install Umbutu" screens.  There after my screen goes black.  This is with an installation disk that came in the back of an Umbutu book.  On an installation disk I made myself, it goes black right after the "what language" screen.  Note that Umbutu installed fine using this disk on a machine that already had windows installed.  Can anyone help me with this?  A friend suggests that a "Master boot record" (what is this?) or lack thereof may be the problem.  Does this seem right?  Thanks.  Any help on this will be appreciated.

---

### Post by newb85 on 2012-11-03
First, welcome!

Second, it's *Ubuntu*, not Umbutu.

Your friend is probably thinking of the difference between MBR and UEFI.  This is only an issue if you're setting the machine up dual-boot, and it wouldn't cause problems until after you had installed both systems.  Definitely not true in your case.

More likely it's a graphics card issue.  (Not that you have a bad card, it just might not be supported in the default mode.)  Since it's a custom built machine, I assume you could provide details about the graphics card...

---

### Post by john18 on 2012-11-03
Thanks newb85.  The graphics are integrated into the motherboard which is called ASRock Z77 Pro 4.  CPU is Intel core I5-3570K.  These seem to be fairly common items for a middle range PC.  Sorry about the spelling.  Will try not to let it happen again.

John

---

### Post by john18 on 2012-11-03
Thanks newb85.  The graphics are integrated into the motherboard which is called ASRock Z77 Pro 4.  CPU is Intel core I5-3570K.  These seem to be fairly common items for a middle range PC.  Sorry about the spelling.  Will try not to let it happen again.  The specs for the mother board go on at length about all the wonderful things it can do in graphics.  It should run for president.  Is there anything in particular i should look for?  Also interesting that you should mention UEFI.  I just saw it for the first time today while trying assign boot priority in bios.  Appears to be a graphical way around bios,  Kinda neat. 

John

---

### Post by newb85 on 2012-11-03
Well, unfortunately, I can't deduce from that which boot option to go with, so unless someone with more experience wants to jump in, we'll have to try a couple options and see if one works.

To access boot options for a Live CD: after the splash screen with a manufacturer logo (probably for your motherboard), small images of a keyboard and a stick-figure man should appear.  Hit the space bar.  That should bring up a boot options screen, and the language selector should come up.  With the right language selected, hit enter.  Hit F6 for a list of some boot options.  As a first try, let's go with nomodeset.  Select it and hit enter.  Then, select "Try Ubuntu without Installing" and hit enter.  See if that will bring up the live session.

If that doesn't work, my next guess would be xforcevesa, but as you probably won't see that in the list when you hit F6, we'll have to alter the steps slightly to try that.

Edit: by the way, if you want to know more about UEFI, a good resource is [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

---

### Post by oldfred on 2012-11-03
Did you download the 64bit version? That is all you should have.

With the 64bit verison the UEFI menu should give you two options on booting, one UEFI/efi and the other BIOS/AHCI/legacy or whatever. Which ever way you boot installer is the way it will install.

UEFI is the new way, BIOS/MBR is the old way. You can also do a mixed gpt with BIOS also.

If only Ubuntu I would install with UEFI & gpt partitioning.

I prefer to partition in advance. Gparted defaults to MBR(msdos), so you have to change to gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

The efi partition must be the first partition and formated FAT32. IF UEFI you do not need a bios_grub partition.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Someone also posted this on Asrock:

> AsRock calls BIOS mode AHCI.
"Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard
Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.


---

### Post by john18 on 2012-11-10
Thanks for the help and references to further my understanding of the ubuntu installation process.  Here is what I did in response to your advice.  I down loaded the 64 bit version of ubuntu (I only just now found the “secure remix” version that includes Boot-repair-will try later).   I believe I created the disk correctly because I was able to use it to Install a live version of Ubuntu on two different windows computers.  Getting back to installing on my new, never before used, computer, I was able to get to the keyboard/stick figure screen and then to the language screen.  From choices along bottom I selected F6. On the dialog that followed, I stepped down to “nomodeset” and pressed enter which put an “X” in its check box .  This did not close this dialog.  I had to hit esc to do that.  With the dialog closed, I was now able to select the top item “Try Ubuntu” which I did by highlighting it and pressing enter.  After some seconds of blackness, the screen filled with lines of text.  After about 30 more seconds another screen full of text appeared and remained for several minutes until I turned off the computer.  The last line of the second screen read: “34.1632661  ata8:  hard resetting link”.  Recall that before selecting “nomodeset” I just got a black screen so this is progress.  Can you suggest anything else I might try in order to complete this installation.

---

### Post by grahammechanical on 2012-11-10
You could try some of the other F6 options along with nomodeset.

What you did was correct and what you saw was correct up to a point and that point was reached when the session did nothing for several minutes.

The last message, in my opinion, was in response to you turning off the computer. That was a hard reset. It is the earlier messages that might be of interest.

The session tries to determine the video mode of the monitor. Failure to correctly determine the mode causes the black screen. The nomodeset option tells it not to try to find and set a video mode. That often gets us to a live desktop and or the first install screen if we choose to install.

Regards.

---

### Post by oldfred on 2012-11-10
Is hard drive in port 0 or 1 and not A1 or A0?

Some need other settings. Are you using the Intel video or do you have another video card. Sometimes you have to change settings in BIOS/UEFI for video mode.

Intel should not need nomodeset but might need one of these:
i915.modeset=1 or i915.modeset=0 
newer: 
 i915.i915_enable_rc6=1

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sidzen on 2012-11-11
[http://openbenchmarking.org/s/ASRock%20Z77%20Pro4-M]("http://openbenchmarking.org/s/ASRock%20Z77%20Pro4-M") refers to some OpenGL drivers, kernels and ubuntu versions that apparently work together on your mobo.

---

### Post by squakie on 2012-11-11
+1 on what OldFred has said - the Intel boards and IGP's often need the i915.x settings.  In addition, some seem to require either ACPI=off or NOAPIC to get around that.  It may even be necessary to specify one the VGA= options just to boot into GUI.  After you get it to actually let you install, check Additional Drivers to see if there is a recommended driver for your IGP.

I would think at this point it could be either the video or the disk, both as OldFred has suggested.  I'm not sure at which point in the boot process it starts looking at the drives, but I suppose that might do it.  I would be leaning more to an IGP option myself, but I don't have the experience someone like OldFred does.

It would also help if you could someone get a picture of the text you get on your screen, or at least copy it down and post back with the last 10 lines of it or so to see if we can get anything to go on from those messages.

---

### Post by john18 on 2012-11-11
Thanks one and all.  oldfred's recommendation to change hard drive port did the trick.

John

---

