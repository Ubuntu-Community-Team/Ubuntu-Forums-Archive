---
title: "Nomodeset problem"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by thehim on 2013-04-08
Hi, I just setup a updated rig.
AMD A4-3400 on ASrock A75m-HSV
8Gb ram.

I tried the whole day fixing this problem but was in vain, so here goes.

I couldn't install Lubuntu at first, so I tried using nomodeset to get to 'Try Lubuntu without Installing' and install from there, it was a success.
However on first boot, I was met with a blinking cursor, and nothing happens.

I tried getting into the grub, by holding Shift or F12 from Bios POST, but was in vain.
All leads to the blinking Cursor.

I'm already tired out, I'll check this thread the next thing I wake up later on.

Previously, I was on the same rig, but A6-3500 on Biostar TA75m+,
The board went down, and I got the ASrock , in the midst of fixing, I bent the pins of the A6, and settled for A4.
The previous build on was all well until HDMI port went crazy, only VGA was working, but it defeats its purposes as an HTPC.

There are ways that state that I need to change the quiet splash on grub to nomodeset, and install ATI drivers, but I just can't get to GRUB.
Another way was to install Lubuntu without an internet connection, so no updates would be installed, that failed for me too.

---

### Post by deadflowr on 2013-04-08
When you get the blinking cursor, can you get to tty1-6 by using ctrl+alt+F1, or 2 ,or 3, so on?
If so from there you should be able to login and edit the file using CLI tools.

---

### Post by thehim on 2013-04-08
I just rebooted the system, my monitor registers nothing.
There is the Bios POST, a short BEEP only.
I'm quite flustered and frustrated now :(

---

### Post by thehim on 2013-04-09
It appears problem lies with my RAM and primary HDD, cleaned the contacts changed HDD, and it worked.
Now I've got a seperate issue, this setup works fine on VGA, but nothing on HDMI.

I'm connecting this setup (HDMI) Denon AVR-1312 (HDMI) TV.
Denon's settings are factory.
I installed ati properiatary drivers but it's nothing.

---

### Post by thehim on 2013-04-09
As per 3 hours ago.
The setup is ok if I plug only the VGA.
If I reboot with HDMI only, nothing is projected.

Using AMD proprietary drivers, instead of Xorg Xserver drivers.
As using the latter, I find no ways of setting up anything,
With the AMD drivers, at least there's the AMD Catalyst window to play around.

I just tried again on reconnecting both VGA and HDMI cables and resetting.
my Denon AVR doesn't show up in AMD Catalyst Window

Even If I used the HDMI straight from TV to PC, nothing happen.

---

### Post by Locus Kiesselbachi on 2013-04-09
> **thehim said:**
> ... but I just can't get to GRUB...


When you hear POST "beep", before and a little after that, press "left Shift" like a mad man. :)
It should take you to GRUB menu.

sometimes it needs holding down Shift.

...but!
I have one old rig, it has USB and old-school (purple) keyboard connection in mainboard and I discovered that to get GRUB I need to use **that** old keyboard connection with an old keyboard (which collected dust somewhere). I dont know if that is the case with you.

Good luck and dont give up!
I installed my Lubuntu about a week, lot of hassle. It is like a sudoku or some puzzle, that after resolving, it feels good.

---

### Post by thehim on 2013-04-14
Moderators could please help me close the thread.
I installed Windows first, and dual booted with Lubuntu 12.04, 
The way to make it work.

As for HDMI, I tried with several different HDMI cables, and finally found 1 that work.
It's quite a hassle though.

---

