---
title: "Best stable version that runs out of the box"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by canadianBill on 2013-03-21
Hello,

I've got a new laptop from work that will not allow me to install Ubuntu side by side with Windows (ugh) but I would rather take advantage of its functionality with a stable version of Ubuntu that I can run from CD and/or USB stick.

Any thoughts on this?

I imagine USB would offer more flexibility since then files could be saved, altered etc.  I was considering installing Wubi to try to bypass security and get a version of Linux on my laptop but not sure that would work.

I believe version 12.04 is the latest.  Is this relatively fast?  Is it secure enough?  Are there limitations?

Any considerations would be useful as to how I can best achieve this.

---

### Post by fantab on 2013-03-21
If you have Windows 8 preinstalled then SEARCH these for "Dual boot Windows 8"... All released versions of Ubuntu are STABLE. 12.04 is LTS (Long Term Support) supported until 2017. Latest is 12.10 and 13.04 will be released sometime in April.

You can run ubuntu LiveDVD/USB to try ubuntu for a few days but for it to be fast it has to be installed, either on Hard Disk or USB drive. Since you can install ubuntu alongside Windows, I suggest you do so eventually.

To create a USB of Ubuntu.iso use [Unetbootin]("http://unetbootin.sourceforge.net/") from Windows.

---

### Post by 3rdalbum on 2013-03-21
12.10 is the latest. It has another year of support - until 14.04 comes out in April 2014.

12.10 has more recent hardware compatibility than 12.04, however 12.04 may be a little more stable. Just a little. It will be supported for another four years as it is a Long Term Support release.

12.04 and 12.10 are both fast and stable on modern hardware.

The live USB idea seems fine. Just be aware it won't be as fast as a regular hard disk installation.

---

### Post by caffeinatedev on 2013-03-21
canadianBill,

You'll have to figure out how to get into your BIOS to disable SecureBoot. It's usually the ESC or F2 keys at startup. I was able to disable SecureBoot and install Ubuntu alongside Windows 8, [see this thread]("http://ubuntuforums.org/showthread.php?t=2087533&page=2") for instructions on an ASUS machine.

---

### Post by squakie on 2013-03-21
it is probably the uefi bios that is messing you up.  I went through a mess recently with a new laptop and fighting that.  it's not an Ubuntu issue, but rather how your vendor implemented uefi.  secure boot is just an option within that and disabling OK t doesn't work a lot of the time.  there are also certain laptops you can brick trying all this.  I have a thread about not being abl e to boot from CD out there in which guru oldfred provided tons of information.  I would suggest using the advanced search function of the forum and search with my use rid to find that thread and read everything olfdred posts including what's in the links they provided before attempting this.  I'd provide you with the link but I'm on my tablet right now and I'm rather "tablet challenged" ;)

---

