---
title: "WD Mybook Essential connected but not appearing"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by duracella on 2011-11-02
**WD Mybook Essential 3.0**
Hey, about 1month ago i bought this external hdd, have been working good all the time. 
worked fine with my laptop (windows7) and my pc (ubuntu 11.10). but two days ago it suddenly is not appearing in either ubuntu or win7.... 
the warranty is not out, so i could send it to repair... but the thing is, i have alot of files & stuff on it, and don't want to loose it (no, have not taken backup of it yet.. :( )

Im going to run dual boot with win7 and ubuntui, so i prefer it would work for both..

[EDIT: I have not used the cd's following the external hdd... and in win7 my laptop tries to install a driver for it when i plug it in, but fails....]

It's not showing up in the folder computer, media or anything (not even in disk utility)
Tried connecting it to different usb 2.0 and 3.0 ports, but same in every port...

I ran this command to check if the device was connected (just to be sure it was nothing wrong with the cables:
```
 lsusb 
```Result without Mybook Essential connected:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
```Result with Mybook Essential connected
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 007: ID 1058:1140 Western Digital Technologies, Inc.
```Would be very happy if anyone could help me with this!

Picture of the external hdd:
[http://www.backupharddrive.org.uk/wp-content/uploads/2011/06/WD-My-Book-Essential-3.0-2-TB-External-Hard-Drive-USB-3.0-2.0.jpg](http://www.backupharddrive.org.uk/wp-content/uploads/2011/06/WD-My-Book-Essential-3.0-2-TB-External-Hard-Drive-USB-3.0-2.0.jpg)

---

### Post by Eiji Takanaka on 2011-11-02
Probably file system incompatability dude.

What file system you got on that sucker?

---

### Post by Eiji Takanaka on 2011-11-02
I ran into similar difficulties when i didn't unmount it cleanly.

---

### Post by Mark Phelps on 2011-11-02
If you send it it, they'll either replace it or do a low-level format on it -- whichever is easier and cheaper for them.  Either way, you'll lose everything on it, plus risk someone else copying off your files.

Perhaps you simply unplugged the drive without safely removing it first.

When you boot up Win7, connect the drive and look in the Disk Management utility.  It may show up there without a drive letter.  IF that happens, you might be able to assign a letter and run CHKDSK on it.  I've had that happen before on my external drives.

---

### Post by duracella on 2011-11-03
The file system is NTFS, i unmounted it every time i plugged it out from win7, but was told that it was not neccesary in ubuntu....

but the thing is that i was copying files to the external drive, when it stopped working, so it was connected...

have not checked disk utility in win7(only in devices, where it ain't showing up), after i had it connected to ubuntu for like 2hours, it showed up in disk utility(ubuntu)

there it said "not supported" and the option to safe removal, but could still not access it..

a guy was talking about that since i was using gnome-shell i had to install something called "Drive menu"...?


but a colleague of mine, said it might just went in sleep mode... so he was going to try to force it to wake up later today... 

hope for the best that it works!

Thanks for all help & tips so far!

---

### Post by duracella on 2011-11-03
> **Eiji Takanaka said:**
> I ran into similar difficulties when i didn't unmount it cleanly.

what was your soloution to your similar problem?

---

### Post by Eiji Takanaka on 2011-11-03
My solution was to get the guy who introduced me to ubuntu to have a look at it, as at the time i was a total nube to ubuntu. =P  I'm pretty sure it was to do with a bit of a dirty dismountage or something, i always click on the safe remove button for ubuntu with my external hardrive as a matter of procedure from then on out.   Hmm as i recall it was either to do with the filesystem type, (my external hardrive is a western digital like yours), or as aforementioned it was removing it before unmounting it, that seemed to mess it up.   I'm sorry i can't be more specific about a fix, just a few ideas for symptoms and possible causes.   Hope your friend can help you slightly better!

---

### Post by Mark Phelps on 2011-11-03
> **duracella said:**
> The file system is NTFS, i unmounted it every time i plugged it out from win7, but was told that it was not neccesary in ubuntu....

Actually, yes it is needed in Ubuntu.

Just unplugging the drive can not only leave it in a state that it won't mount the next time, it can also cause data loss -- because NTFS does delayed writes.  Safely Removing the drive causes any remaining writes to the drive to be performed so that, when you unplug it, there is no data loss.

You would need to run a CHKDSK on this drive in MS Windows -- which is why I suggested connecting it under Win7.

---

### Post by duracella on 2011-11-04
It shows up in disk manager in win7, but the disk says not initalized, tried to initalize it, but only says error, tried using the  cd's following and the software from their internet site, but gives me the message that i have to close all programs, but i don't have any other programs up and running, seems like chckdsk doesn't see that the disk is there...

unfortunately what my colleague thought was the problem seemed to not be the problem...

---

### Post by snyfear on 2012-11-12
Hi,

I am facing the same kind of issue with a Western Digital MyBook Essential 3To on Lubuntu 12.10.
The HDD doesn't even  appear in "lsusb" command when it works perfectly on my dualboot with Windows XP.
Please refer to my french post for more commands result :
[http://forum.ubuntu-fr.org/viewtopic.php?id=1102631](http://forum.ubuntu-fr.org/viewtopic.php?id=1102631)

---

### Post by Bartender on 2012-11-12
I really *hate* these pre-packaged external drives.  Especially the ones from WD.  They put a little circuit board inside with some firmware installed on that board.  When your PC tries to access the drive, it has to go thru that board and the firmware first.

My Dad gave me a WD MyBook a few years ago that he couldn't figure out.  I could see it in Windows but nothing in Linux.  I ripped it open (they're designed to discourage disassembly) and freed the HDD from its prison.  Plugged it into a dock.  It now works just like you would expect in Windows or Linux.

If you decide to free your drive, one thing to watch out for.  Older docks don't support huge drives.  The oldest dock I have, a 3 year old Vantec, can only spin a 1TB drive.  That's what they say anyway, and I haven't bothered to test that claim.

---

### Post by snyfear on 2012-11-12
Thank you for the information Bartender. I was not aware about such internal firmware.
Anyway, I would prefer to not open this brand new external HDD so I will keep your solution as the one of the "last chance".

---

### Post by Bartender on 2012-11-12
Yeah, there's no turning back once you start to tear into one of these.

---

### Post by snyfear on 2012-11-13
It seems my HDD isn't recognized only when plugged before startup.
When I unplugged and plugged again the HDD during Lubuntu execution, it is perfectly recognized.

Is somebody knows where comes this detection problem the solution will be welcome?
Otherwise, if it's possible to write a script which is able to simulate the unplugged/plugged of the HDD at startup would be a welcome workaround. Some clues for it?

Thanks in advance,

---

### Post by Bartender on 2012-11-13
sny -
Can you look into your BIOS and find out whether the Hard Drive Emulation is IDE or AHCI?  I've been reading a bit about this lately.  My impression is that the PC has to be in AHCI mode in order to "hot-plug" a drive.  I think there are other factors, too, but pretty sure that AHCI has to be in effect or it's no go.

If your BIOS says that Hard Drive Emulation is "IDE", you can't just flick it to AHCI.  The OS has to be installed _after_ the PC is set to AHCI or IDE.  If you installed the OS (Windows or Linux, doesn't matter) with BIOS set to IDE, then switch to AHCI later, the PC won't recognize the HDD.

---

### Post by snyfear on 2012-11-14
Thank you for your help [Bartender]("http://ubuntuforums.org/member.php?u=52039").

I will dig this clue as soon as I'll come back at home and will try to be back with my current Hard Drive Emulation mode.

However, I don't face problem with the hot plug. In fact, it's the only thing which works. My problem is encountered only when the HDD is plugged before the laptop start, so I am not sure it's corresponding to your clue.

---

