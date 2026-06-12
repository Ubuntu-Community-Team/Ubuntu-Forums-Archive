---
title: "Problems with Installing Ubuntu 11.10"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by voodoochild850 on 2012-03-12
Hi I'm new to Linux, my only experience with linux is a short time playing around with xandros 03 back in 06 but that never went far....but now I somehow accedentally deleted my windows user account and cannot log on, im trying to setup a dual boot with the Ubuntu 11.10 iso live CD, but when I try to actually install it, it wont let me partition my drive, my only options are to replace Vista, or something else, and when I do that it wont let me partition it, the first time I tried to install it it did have the option for a dual boot, I set the slider the way I wanted to but then it sat there for a long time, finally saying it failed to resize the partition, now I dont have that option....it does ask me if I want to unmount the partition, Im guessing the one it was trying to create that first time, but it doesnt seem to be able to do it....anyone know how I can resize the partiton? maybe with a program I can use from the Live CD (which is what Im using now)....Im not really sure how large I should do the partions either, I would rather actually use Ubuntu for most of my stuff and just have windows available for anything I need to do like gaming or whatever that wont work with Linux

---

### Post by roger_1960 on 2012-03-12
Hi

That sounds like you already have 4 primary partitions - the maximum.  If so you can't create another without deleting something.  Suggest you post back with the relevant info so informed advice can be given. Can you run gparted from your live disk and post a screen shot of your existing partition setup?

---

### Post by gdea73 on 2012-03-12
Yeah it'd be helpful to know that. Though also beforehand it wouldn't be a bad call to boot up the LiveCD, mount your old Windows system, find your user folder and copy its important contents to a USB flash drive or other removable media, depending on its size.

Afterward we can work on organizing your partitions. Also see if you can check the filesystem on your existing partition(s) with Disk Utility from the LiveCD, and correct errors if possible, so that the resizing will go more smoothly. I had a similar error installing Lubuntu when I had a wrongly reported amount of free space on a partition. Then from there, check your "drive health status" or "SMART status," make sure that you don't have any more serious drive problems, i.e. bad sectors.

After that then we can work out the partitioning options.

---

### Post by voodoochild850 on 2012-03-12
[IMG]https://mail.google.com/mail/?ui=2&ik=9e295545a2&view=att&th=136092ce29f5d407&attid=0.1&disp=thd&realattid=f_gzq4jrs20&zw[/IMG][IMG]http://i1127.photobucket.com/albums/l625/morri896/ss1.png[/IMG]

I didnt even know about gparted, here is a screenshot of my partitions, but during the instalation it only shows the top two, Im guessing the third is the one that was attempted to be created during the first install

---

### Post by voodoochild850 on 2012-03-12
Here is the screen shot from disk utility
[IMG]http://i1127.photobucket.com/albums/l625/morri896/ss2.png[/IMG]

---

### Post by voodoochild850 on 2012-03-13
I posted earlier so I'm sorry for the repost, but Im still having problems with getting my install to work without deleting windows, Im a linux newbie.... Im trying to install Ubuntu 11.10 from the live CD which is currently the OS I am running, I somehow deleted my windows user account and although all my stuff is still there I have no access to it...the problem is when I tried to install ubuntu last night it had the option to set it up allongside vista, I set the slider and it sat for awhile, I went to bed because It was taking a long time, in the morning i saw an error message saying that is was unsuccesfull in resizing the partition or something like that...so I tried to repeat the install, however now I dont have the option to install allongside windows, just to replace it or something else, which is what I try, but it wont let me repartition the drive....following the advice I recieved when I posted earlier I took some screenshots
sorry about the size, I just used print screen, and posted to photobucket

[IMG]http://i1127.photobucket.com/albums/l625/morri896/ss1.png[/IMG]
[IMG]http://i1127.photobucket.com/albums/l625/morri896/ss2.png[/IMG]
[IMG]http://i1127.photobucket.com/albums/l625/morri896/Screenshotat2012-03-13001312.png[/IMG]
[IMG]http://i1127.photobucket.com/albums/l625/morri896/Screenshotat2012-03-13001327.png[/IMG]
[IMG]http://i1127.photobucket.com/albums/l625/morri896/Screenshotat2012-03-13001422.png[/IMG]
[IMG]http://i1127.photobucket.com/albums/l625/morri896/Screenshotat2012-03-13001502.png[/IMG]

---

### Post by marinara on 2012-03-13
get a windows recovery disk or something like partition magic and resize the partition there.
it's a known bug that ubuntu can't resize vista partitions most of the time

**
wait actually, you might be able to just boot into windows, create a new user, then resize the partition then.

---

### Post by techjuan on 2012-03-13
I had somewhat of a similar issue. Here is what I did, following some previous post. Or if this is to hard to follow, Click on hard drive from My Computer under start and rezise the partition. Then install Ubuntu You may have to run a backup [COLOR="Red"]if you deleted the system partition[/COLOR].

From windows, run CMD command

type [COLOR="DarkGreen"]diskpart[/COLOR]

type [COLOR="rgb(0, 100, 0)"]list disk[/COLOR] to find out unallocated disk space
type [COLOR="rgb(0, 100, 0)"]select disk X[/COLOR] (X mean disk number)
type [COLOR="rgb(0, 100, 0)"]create partition extended[/COLOR]
type [COLOR="rgb(0, 100, 0)"]create partition logic size=20000[/COLOR] (create a 20Gb partition for data store)
type [COLOR="rgb(0, 100, 0)"]create partition logic size=4000[/COLOR] (create swap)
type [COLOR="rgb(0, 100, 0)"]create partition logic size=10000[/COLOR]" (create space for Ubuntu)
type [COLOR="rgb(0, 100, 0)"]create partition logic[/COLOR] (remaining space assigned to /home)
Restart and boot from Ubuntu CD
Select install Ubuntu
Select assign space Manually
Partition created for ubuntu assign to "/"
Partition created for /home assign to "/home"
Start install process

Good luck.

---

### Post by Bucky Ball on 2012-03-13
ALWAYS use the Windows Vista software for shrinking the drive before installing Windows. NEVER use Gparted (either in Ubuntu or from the bootable Gparted ISO). Bit late now, I know. ;)

You're much better off selecting 'Something Else' when it gets to the bit of the Ubuntu install you are talking about and doing it manually. This means shrinking whatever you have to Windows-wise and leaving the free space to install Ubuntu to.

---

### Post by voodoochild850 on 2012-03-13
are there any free programs that would work on Linux? I actually have absolutely no access to windows, I got this computer from my mom...couldnt figure out why I was unable to change accounts until I realized it was networked, when I turned that off I tried to rename the user account and change the password and all that but somehow deleted the account instead, now the only user account on the computer is the one used by the guy that set the computer up for her years ago when she got it, with a password I cannot guess....I tried ophcrack but it wouldnt work right for some reason, but yeah until I can find a way around that I cant use windows, but most of my work stuff I can do with linux so if I can get Linux to work then Im not to concerned with it for now

---

### Post by nothingspecial on 2012-03-13
Threads Merged.

If your thread disappears way down the list, please bump it up every 24 hours or so, rather than creating a new one.

---

### Post by voodoochild850 on 2012-03-13
well im not sure how I did it but now when I try to boot Vista it says that I need the startup disk (which I dont have) I was gonna try a few passwords that the guy said he may have used, but thats irrelevant now I guess :(

---

### Post by Bucky Ball on 2012-03-13
[http://www.google.com.au/#hl=en&gs_nf=1&cp=15&gs_id=2o&xhr=t&q=vista+startup+disk&pf=p&sclient=psy-ab&oq=vista+startup+d&aq=0&aqi=g4&aql=&gs_sm=&gs_upl=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=e2a8e1755219aa7b&biw=1024&bih=597](http://www.google.com.au/#hl=en&gs_nf=1&cp=15&gs_id=2o&xhr=t&q=vista+startup+disk&pf=p&sclient=psy-ab&oq=vista+startup+d&aq=0&aqi=g4&aql=&gs_sm=&gs_upl=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=e2a8e1755219aa7b&biw=1024&bih=597)

Try searching for some solutions. ;)

Hopefully you can find some help here. Alternatively, if you know someone who has a Vista disk you might try using that to repair startup.

Another option again is to download [Boot Repair]("http://sourceforge.net/projects/boot-repair-cd/Boot") which may be able to fix your MBR. Pretty sure there is a way around this; hopefully a more knowledgeable head can chime in (I rarely use Windows).

---

### Post by voodoochild850 on 2012-03-13
well at this point ive pretty much given up on getting vista to actually work again for now, mostly im just wanting to repartition my drive in a way that I can install ubuntu without deleting all my stuff, most of my personal files I've backed up to a flash drive, but my work files wont fit on it (its just 4gb) Ive been looking around for repartitioning software that will run on ubuntu but so far with no success

---

### Post by Bucky Ball on 2012-03-13
There's already repartitioning software in Ubuntu and you can do that as part of the install or boot from the install CD, 'Try Ubuntu', get to the desktop and open Gparted (partition editor). To repartition you need to do it from the CD as the partitions need to be unmounted. This is easiest. 

It's all there already! Just do that and delete the lot (apart from the partition you want to save).

---

### Post by voodoochild850 on 2012-03-22
> **Bucky Ball said:**
> There's already repartitioning software in Ubuntu and you can do that as part of the install or boot from the install CD, 'Try Ubuntu', get to the desktop and open Gparted (partition editor). To repartition you need to do it from the CD as the partitions need to be unmounted. This is easiest. 

It's all there already! Just do that and delete the lot (apart from the partition you want to save).

I tried that, it only allows me to change the size of the partition by 2mb, also when i try to unmount the drive it doesnt (prolly cause this is the only HDD)

---

### Post by Bucky Ball on 2012-03-22
As mentioned, you need to boot from the LiveCD, 'Try Ubuntu', then open Gparted and resize your partitions. That way all partitions will be unmounted from the start. If they're not, unmount them in Gparted (no, you can't do this running from the hard drive as you can't unmount the partition you are running the OS on).

---

### Post by wlraider70 on 2012-03-23
the reason you can change by 2 mb is because that is the un-allocated space on the disk.

You have to free space first. That is shrink the first partition then enlarge/make a new partition. It wont auto-subtract from 1 to build 2.

---

### Post by voodoochild850 on 2012-04-05
It wouldnt allow me to unmount the drive for some reason, but I have installed Linux on the entire drive now, just moved all of my stuff to another computer

---

