---
title: "harddrive not recognized"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by dmkinsey on 2013-05-12
I'm really a rookie and I'm trying to install Ubuntu.
The computer is a Dell Dimensions 4550 running Windows XP on one hard drive and an empty second drive.
I wanted to keep the XP and install Ubuntu on the empty drive.

I formatted the drive as EXT4 created a partition and swap space. I installed from the Ubuntu bootable CD that I downloaded. All seemed successful until I rebooted the first time.

On restart, the computer appears to be in DOS mode and the BIOS indicates that no HDD are present. In addition, the DOS screen is totally unresponsive. If I strike any key-nothing. 

I can use the bootable CD to get the machine up but can't re-install because still "no hdd present"
I've tried 4 different harddrives in this computer today and same result with all.
I tried the HDDs from the Dell in my external enclosure and my laptop gives the "new hardware ready" message but the drive(s) do not appear in  "My Computer"

I'm at a loss

---

### Post by taidoka on 2013-05-12
Hi, probably the MBR is screwed.
Try this: [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)
Good luck

---

### Post by oldrocker99 on 2013-05-12
Exactly what he said; I've used that disk more than once to, uh, Rescue A Tux.

---

### Post by dmkinsey on 2013-05-12
So you're thinking this is a coincidence in that the MBR was working yesterday morning and then I installed a new operating system and the MBR died.

---

### Post by Bashing-om on 2013-05-12
dmkinsey;
Nope, not at all.... What likely happened when you (re-)installed is that the grub (GRand Unified Bootloader) installed to the default sda (1st hard drive) rather than to the drive that ubuntu is installed onto (sdb). So when you boot up, bios is looking for the boot code in an invalid position.
Following the given advise, installing grub onto the second hard drive and setting the boot priority to that drive, should resolve your situation.[INDENT=2]
just my thought

[/INDENT]

---

### Post by taidoka on 2013-05-12
Did you formate that partition manually or during the installation process?
Usually MBR gets screwed when you install Windows as a second os. So the explanation of Bashing-om sounds quite valuable.

Edit: I see it's not a partition but a 2nd hdd.

---

### Post by dmkinsey on 2013-05-12
So I used the Rescatux CD and it finds no file system present. And BIOS still can't find any hard disks.

---

### Post by grahammechanical on 2013-05-12
The BIOS should show hard disks even if they are empty and unformatted. What messages do you get as the machine is switched on? Is there a key that you can press to show the Power On System Test (POST) messages? Start at the beginning and tell us everything that you see on the screen from the moment you switch on until the computer appears to go into DOS mode. We need to work out at what stage that is happening. 

If the BIOS cannot find an operating system then it should give a message to the effect. If you have two OS on the machine then you should get a boot loader menu (Grub menu)

Try going into the BIOS and go through all the options to see if there is anything that is preventing the BIOS from recognising hard disks. When you set the BIOS to boot from the DVD drive did you somehow stop it from seeing the hard drives? 

Regards.

---

### Post by dmkinsey on 2013-05-12
Thanks for your advise and for taking the time to respond.
I've made some progress. I think an earlier response indicated that the Ubuntu may have landed in the other hard drive, the one with the Windows XP that I wanted to leave undisturbed. Looks like that is what happened.
Anyway, I shifted my focus to getting one drive working. 
I used the "XP" drive. I set the jumper pin open, the setting for single drive. I plugged it in to the end connector on the cable and re-ran the Rescatux CD.
This time it indicated that the file system was present and had been repaired successfully.
I re-booted with the Ubuntu CD and it found the drive OK
Proceeded to install the new OS by erasing the drive and replacing it all with Ubuntu, and that seemed successful.  Until it came time to re-start the computer to complete the install.
The machine went off as expected but wouldn't come on again. Actually, it froze before it totally shut down.
It remained unresponsive for a while and finally I pulled the power cord.
Repeated the install. Again, went well, successful.
Again problem on the re-start. This time it fully shut down and did re-start but it froze again. This time I'm trying to be patient but it's been frozen for, like, an hour. Nothing happening, unresponsive.

Still, it's progress

---

### Post by dmkinsey on 2013-05-12
WoooHoo, It's up!
I got tired of watching it be frozen and pushed the big power button on the front, held it until it shut down.
Turned it back on, planning to switch the boot order to Hard drive, CD. 
BIOS still whines that Hard disk 1 is not present and it's not but disk 0 is present and pressing 'F1 to continue'
It booted-up Ubuntu and it's on line now.
I'm a little wary about shutting it down now

---

