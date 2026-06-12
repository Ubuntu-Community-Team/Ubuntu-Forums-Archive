---
title: "Ubuntu os from scratch"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by klient57 on 2012-12-10
Got a dell inspiron9300. Changed hd due to virus, and did format it. Want to install Ubuntu on it, and tried download to USB 2gb. , but it says , bootmgr is missing. What should I do?

---

### Post by Frogs Hair on 2012-12-10
Hello and Welcome 

This may help and wait for others who have installed via USB.[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ibjsb4 on 2012-12-10
I would suggest trying unetbootin and see if you have better luck with it.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by oldfred on 2012-12-10
Links above should work.

The bootmgr missing is from a Windows boot. Generally you then still have a Windows boot loader in the MBR and the Windows boot partition is missing or corrupted.

Since Windows only boots from internal drive that has to be what is booting. You may need to change settings in BIOS or if you have a one time boot key (f12 on my system) use that to boot CD/DVD or USB flash device.

---

### Post by klient57 on 2012-12-11
I took the USB and connected it to the pc i used to download Ubuntu, was thinking to install it on the USB again, correct ....   but now USB is only 753mb.  was 1.86gb last time I did it.?   I need a absolute beginners section help for noob for life..!   What do I do now??

---

### Post by mörgæs on 2012-12-11
It´s likely that you have hidden files on the USB drive.

---

### Post by klient57 on 2012-12-11
Thx for helping me ,Frogs Hair, ibjsb4, oldfred and mørgæs.  Just for info,  I am horrible on all pc stuff, and ruined a few computers after I "fixed" them a bit..  So is it a easy way to do this? Or can any of u do it, if i conect the dell9300 to internet?

---

### Post by klient57 on 2012-12-11
> **mörgæs said:**
> It´s likely that you have hidden files on the USB drive.
 ok. how do i clean it.?

---

### Post by mörgæs on 2012-12-11
I think it's time you begin experimenting. In your file manager search for the setting that controls whether or not hidden files are shown.

---

### Post by klient57 on 2012-12-11
> **mörgæs said:**
> I think it's time you begin experimenting. In your file manager search for the setting that controls whether or not hidden files are shown.
 im worse than i thougth. changed to show hidden files, but cant see any and still 753mb..

---

### Post by klient57 on 2012-12-11
> **mörgæs said:**
> I think it's time you begin experimenting. In your file manager search for the setting that controls whether or not hidden files are shown.
 How can i order a cd with ubuntu?  i give up. i am useless on pc stuff.

---

### Post by GordThompson on 2012-12-11
re: the machine you are using to create the USB -- Is it also running Ubuntu, or is it running something else? Please be specific; it will help us give you more precise instructions.

---

### Post by klient57 on 2012-12-11
> **GordThompson said:**
> re: the machine you are using to create the USB -- Is it also running Ubuntu, or is it running something else? Please be specific; it will help us give you more precise instructions.
 its windows 7 build 7601 , not genuine.

---

### Post by GordThompson on 2012-12-11
Okay, on the hard drive of the Windows machine you need two things:

1. The Ubuntu ISO file you downloaded, and 

2. A copy of the UNetbootin program: Go to...

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

...and click the "Download (for Windows)" link.

Reply back here when you are ready to proceed with the next step.

---

### Post by klient57 on 2012-12-11
> **klient57 said:**
> its windows 7 build 7601 , not genuine.
 Since all computers need a os to work, why dont they put a chip with a os when they make them?

---

### Post by GordThompson on 2012-12-11
> **klient57 said:**
> Since all computers need a os to work, why dont they put a chip with a os when they make them?
Well they do, sort of: it's called "firmware" and it's very important but also very limited in what it can do. However, let's not stray too far from the topic at hand.

---

### Post by klient57 on 2012-12-11
> **GordThompson said:**
> Okay, on the hard drive of the Windows machine you need two things:
 
1. The Ubuntu ISO file you downloaded, and 
 
2. A copy of the UNetbootin program: Go to...
 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
...and click the "Download (for Windows)" link.
 
Reply back here when you are ready to proceed with the next step.
 ok.  run or save?

---

### Post by GordThompson on 2012-12-11
> **klient57 said:**
> ok.  run or save?
Save. You'll run it later.

---

### Post by klient57 on 2012-12-11
> **GordThompson said:**
> Save. You'll run it later.
 unetbootin-windows 581 download has completed.

---

### Post by GordThompson on 2012-12-11
Now, plug the USB stick into the Windows machine. If Windows pops up an AutoPlay dialog asking what to do with the contents of the stick (e.g., "Import pictures and videos", "Open folder to view files", etc.) just close the dialog. 

Click the Windows "Start" button, then click "Computer". Verify that the USB stick appears under the section "Devices with Removable Storage".

Okay so far?

---

### Post by klient57 on 2012-12-11
> **GordThompson said:**
> Now, plug the USB stick into the Windows machine. If Windows pops up an AutoPlay dialog asking what to do with the contents of the stick (e.g., "Import pictures and videos", "Open folder to view files", etc.) just close the dialog. 
 
Click the Windows "Start" button, then click "Computer". Verify that the USB stick appears under the section "Devices with Removable Storage".
 
Okay so far?
 ok

---

### Post by GordThompson on 2012-12-11
Good. Now, in the "Computer" window, right-click on the USB stick and choose "Format...". Choose FAT32 for the File system and use the "Quick Format" option. Double-check that you have selected the USB stick (and NOT the hard drive), then click the "Start" button. When the format is completed, close the format dialog.

---

### Post by klient57 on 2012-12-11
> **GordThompson said:**
> Good. Now, in the "Computer" window, right-click on the USB stick and choose "Format...". Choose FAT32 for the File system and use the "Quick Format" option. Double-check that you have selected the USB stick (and NOT the hard drive), then click the "Start" button. When the format is completed, close the format dialog.
 ok, but now its 749mb.

---

### Post by audiomick on 2012-12-11
> **GordThompson said:**
>  Double-check that you have selected the USB stick (and NOT the hard drive),

Make that triple check, and then check it again to make sure. If you point this action at your hard drive instead of the stick, your computer will be dead in the water.

Edit: looks like it worked. Good.

---

### Post by GordThompson on 2012-12-11
> **klient57 said:**
> ok, but now its 749mb.
Right-click the USB stick and choose "Properties". What does it say for "Used space", "Free space", and "Capacity"?

---

### Post by klient57 on 2012-12-11
> **GordThompson said:**
> Right-click the USB stick and choose "Properties". What does it say for "Used space", "Free space", and "Capacity"?used 4kb    free 749mb      capacity 749mb

---

### Post by GordThompson on 2012-12-11
> **klient57 said:**
> used 4kb    free 749mb      capacity 749mb
Okay, try this: Click the Windows "Start" button, then right-click "Computer" and choose "Manage". In the Computer Management dialog click "Disk Management" in the left-hand tree view. In the lower-middle pane you should see pictures corresponding to the various drives for that machine. Does the picture for the USB stick ("Removable") show any unallocated space?

---

### Post by klient57 on 2012-12-11
> **GordThompson said:**
> Okay, try this: Click the Windows "Start" button, then right-click "Computer" and choose "Manage". In the Computer Management dialog click "Disk Management" in the left-hand tree view. In the lower-middle pane you should see pictures corresponding to the various drives for that machine. Does the picture for the USB stick ("Removable") show any unallocated space?
 yes.  1,13gb.

---

### Post by GordThompson on 2012-12-11
Aha. When you right-click on the allocated (749 MB) part is the "Extend Volume..." option enabled? If so, then you should be able to extend that partition back to the full size of the USB drive.

---

### Post by klient57 on 2012-12-11
> **GordThompson said:**
> Aha. When you right-click on the allocated (749 MB) part is the "Extend Volume..." option enabled? If so, then you should be able to extend that partition back to the full size of the USB drive.
 extend volume wont work.

---

### Post by GordThompson on 2012-12-11
> **klient57 said:**
> extend volume wont work.
Darn. Do you have another USB stick (2 GB or larger) you could use?

Or, can the Windows machine burn a DVD? If so, and if you have a spare blank DVD/R or DVD/RW then you could just burn the Ubuntu ISO image to disk (using an app like ImgBurn) and then use that to boot the Dell and install Ubuntu.

Or, as you mentioned earlier, you could just buy a copy of the DVD here:

[http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17)

---

### Post by mörgæs on 2012-12-11
> **GordThompson said:**
> 
Or, as you mentioned earlier, you could just buy a copy of the DVD here:

[http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17)

No, using this computer you shouldn't buy Ubuntu. Go for Xubuntu 12.04.

Just google your way to a local online shop.

---

### Post by klient57 on 2012-12-11
> **GordThompson said:**
> Darn. Do you have another USB stick (2 GB or larger) you could use?
 
Or, can the Windows machine burn a DVD? If so, and if you have a spare blank DVD/R or DVD/RW then you could just burn the Ubuntu ISO image to disk (using an app like ImgBurn) and then use that to boot the Dell and install Ubuntu.
 
Or, as you mentioned earlier, you could just buy a copy of the DVD here:
 
[http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17)
 Thats the largest usb i got. and no empty dvds.   Can i connect dell9300 to windows pc ,with a normal cabel?   and boot it from the windows?             Anyway, thank you very much for beeing so helpfull .!     :)

---

### Post by GordThompson on 2012-12-11
Actually, the suggestion by mörgæs raises another possibility. The latest desktop ISO for Ubuntu 12.10 is 753 MB, so it is too big to fit on the USB stick as it stands now. However, if you were to install a slightly lighter version onto the USB stick it might still fit. For example, the standard desktop CD for Xubuntu 12.04.1 is 682 MB so it might just fit on the USB stick's existing partition. (I don't know how much overhead a bootable USB needs.)

If you want to give that a try then head over to

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

scroll down to the "Latest stable release: 12.04, Precise Pangolin" section, pick a mirror, and download the file

xubuntu-12.04.1-desktop-i386.iso

---

### Post by GordThompson on 2012-12-11
> **mörgæs said:**
> Go for Xubuntu 12.04.
In my previous post I specified 12.10 because it was the latest version. Is there a particular reason why you recommended 12.04 over 12.10?

---

### Post by arpanaut on 2012-12-11
12.04 is a LTS release and has 5 years of support.
12.10 is not LTS thus only has 18 mo. of support.
Better for a noob to not being forced to upgrade in such a short period of time.
Leaves more room/time to learn and grow used to system.

---

### Post by danielz123 on 2012-12-11
unetbootin worked for me.. I had a similar situation happen to me last friday, and I'm happy to say that Ubuntu running from a USb stick let me use my laptop instead of throwing it out.

---

### Post by GordThompson on 2012-12-11
> **arpanaut said:**
> 12.04 is a LTS release and has 5 years of support.
12.10 is not LTS thus only has 18 mo. of support.
Better for a noob to not being forced to upgrade in such a short period of time.
Leaves more room/time to learn and grow used to system.
Good point. I've edited my post, above.

---

### Post by GordThompson on 2012-12-11
> **GordThompson said:**
> the standard desktop CD for Xubuntu 12.04.1 is 682 MB so it might just fit on the USB stick's existing partition. (I don't know how much overhead a bootable USB needs.)
I just checked the USB I created two days ago and the space used on the USB was only about 3% more than the size of the ISO image itself, so I think the chances are good that a bootable copy of Xubuntu will fit on a USB with only 749 MB of usable space.

---

### Post by mörgæs on 2012-12-11
> **GordThompson said:**
> In my previous post I specified 12.10 because it was the latest version. Is there a particular reason why you recommended 12.04 over 12.10?

Yes, I'm not sure that this computer supports PAE. If it doesn't, 12.04 is the only option.

[http://xubuntu.org/news/12-04-release/](http://xubuntu.org/news/12-04-release/)

---

### Post by GordThompson on 2012-12-11
> **mörgæs said:**
> Yes, I'm not sure that this computer supports PAE. If it doesn't, 12.04 is the only option.

[http://xubuntu.org/news/12-04-release/](http://xubuntu.org/news/12-04-release/)
Good to know, thanks!

---

### Post by GordThompson on 2012-12-12
> **klient57 said:**
> Can i connect dell9300 to windows pc ,with a normal cabel?   and boot it from the windows?
Unfortunately no, that won't work. However, I just did a test with an old USB stick and a copy of...

xubuntu-12.04.1-desktop-i386.iso 

...and I can confirm the following:

1. After I reduced the partition size on the USB stick so only 749 MB was available (same as yours) the UNetbootin app was able to create a bootable Xubuntu image on the stick with about 45 MB to spare. So, you *can* get Xubuntu onto the Dell if you still want to try.

2. I used the GParted app to mess with the partition size on the stick, so once you get Xubuntu installed on the hard drive of the Dell you can use GParted to fix the partition on your USB stick and get your "missing" 1.13 GB back.

> **klient57 said:**
> Anyway, thank you very much for beeing so helpfull .!     :)
You're welcome. Don't give up; you can still win this battle! (BTW, I'm typing this reply from Firefox in Xubuntu after booting from the USB stick I built. It really does work!)

---

