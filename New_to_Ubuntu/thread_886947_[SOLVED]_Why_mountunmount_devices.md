---
title: "[SOLVED] Why mount/unmount devices?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by rbjscv on 2008-08-11
I'll jump right in on this one.

Why do I have to mount and unmount devices?  Why can't I simply hot-plug/hot-unplug as others do in Whimdoers (and as I did before seeing the light of freedom.

The answer may be painfully obvious, but to me it is one of the mysteries of my machines life.

---

### Post by OutOfReach on 2008-08-11
Windows (I believe) also mounts/unmounts devices, but they don't call it mount/unmount. And from what I remember you have to 'Safely Remove' devices before you un-plug them in Windows.

---

### Post by lisati on 2008-08-11
The "Mount" provides the connection between your hardware and the OS. Ubuntu will do this automatically much of the time. The "unmount" tells the OS that you've finished with it, so that the OS will make sure that it's not currently in use, and that if necessary the OS will finish writing data to the device. If you don't properly unmount, there is a possibility that you could lose or scramble data.

Strictly speaking, you shouldn't just unplug devices in Windows either, for similar reasons.

---

### Post by loboc on 2008-08-11
when you work with a removable drive alot of the writes may be delayed until unmounting if you are moving instead of copying you might lose you data completly in delayed write limbo.  See this for an example

[http://ubuntuforums.org/showthread.php?t=239631](http://ubuntuforums.org/showthread.php?t=239631)

---

### Post by rbjscv on 2008-08-11
Otay Buckwheat!  Now it makes sense.  I was mounting/unmounting in Linux as I found out the hard way that problems happened. The reason why was what I couldn't mount my mind on.

But back in my windows days I admit that I always just pulled whatever device out without a care in the world.  And of course did the same when plugging in.  Now when I have to mess in the Gates System I'm much more careful about peripherals.

---

### Post by ajgreeny on 2008-08-11
Interestingly, if you use a USB flash drive in windows (NTFS) and just pull it out without removing it safely, you will find that it will not mount in Ubuntu as it normally would.  This is due to some form of lock that NTFS puts on improperly removed USB drives.  If it happens to you, just use it in windows again, but remove it properly this time to reset it.

---

### Post by rbjscv on 2008-08-11
Yep, learned that lesson 'bout flash drives the hard way too.

Seems that I get most of my knowledge (computers and rest of life) from just doing something and then finding out what the consequences are.  It apparently has never occurred to me to do otherwise.

Ce la vie.

---

### Post by SunnyRabbiera on 2008-08-11
Well the linux way of mounting and unmounting is honestly a good idea.
For one when you enter a disk into the system instead of just jarring it out like you do in windows linux allows the device to have some breathing room.
I found out the linux way is better because I had two computers with the same DVD drive in it, one windows one linux... guess what lasted longer?

---

### Post by cybrsaylr on 2008-08-12
> **ajgreeny said:**
> Interestingly, if you use a USB flash drive in windows (NTFS) and just pull it out without removing it safely, you will find that it will not mount in Ubuntu as it normally would.  This is due to some form of lock that NTFS puts on improperly removed USB drives.  If it happens to you, just use it in windows again, but remove it properly this time to reset it.

I've also found this out the hard way.
It never seemed to matter when only using Windows but when switching to linux the ext HDD wouldn't mount again unless I went back into Windows and removed it properly first.

---

### Post by misswham on 2008-08-12
I am so dumb when it comes to this.  What and how do u unmount and mount in both linux and XP?  I thought you just pulled it out of the usb port.

---

### Post by Northsider on 2008-08-12
I learned the hard way with not unmounting and just pulling out a USB device...I had to rewrite a whole paper.  Now I always make sure to unmount, even in windows

---

### Post by lisati on 2008-08-12
> **misswham said:**
> I am so dumb when it comes to this.  What and how do u unmount and mount in both linux and XP?  I thought you just pulled it out of the usb port.

No - if you've written to files on the device, the OS might not have finished doing the physical write. Unmounting (Linux)/"safely removing hardware" (Windows) tells the computer, amongst other things, to make sure that the physical information matches what your software thinks has happened.

See [http://en.wikipedia.org/wiki/Cache](http://en.wikipedia.org/wiki/Cache) and [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB))

---

### Post by LaRoza on 2008-08-12
> **misswham said:**
> I am so dumb when it comes to this.  What and how do u unmount and mount in both linux and XP?  I thought you just pulled it out of the usb port.

Usually, devices like flash drives are mounted when they are found in both Windows and Linux (although you can configure them not to in both)

To unmount, you basically just have to flush the cache and the kernel "lets it go". In Windows, it's drive letter is gone and in Linux it is removed from the / tree (usually mounted in /media/)

---

### Post by hyper_ch on 2008-08-12
> **rbjscv said:**
> Seems that I get most of my knowledge (computers and rest of life) from just doing something and then finding out what the consequences are.  It apparently has never occurred to me to do otherwise.

That's learning by doing ;) it's actually a good way, except if you're under pressure of achieving something... then you may not just want to trial and err ;)

---

### Post by 3rdalbum on 2008-08-12
> **misswham said:**
> I am so dumb when it comes to this.  What and how do u unmount and mount in both linux and XP?  I thought you just pulled it out of the usb port.

On Windows, you go to the system tray and the Safely Remove Hardware icon. On KDE, there is a similar icon. On Gnome, you right-click the drive's icon and choose Unmount.

Windows usually mounts disks in sync mode, which means that your data gets written to the device as soon as possible. Linux maintains a buffer, which causes less damage to Flash drives and causes copying and writing operations to finish faster. There's also the side-effect that the source disk can be removed faster. The buffer is "flushed" (written to the drive) when it is full, when the drive is unmounted, or when it's been around for a long while.

Even though Windows doesn't maintain a buffer, it's still a bad idea to remove disks without unmounting them first. The exact moment that you rip out a drive could be the exact moment that a program decides to write a file to it.

Unfortunately the "Just pull it out" mindset and habit has been established in the Windows world since the days of floppy disks. Apple had the right idea of having the floppy drive eject the disk when the operating system unmounted it, and not providing a physical button for it. (In emergencies, you could get a straightened paperclip to manually push the disk out - yes, the little hole in your DVD drive today is a descendent of this!)

---

