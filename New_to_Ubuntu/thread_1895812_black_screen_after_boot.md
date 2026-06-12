---
title: "black screen after boot"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by lile001 on 2011-12-15
I am experiencing a rather severe problem - Screen is black after boot.  

I am running Ubuntu 11.04 on a Dell T3400.  Although working fine all morning, Operating system was acting strange just before this happened:

1.  It started insisting that my thumbdrive was a read-only file system.  I was in the middle of using GKSU Nautlius to change permissions of the thumb drive when things started to go haywire.  The program would not let me change permissions, although I was logged in as root.  I closed nautlius, and closed terminal.  Terminal complained that there was still a process running, which was not true.  

2.  After that, all of the Icons on the screen had a big X through them, like they could not be found.  This happened in the panel at the top of the screen, which has some shortcuts.  None of them appeared with normal graphics. 

3. I tried to shut down normally, turned off all the programs and turn off the computer using the screen menu.  This was unsuccessful.  Computer remained on. 

4. I hit BOB, the Big Off Button.  Computer shut off. 

5.  When I rebooted, the computer wanted to check its hard drives, which I allowed it to do.  A few minutes later, the screen remained blank.  I waited a while longer, but there was no activity on the screen.  A mouse would create an odd-looking cursor I had never seen before, keyboard activity had no effect.  Screen is black.   Eventually I gave up and hit BOB again. 

6. On boot, using our old friend BOB, I see a normal list of operating system choices, the Ubuntu 11.04 logo that I normally see on boot, then a pop comes out of the speakers, and the screens go blank.  No mouse-wiggling or keyboard tapping wakes up any activity.  Hitting BOB again, I see a normal shutdown sequence on the screen, "Deconfiguring network interfaces... " and some other gibberish then the machine turns off.  

10 Tried a recovery mode operating system, same result, when I chose to use low-graphics operating system (I got that far at least.)  Black screen after boot.  

11. Just tried "reboot into file system check" which still seems to be thinking about something..

I am pretty much at sea here, and I need to get this machine running for my business.  How should I start?  What is happening?  How do I go about fixing it?

---

### Post by bluexrider on 2011-12-15
you need to be able to boot from a live CD 

```
sudo shoot-bob
```just kidding about BOB

---

### Post by lile001 on 2011-12-15
File System check returned the following:

/dev/sda5: clean, 
init: ureadahead-other main process (752) teminated with Status 4

/dev/sdb6: recovering journal
init: udev-fallback-graphics main process (796) terminated with status 1
/dev/sbd6: clean, 
skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

[OK]

init: dbus main process (933) killed by TERM signal
init: disconnected from system bus
[45.129345] Restarting system.

There it hangs.  At least there is something on the screen. I don't have any idea what any of this means.   

I have been using Ubuntu for maybe 1-2 years, but really am not very sophisticated.  Start slow and simple if you can!

---

### Post by lile001 on 2011-12-15
> **bluexrider said:**
> you need to be able to boot from a live CD 

```
sudo shoot-bob
```just kidding about BOB

The computer responds with:

Error 7849: BOB is wearing bulletproof vest.  Delete BOB? [Y/n]

What should I do?  

Meanwhile, all kidding about BOB aside, I am making a bootable thumb drive live CD.  Cross your fingers and pray to BOB.

---

### Post by bluexrider on 2011-12-15
> **lile001 said:**
> The computer responds with:

Error 7849: BOB is wearing bulletproof vest.  Delete BOB? [Y/n]

What should I do?  

Meanwhile, all kidding about BOB aside, I am making a bootable thumb drive live CD.  Cross your fingers and pray to BOB.

Meanwhile back at the ranch. If you get anywhere with booting this live. Back up your data as too not loose it. 

This may turn nasty and you need to be prepared.

---

### Post by jockyburns on 2011-12-15
I had a very similar problem a few months ago. Graphics card had given up the ghost so I thought I could use the onboard graphics instead. G/F had used BOB to shut the computer down. When I got home from work I took out the PCIe graphics card booted to bios and set the graphics to onboard. When it started to load Ubuntu, I got a text based screen asking if I wanted to go to recovery mode, selected yes and about 10 mins or so later got a message similar to yours where it said restarting system etc. Only for it to boot to the text based screen again, and still asking to do the recovery thing again. Tried unsuccessfully to start my computer before using an ISO on a usb stick. Backed up all important things then re-installed 11,04 as a clean install. So far no problems. ;);)

---

### Post by bluexrider on 2011-12-15
> **jockyburns said:**
> I had a very similar problem a few months ago. Graphics card had given up the ghost so I thought I could use the onboard graphics instead. G/F had used BOB to shut the computer down. When I got home from work I took out the PCIe graphics card booted to bios and set the graphics to onboard. When it started to load Ubuntu, I got a text based screen asking if I wanted to go to recovery mode, selected yes and about 10 mins or so later got a message similar to yours where it said restarting system etc. Only for it to boot to the text based screen again, and still asking to do the recovery thing again. Tried unsuccessfully to start my computer before using an ISO on a usb stick. Backed up all important things then re-installed 11,04 as a clean install. So far no problems. ;);)

I have a suspicion because what the OP said about "it was working fine then he was in the middle of something" like as a hardware failure.

---

### Post by anewguy on 2011-12-15
That and the POP! have me leaning towards the same idea.  Hopefully that pop wasn't a capacitor on the motherboard.

Dave ;)

---

### Post by bluexrider on 2011-12-15
> **anewguy said:**
> That and the POP! have me leaning towards the same idea.  Hopefully that pop wasn't a capacitor on the motherboard.

Dave ;)
The POP came out of the speakers! However may have shorted something....sniff....sniff....whats burning?

---

### Post by lile001 on 2011-12-15
OK, was finally able to boot from live CD into Ubuntu 11.10.  Backing everything up to another computer, and then to an external hard drive.  I am experiencing wierd problems - such as, when copying, Linux complains about a filename too long.  I didn't need that whole folder, so I deleted it, but Linux still complains that the file is there and name is too long.    

Once this stuff has all been backed up twice, how shall we proceed?  

(poor BOB.  Had to shoot him again.)

---

### Post by lile001 on 2011-12-15
Hardware failure?  Hmm.  Under live CD, screen is working OK.  THat seems to rule it out. No?  

I have dual monitors, if that makes any diff.  Don't ask me what hardware it is, I don't know.  Live CD is treating them both as one monitor.  Maybe has something to do with that?

---

### Post by lile001 on 2011-12-15
> **lile001 said:**
> Hardware failure?  Hmm.  Under live CD, screen is working OK.  THat seems to rule it out. No?  

I have dual monitors, if that makes any diff.  Don't ask me what hardware it is, I don't know.  Live CD is treating them both as one monitor.  Maybe has something to do with that?


DUal monitors now working under Live CD.  Looks less and less like hardware failure.  Could OS have just become hosed like that? 

Damn this Ubuntu One Dashoard crap. As soon as I have done the more important stuff I'll turn it off so my desktop looks like it always did. Why make Linux look like a friggin Mac?  Can't even find how to start a terminal in this gooey BS.  What is the key combo again?

---

### Post by Dlambert on 2011-12-15
Not really a DOA, or at least I think.

---

### Post by MG&amp;TL on 2011-12-15
> **lile001 said:**
> DUal monitors now working under Live CD.  Looks less and less like hardware failure.  Could OS have just become hosed like that? 

Damn this Ubuntu One crap.  Can't even find how to start a terminal in this gooey BS.  What is the key combo again?

Ctrl-Alt-T ;)

I hope your hardware isn't dead. BOB was cute....

I had something very similiar when an area of disk stopped working, in the "system" bit of disk. :(

---

### Post by Ms. Daisy on 2011-12-15
> **lile001 said:**
> Can't even find how to start a terminal in this gooey BS.  What is the key combo again?

Ctl + Alt + T

> **lile001 said:**
>  Could OS have just become hosed like that? 

Have you backed up the data on the system? If you reinstall the OS, you'll know if the OS was hosed or if another problem is happening.

---

### Post by lile001 on 2011-12-15
> **Ms. Daisy said:**
> Ctl + Alt + T



Have you backed up the data on the system? If you reinstall the OS, you'll know if the OS was hosed or if another problem is happening.


Backing up data now.  I do regular backups to an external hard drive, so this one is just for insurance for last few day's work.

---

### Post by lile001 on 2011-12-15
So it sounds like people are leaning toward re-installing the OS and hoping for the best?  

How would I know if I have a bad spot on the hard drive causing this madness? and what's more, how to fix?

---

### Post by MG&amp;TL on 2011-12-15
> **lile001 said:**
> So it sounds like people are leaning toward re-installing the OS and hoping for the best?  

How would I know if I have a bad spot on the hard drive causing this madness?

You wouldn't (unless you looked at disk utility or whatever), but reinstalling will fix this (if that is what it is), because it will just not install over the bad block.

Hoping for the best is what we do a lot. :D

---

### Post by lile001 on 2011-12-15
> **MG&TL said:**
> You wouldn't (unless you looked at disk utility or whatever), but reinstalling will fix this (if that is what it is), because it will just not install over the bad block.

Hoping for the best is what we do a lot. :D

What was that sound Curly Stooge used to make?  NGGUNG NGUNG NGUNG!  THen he'd bite his nails and slap his face a few times.  THat is what I am doing right now...

---

### Post by Ms. Daisy on 2011-12-15
After you reinstall and have a functioning OS, it would be good to test for bad blocks. That can indicate impending hard drive failure.  I found this but I've never tried it.

[http://bredsaal.dk/checking-a-harddrive-for-bad-sectors-on-ubuntudebian](http://bredsaal.dk/checking-a-harddrive-for-bad-sectors-on-ubuntudebian)

---

### Post by lile001 on 2011-12-15
> **Ms. Daisy said:**
> After you reinstall and have a functioning OS, it would be good to test for bad blocks. That can indicate impending hard drive failure.  I found this but I've never tried it.

[http://bredsaal.dk/checking-a-harddrive-for-bad-sectors-on-ubuntudebian](http://bredsaal.dk/checking-a-harddrive-for-bad-sectors-on-ubuntudebian)

I am suspecting that I am having a hard drive failure.  This link points to a program called badblocks, however badblocks refuses to run because the hard drive is in use by the system, "therefore not safe to run badblocks".  

In trying to install a new Ubuntu, I come across an error message saying there are problems with the hard drive, as I suspected.  It recommends I fix them.  I really don't know how to go about that though.  Is there a way to look for errors on the hard drive?  Or use this badblocks program?

---

### Post by lile001 on 2011-12-15
Maybe the drives have to be unmounted first?  How would I do that?

---

### Post by Ms. Daisy on 2011-12-15
Like I said I haven't used the badblock program, but you may want to check the badblock manual.

If you've got another computer, I would remove the bad hard drive, put it in an enclosure, & test it through the other good computer.

---

### Post by lile001 on 2011-12-15
> **Ms. Daisy said:**
> Like I said I haven't used the badblock program, but you may want to check the badblock manual.

If you've got another computer, I would remove the bad hard drive, put it in an enclosure, & test it through the other good computer.
  Well, I am pretty sure one of them is bad now.  sdb seems to report errors.  I wonder how I will know which physical drive that is when i open the box?

I'm in way over my head here, but this is what I was just seeing on the screen:
```

e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by Ms. Daisy on 2011-12-15
> **lile001 said:**
> Well, I am pretty sure one of them is bad now.  sdb seems to report errors.  I wonder how I will know which physical drive that is when i open the box?
Take one out, close it up & test to see if it's any good.  If it is, then put it back & remove the other one.

edit: But I think you should check Disk Utility first.  See what's on each drive.

---

### Post by bluexrider on 2011-12-15
> **lile001 said:**
> Well, I am pretty sure one of them is bad now.  sdb seems to report errors.  I wonder how I will know which physical drive that is when i open the box?

I'm in way over my head here, but this is what I was just seeing on the screen:
```

e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

Well now, as the plot thickens i would say we have ourselves a hardware failure. 

1. Do not install critical data on a drive with bad blocks. Chances are pretty good you will loose it.
2. Do not install the operating system on a drive with bad blocks. Physical problems will not go away. You are just asking for a band-aid. 

I would say that hard drives are cheap enough today and good insurance. Why risk it?

---

### Post by lile001 on 2011-12-15
> **Ms. Daisy said:**
> Take one out, close it up & test to see if it's any good.  If it is, then put it back & remove the other one.

edit: But I think you should check Disk Utility first.  See what's on each drive.

Don't seem to have Disk Utility, or else it is impossible to find in this ridiculous new squishy-gooey mac clone  dashboard crap.

---

### Post by bluexrider on 2011-12-15
> **lile001 said:**
> Don't seem to have Disk Utility, or else it is impossible to find in this ridiculous new squishy-gooey mac clone  dashboard crap.

Ctrl+Alt+t = terminal

```
sudo palimpsest
```

try that

---

### Post by MG&amp;TL on 2011-12-16
> **lile001 said:**
> Don't seem to have Disk Utility, or else it is impossible to find in this ridiculous new squishy-gooey mac clone  dashboard crap.

Click on the big button at the top, then type disk utility. Squishy mac crap squishy but easy enough when you get used to it. :)

---

### Post by anewguy on 2011-12-16
Also - a key to finding more information, or *maybe* bypassing the problem, be sure to remove existing Ubuntu paritions then create new ones in a different order than before and be sure "format" is checked, then let the reinstall continue.  If you do not delete/create partitions and force a format, there are some errors that won't get fixed.  Format will sometimes "go around" bad blocks.

I might offer again that I still think it's a hardware problem - and does seem to be with your drive.  Personally, I would just replace the drive.  Normally if a disk has been running fine for a long time then gets this type of error it is indicative of larger quantities of these failures as the drive slowly dies.  It's just not worth the hassle every time it gets another error.

Dave ;)

---

### Post by lile001 on 2011-12-16
> **bluexrider said:**
> Ctrl+Alt+t = terminal

```
sudo palimpsest
```try that


THis looks like just the ticket!  A graphical drive health checker for a knucklehead like me!  It seems to report things in English, instead of the gibberish that you get in terminal based programs.  I am going to check the drive that I suspect is the bad one now.  


Meanwhile, with the suspect drive unplugged, I installed Ubuntu 11.10.  When I reboot, I get a black screen with some text messages on it, a blinking cursor that doesn't respond, or occasionally some colored lines that appear for a second or two.  The text messages seem to be reporting normal things like the battery is being checked or the realtime clock is OK.  Screen displays normal graphics when booted froma  live CD.  

Let's work on this while Palimpsest is checking that suspisious drive - How do I proceed to get the new install to display graphics?

---

### Post by lile001 on 2011-12-16
Palimpsest is reporting both hard drives to be good.

---

### Post by lile001 on 2011-12-16
> **lile001 said:**
> Well, I am pretty sure one of them is bad now.  sdb seems to report errors.  I wonder how I will know which physical drive that is when i open the box?

I'm in way over my head here, but this is what I was just seeing on the screen:
```

e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

This gibberish says something about swap space - there is definitely some Linux swap space on this particular drive.  SOooooo - I don't know if it is bad or not.

---

### Post by bluexrider on 2011-12-16
Okay, I wouldn't worry about getting the graphics to work right now. Unplug the hard drives leaving 1 plugged in. Only 1, then boot from a Live CD or DVD. Run the disk checker from the Live CD. 

You need to eliminate the one causing the issues. Once the disk checker has completed and you get a health report move on to the next one. Step by step, one by one. 

if you are satisfied with the results and have eliminated the "bad" hard drive then install or reconnect one of the remaining.

While using the Live CD run "gparted" and format the hard drive to Ext4. Then install the operating system.

If the graphic issues still occur we will work on them.

happy *buntu

---

### Post by Ms. Daisy on 2011-12-16
> **bluexrider said:**
> Okay, I wouldn't worry about getting the graphics to work right now. Unplug the hard drives leaving 1 plugged in. Only 1, then boot from a Live CD or DVD. Run the disk checker from the Live CD. 

You need to eliminate the one causing the issues. Once the disk checker has completed and you get a health report move on to the next one. Step by step, one by one. 

if you are satisfied with the results and have eliminated the "bad" hard drive then install or reconnect one of the remaining.

While using the Live CD run "gparted" and format the hard drive to Ext4. Then install the operating system.

If the graphic issues still occur we will work on them.

happy *buntu
What he said. Exactly.

---

### Post by lile001 on 2011-12-16
> **Ms. Daisy said:**
> What he said. Exactly.


I am getting conflicting and confusing information about which drive is "bad".  

Palimpsest says both drives are good. 

e2fsck reports sdb to have a bad superblock after this drive was formatted and the swap space removed out of it.  

e2fsck reports sda, now, to have a bad superblock.  It has an NTFS partition, does that cause trouble?  Formerly it reported this drive as good.  

OK, which one shall I believe?

---

### Post by Ms. Daisy on 2011-12-16
Well, if you want to err on the side of caution you should believe they're both bad. You mentioned that you rely on this computer for your business. I guess you have to decide if you're willing to risk putting your valuable business data on possibly bad hard drives.  There's no utility to fix a bad hard drive.

Silver lining to your crap cloud: new hard drives for your business would be a tax write-off...

---

### Post by bluexrider on 2011-12-16
> **Ms. Daisy said:**
> Well, if you want to err on the side of caution you should believe they're both bad. You mentioned that you rely on this computer for your business. I guess you have to decide if you're willing to risk putting your valuable business data on possibly bad hard drives.  There's no utility to fix a bad hard drive.

Silver lining to your crap cloud: new hard drives for your business would be a tax write-off...

agreed +1 for err
plus 2 for the tax write off

---

### Post by lile001 on 2011-12-16
Disk utility" is the same thing as Palimpsest, and reports both drives as good.  


Despite that, disk utility also reports a "Read error rate" of 174130348 for sdb and 5873334 for sda.  These are above the "threshold" number displayed of "6".  

THis thread [http://askubuntu.com/questions/20393/how-do-i-interpret-hdd-s-m-a-r-t-results](http://askubuntu.com/questions/20393/how-do-i-interpret-hdd-s-m-a-r-t-results)  indicates that this raw value has no meaning.  Other metrics of hard drive health look OK.  

I don't think there is anything wrong with the drives.

---

### Post by lile001 on 2011-12-16
> **Ms. Daisy said:**
> Well, if you want to err on the side of caution you should believe they're both bad. You mentioned that you rely on this computer for your business. I guess you have to decide if you're willing to risk putting your valuable business data on possibly bad hard drives.  There's no utility to fix a bad hard drive.

Silver lining to your crap cloud: new hard drives for your business would be a tax write-off...

THis 'puter will become the second computer, new computer is on order.  Second computer won't hold business data, just a second station.  I'd like to at least salvage something out of this.  I can't prove the old drives are bad, which makes it hard to convince Dell to replace them under warrantee.  

I can boot from the live CD, but after installing Linux on this stuff, nothing after boot - a few text messages then it hangs.  I'd like to have a computer that works at least somewhat.   

Where do we go to get Ubuntu talking to the graphics card?  I have looked at some threads that talk about this but quickly get completely lost.

---

### Post by lile001 on 2011-12-16
well, an amazing thing happened - I formatted bothdrives in gparted, and made them ext4 (was ext3 and ntfs) and the damn thing started and displayed!  

Hmmm...  now to get rid of that squishy Ubuntu One Dashboard crap so I can use this thing.

---

### Post by MG&amp;TL on 2011-12-16
> **lile001 said:**
> well, an amazing thing happened - I formatted bothdrives in gparted, and made them ext4 (was ext3 and ntfs) and the damn thing started and displayed!  

Hmmm...  now to get rid of that squishy Ubuntu One Dashboard crap so I can use this thing.

If you're referring to Unity (dashboard down side, fuzzy focus launcher thing on clicking top button on dash):

a) give it a chance. It's not as bad as you think once you learn some keyboard shortcuts and learn to use typing rather than menus.

b) without installing a different DE, you can't. Unity is kinda woven into the fabric of GNOME or whatever Unity is a mod of.


c) if you really can'y use it, install Kubuntu, Xubuntu or Lubuntu (in order of 'weight', descending).

---

### Post by bluexrider on 2011-12-16
> **lile001 said:**
> well, an amazing thing happened - I formatted bothdrives in gparted, and made them ext4 (was ext3 and ntfs) and the damn thing started and displayed!  

Hmmm...  now to get rid of that squishy Ubuntu One Dashboard crap so I can use this thing.

                  [How to] Make Ubuntu 11.10 Look and Feel Like GNOME 2

[http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/](http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/)

[http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/](http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/)

You might find these desirable as opposed to what you have

---

### Post by anewguy on 2011-12-17
And why I recommended way back to delete the old partitions, create new ones and be sure to format them.  This catches and clears some errors the other tools cannot.

---

