---
title: "Install freezes at language selection screen"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by *-tread-* on 2008-05-14
Trying to install 8.04 amd64 on a Dell optiplex gx620 (pentium D).  The install flashes the fisrt menu and goes straight to the language selection screen where it freezes.  Neither the arrow keys or function keys do anything. The numlock and caplock don't respond either.

I've tried the sever, desktop, and alternate images.  I've check them with md5sum, burned them multiple times on the slowest speed. Always the same thing.

Suggestions?

---

### Post by papuccino1 on 2008-05-14
Are you sure you downloaded the correct image (32bit, 64bit).

Check, triple check that.

---

### Post by *-tread-* on 2008-05-15
I've tried both the 32 and 64bit versions. In all cases, it freezes at the language selection screen.

---

### Post by balagosa on 2008-05-15
hmmm....have you searched the forums for people who also have the same problem??

i didnt experience this one though.

---

### Post by *-tread-* on 2008-05-15
I've searched hi and low for an answer.  I'm stuck.

---

### Post by cracbah on 2008-05-15
I am having the same problem! I have tried desktop, server and alternate cds. All are booting to the language screen (F2) and no keys will work to do anything. I am dead in the water!

---

### Post by Tatty on 2008-05-15
> ***-tread-* said:**
> I've tried the sever, desktop, and alternate images.  I've check them with md5sum, burned them multiple times on the slowest speed. Always the same thing.

Ok since you have done all that, its unlikely to be the CD. Although you didnt say if you have used the cd integritry checker on the main menu of the cd, it would be worth also checking that if you havent.

The next thing to check would be your hardware.  Its possible that either your RAM or CD drive is faulty, and so the data is getting corrupted during the install process.  -  The last time i had a problem with an install mysteriously locking up it turned out to be the CD drive, as it installed fine when i swapped the drive for another on I had previously done another install with.

Try running the memory test on the main menu of the CD (before installing/booting)

---

### Post by Mhurst1 on 2008-05-15
Make sure you are burning the cd at the lowest speed.

---

### Post by cracbah on 2008-05-15
I cannot check the disk integrity since it jumps right past the menu that should be visible and goes to the language window. I have not verified all the cds but I have booted another machine (not a GX620) with the desktop cd and the live user version came up without a problem.

The GX620 works with Windows XP without any issues (not that I really care that it works with Windows)!

---

### Post by Sordelka on 2008-05-15
How long have you waited at the language selection screen?

It has this ability to appear stuck, but it is actually not...I've waited for 7 hours and it did install :lolflag:

---

### Post by Tatty on 2008-05-15
In that case check the disk integrity on the machine that works :)  Its likely to be correct, but troubleshooting is a process of elimination.

As i say its likely to be a hardware problem.  Booting/instaling an OS is quite a delicate job for a computer to do, and sometimes hardware that has never shown up any problems before suddenly turn out to be slightly faulty.  Even one slight bit gone wrong can bring it all down.

You just need to start systematically checking each bit of hardware - RAM and CD are the most likely to be causing you problems.

Try swapping your CD drive for the one in your working machine.

---

### Post by cracbah on 2008-05-15
I have 2 cd rom drives in the machine and have tried both of them! No difference on all 3 cds (desktop, server and alternate).

I was hoping there was some bios parameter that needed to be tweaked to get it to boot properly. I cannot find anything other than someone changing their ATA drives from normal to raid in the bios. I will try that tomorrow at work.

---

### Post by Tatty on 2008-05-15
> **cracbah said:**
> I was hoping there was some bios parameter that needed to be tweaked to get it to boot properly. I cannot find anything other than someone changing their ATA drives from normal to raid in the bios. I will try that tomorrow at work.

Its unlikely to be that if it freezes at the language selection screen... as it will not be using the hard drive yet.

If its not the CD drives then it could be ram, test that.

---

### Post by skeltoac on 2008-08-29
Same problem here: numlock is frozen and the normal 30-second countdown is not present at the language screen. Waiting 12 hours had no effect. The same server CD worked in another system (D600). A desktop CD works in the GX620.

I have flipped several options in the BIOS but nothing has worked. I'll keep trying things.

---

### Post by Gatesisanidiot on 2008-09-11
I too have this problem.  The CD starts to run, I get to the language screen and it freezes.  The function keys don't work.  I made some changes in the BIOS, mostly disabling features to slow the computer down and that was when I saw the opening screen with the UBUNTU logo and the menu for the first time.  Still I could not make a choice from the menu and the function keys didn't work.  

I'm trying to install 8.04.1 i386 server.  I just updated the Award BIOS on the computer (Compaq).  The Boot procedure says the memory (512 mg) is fine.  

I downloaded the Ubuntu file and the hash number confirmed it was good.  Considering the suggestions on this thread it looks like my choices are either burning another CD ( I tried setting InfraRecorder at 2x but it ran off and burned the disc at a much faster rate) or swapping out the CD-ROM.

---

### Post by Gatesisanidiot on 2008-09-11
I found my problem.  I was using a PS2 keyboard, connected through the appropriate adapter into the USB port.  When this machine was running Windows, no problem.  But, the UBUNTU loader did not like it.  I unplugged the keyboard, plugged it into the PS2 port and tried booting the system again.  

The machine just finished partitioning the HDD and it looks like I'm on my way to Windowless heaven.

---

