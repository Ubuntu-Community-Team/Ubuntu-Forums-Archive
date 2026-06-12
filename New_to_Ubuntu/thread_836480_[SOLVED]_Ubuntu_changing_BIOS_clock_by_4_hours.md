---
title: "[SOLVED] Ubuntu changing BIOS clock by 4 hours"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Shobuz99 on 2008-06-21
I'm new to Ubuntu and Linux, so maybe that's the reason I don't understand how Ubuntu seems to be changing the CMOS/BIOS settings of my clock, after bootup.
I'm using version 8.04.
I have setup a dual boot situation using the /boot/grub/menu.lst to boot between Ubuntu and Windows XP. 
The Ubuntu drive is set as slave, and the NTFS drive (Windows) is set as master. 
This works flawlessly; except for the clock time. 
If I choose to boot from Windows, at cold start up, the clock time is correct in the BIOS. 
If I decide to boot to Ubuntu, the clock time displayed, is correct in Ubuntu.
When I restart the machine and select Windows after being in Ubuntu, the clock in the BIOS is now exactly 4 hours ahead of the time it's supposed to be. 
I must reset it in the BIOS prior to booting Windows, again. 
I've checked time settings in Ubuntu and selected servers and the correct time zone for where I am (Eastern, USA). 
I have searched some tech forums on the topic, but haven't yet found my problem showing up for someone else.
Can anyone shed some light on this for me?
I would be happy to post whatever files from Ubuntu or Windows XP that I need to for review by this group's members.
Please help.
Rick (Shobuz99)

---

### Post by Sarah L on 2008-06-21
A quick fix would be to select a timezone that is four hours behind your actual timezone in Ubuntu. This should at least get your system clocks synchronized.

You might instead want to click on the clock in the corner and select Automatically Update From the Web and see if that fixes the problem. The web updates have always managed to sync my Ubuntu clock with my Windows clock correctly.

---

### Post by imon9 on 2008-06-21
this is because both windows and ubuntu update the time with the internet time server...

so the bios got reset twice

to avoid this, go to "system" > administration > time and date setting >

undet the option "configuration" , change it to "manual" instead of "keep synchronized with internet server"

that should fix your problem ;)

---

### Post by Shobuz99 on 2008-06-21
Thanks Sarah, but it doesn't solve my problem. 
The time zones are correct in **both Windows and Ubuntu**, if I check their settings once I'm booted to them. 
The problem is Ubuntu seems to be changing the BIOS. 
I only have one BIOS in my computer. 
BIOS is where all OS's get the time from or where they have access to the time.
I have already tried the automatic update from the web...
that is, if it's set in the Time and Date setting of the System/Administration section that I have been using to set the Time Zone, configuration, and Time Servers selection...is that the correct place?
Setting the Time Zone 4 hours back, in Ubuntu or windows will just make matters worse; since the BIOS is what controls the clock.
besides, I said in my post that teh Ubuntu clock is correctly showing teh time..it's the Windows clock that CHANGES when I come back to it from Ubuntu. 
If I never boot to Ubuntu, the Windows clock is ALWAYS correct..
I do appreciate your suggestions, though.
Rick (Shobuz99)

> **Sarah L said:**
> A quick fix would be to select a timezone that is four hours behind your actual timezone in Ubuntu. This should at least get your system clocks synchronized.

You might instead want to click on the clock in the corner and select Automatically Update From the Web and see if that fixes the problem. The web updates have always managed to sync my Ubuntu clock with my Windows clock correctly.

---

### Post by Shobuz99 on 2008-06-21
> **imon9 said:**
> this is because both windows and ubuntu update the time with the internet time server...

so the bios got reset twice

to avoid this, go to "system" > administration > time and date setting >

undet the option "configuration" , change it to "manual" instead of "keep synchronized with internet server"

that should fix your problem ;)

thanks imon9, I will try that right now.
Rick (shobuz99)

---

### Post by Shobuz99 on 2008-06-21
imon9

Nope. Didn't work. Here's what i did:
I made the change you suggested. 
Then Restarted/rebooted.
When the BIOS screen came up, I went into the BIOS
and selected "Standard CMOS Settings".
Looked at the clock and it was 4 hours ahead of EDT.
I adjusted the BIOS settings to the correct time.
I then saved those settings.
I then rebooted and selected Ubuntu, again. NOT Windows.
Once I got to the Ubuntu screen and looked at the clock,
I saw it was the correct time/time zone.
I double checked the settings you told me to change.
It was set to Manual, like you said.
I then rebooted and looked at the BIOS settings again.
They were changed to 4 hours ahead, again!!
Why is Ubuntu changing the BIOS exactly 4 hours ahead?
It doesn't make sense to me. Especially since the clock
time IS correct while I'm in Ubuntu viewing the time date
at the top...
Rick (shobuz99)

---

### Post by Jeff250 on 2008-06-21
Unix operating systems set the system clock to be universal time.  Windows operating systems set the system clock to be local time.  (This is why Windows has to adjust the system clock for daylight savings transitions, which can be problematic, say if you are dual-booting two Windows OS's, because then you will be adjusted twice!)  To get Linux to set the system clock to a time that Windows can handle, try the following:

Open /etc/default/rcS in a text editor with root privileges.  Find the line that says 'UTC=yes' and change it to 'UTC=no'.  Then reboot.  I've never tried this personally, so let me know how it works.

---

### Post by louieb on 2008-06-21
The clock switching time when alternating boots between XP and Linux is a pain. To keep Linux from using UTC Right click on the clock > Preferences > uncheck the UTC box. Or if you don't have the clock edit **/etc/default/rcS** and change the line **UTC=yes to UTC=no**
If you need to change the timezone this can be done by runing sudo tzselect

---

### Post by imon9 on 2008-06-21
with the same setting, 
you should reboot and change the bios time again and go into ubuntu.

it probably becoz the time change once u login (before the setting came into effect)

try and let me know

---

### Post by Shobuz99 on 2008-06-21
Thanks. That sounds like what I should do.
I tried the command sudo tzselect and selected the correct time zone
(It was already correct).
While I did that, I noticed that the UTC time IS exactly 4 hours ahead.
So using /etc/default/rcS will solve my problem.....however,
Beginner question: How do I log into root?
I get permission denied when I try to change the UTC time
using /etc/default/rcS in terminal mode.
Rick (shobuz99)

> **louieb said:**
> The clock switching time when alternating boots between XP and Linux is a pain. To keep Linux from using UTC Right click on the clock > Preferences > uncheck the UTC box. Or if you don't have the clock edit **/etc/default/rcS** and change the line **UTC=yes to UTC=no**
If you need to change the timezone this can be done by running sudo tzselect

---

### Post by Sarah L on 2008-06-21
gksu gedit /etc/default/rcS

---

### Post by Otto-C on 2008-06-21
Take a look at this blog post.

[http://burnz.wordpress.com/2008/06/20/fix-date-and-time-in-ubuntu/](http://burnz.wordpress.com/2008/06/20/fix-date-and-time-in-ubuntu/)

hth
otto-c

---

### Post by Shobuz99 on 2008-06-21
> **Sarah L said:**
> gksu gedit /etc/default/rcS
thank you Sarah L! That worked.
I went in and changed the UTC=yes to UTC=no.
I restarted and when BIOS came up, I went in and looked at
the clock. The settings were still correct.
Now all I have to do is restart one more time to see if it 'sticks';
which i think it will, and then boot to windows and back to be sure.
(kind of anal, I know :redface:):lolflag:
Thank you again for your help, and everyone else here as well.
I'm learning...:-k
Mark this problem SOLVED!
Rick (shobuz99)

---

