---
title: "Shrinking Ubuntu 12.10 Partition?"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by Deliphin on 2013-10-23
I'm starting to run out of space on my Win7 Partition on my 1TB harddrive, I have roughly half in Win7 and half in Ubuntu 12.10, and since I rarely use Ubuntu, I would like to move a bit of space to Win7, an I have tried GParted (On Win7 AND Ubuntu) and EaseUS (On Win7) and neither will shrink the Ubuntu Partition, but all are fine with the Win7 one. I attempted a live disk, and it wouldn't boot, I even checked my BIOS and set CD to first boot, and it still went to regular boot.

OS: Windows 7 Home Premium, Ubuntu 12.10 (I believe 64 bit is what I got, but not sure. Most likely 64, as Win7 is 64bit.)
I've lost the link to the live disk, but if I find it again, I will link it here. (I got it from a friend, (the link, I burned the disk) who told me this one would work with Ubuntu.)

NOTE: I put this in absolute beginners, since I can't say I'm anywhere near experienced in Ubuntu, despite having had it for around a year. (I just rarely use it.)

---

### Post by dekadence2 on 2013-10-23
Hello,

You must resize partitions from a live CD/USB, you need download Ubuntu live CD/USB from: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) (12.04 LTS), make a botable USB/CD and boot this from your BIOS (Press F8 in startup in ASUS motherboards, F9 in HP notebooks, etc etc...) this depend of the manufacturer of your computer.

Login in Ubuntu and press Start (the first icon in sidebar), type gparted in search bar and click in "Partition manager GParted" icon.

Resize and move Ubuntu partition to make free space after Windows partition.

Now, resize Windows partition taking the free space, if you have problems with resize in ntfs partition run "chkdsk /f" in CMD of Windows and try again from Ubuntu live USB/CD.

A greeting

---

### Post by Impavidus on 2013-10-23
+1 to dekadence2, except for one small note: it may be best to use the live disk only to shrink the Ubuntu partition. Use Windows tools to enlarge the Windows partition.

---

### Post by Deliphin on 2013-10-23
That's what I had in plan. Burning the disk now, will reply when the live disk does the job.

---

### Post by dekadence2 on 2013-10-24
> **Impavidus said:**
> +1 to dekadence2, except for one small note: it may be best to use the live disk only to shrink the Ubuntu partition. Use Windows tools to enlarge the Windows partition.

Yes, thanks for the tip, in my case, resizing NTFS partition with GParted Windows 8 no boot, I needed run "chkdsk /f" after resizing.

A greeting

---

### Post by Deliphin on 2013-10-25
I burned the iso itself with windows 7's own disc burner, wouldn't boot. (Even checked BIOS, nothing wrong.)
I extracted the iso's files, and burned that. wouldn't boot.
I burned the iso with IMGBurn, wouldn't boot. (IMGBurn is what I used to burn my Ubuntu 12.10 disc to get Ubuntu.)
This is what I tried with the Ubuntu 12.04 LTS disc. My Ubuntu 12.10 disc didn't work either.

I'm going to try the GParted livedisk from their site ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) tonight.

---

