---
title: "Operating System Not found Error"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by ndakota on 2012-06-29
Hi guys this is my first post
[COLOR=DarkRed]_**(Hi)Story:**_[/COLOR]
I've been using 10.10 (64 bit) along with windows7 for over a year. Today as ubuntu gave **you have low space **error, I tried to extend the linux partition on /dev/sda7 (this is where i installed it)with Paragon Partition Manager on win7. resulting a boot failure, then I reinitiated the grub. Surprisingly the extended part is not really working(i think so..because of these reasons)
**(**linux - **/dev/sda7** with ext4
 win7 - **/dev/sda2** **)**
[B]1. 
[/B]i)** fdisk -l** gave the output with (sorry..currently i can't give the full output as windows startup repair is running for *quite a while*)
/dev/sda2 * windows....
.
.
/dev/sda7 Linux with 25.6 GB (13.3GB + recently extended)

ii)but **df -h**
 mounted on /dev/sda7
13.3 GB(total) 99%(used) "/"
.
.
(I didn't give any separate partition for "/home" or "/usr" . But Swap is there with some some 850 MB(sorry again..)
iii)windows NTFS drives didn't even show up in the *places* menu..

So followed the yahoo [link]("http://uk.answers.yahoo.com/question/index?qid=20110525123845AA1Z9Q0") and there I screwed up big time. 
This is what i did.. 
I ran (donno what they mean or do..)
$**fdisk /dev/sda**
command (m for help):**o**
command (m for help):**w**
then restarted... (later found that I misread the link and ran those commands:confused:)

Then popped another issue [COLOR=DarkRed][U][B]
Present:[/B][/U][/COLOR]
**Operating system not found **error 
These are the futile things I did to cure the disease. 
1)booted from ubuntu 10.10 live CD and found that **fdisk -l **no longer showing the hard disk partitions (no /sda7 ..no /sda2), just showing the /sdb(USB..). **Atleast earlier it ntfs drives were invisible in places but showed up with fdisk -l command..** now nothing remains)
2)So I am trying to do things with Windows7 CD, started running startup repair restarted after 2 hours and ran it again still going on like a boat in a sea..) Need help !!!


[COLOR=Blue]**If the post was big.. here is the brief explanation of problem**[/COLOR] 
Operating System not found error..
1)with linux live CD--> unable to do anything as **fdisk -l  **is not showing the hard disk partitions
2)with windows7 CD --> startup repair is there.. like forever
(think I gave all the required information..:confused:.)

---

### Post by southerngeek on 2012-06-29
Hi ndakota, welcome to the forums!

Well, what you did with your ```
fdisk /dev/sda
``` command was:
o = told fdisk that you wanted to create a new partition on /dev/sda
w = confirmed your changes (creating the new partition) and wrote them to the disk.

In so doing you overwrote your old partitions on sda, deleting both your Ubuntu and windows installs..

---

### Post by ndakota on 2012-06-29
> In so doing you overwrote your old partitions on sda, deleting both your Ubuntu and windows installs..what ?? you mean.. I've deleted my both OS. what about the data/my documents on drives? I haven't even backed up some of the data.. please don't tell me everything is gone. Isn't there anyway to recover ??

---

### Post by Mark Phelps on 2012-06-29
Maybe ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by ndakota on 2012-06-30
thanks guys for the replies.. problem solved.
windows disk check deleted everything.. so its a brand new lappy, except for the full 400 GB of HD movies and games.

---

### Post by southerngeek on 2012-06-30
> **ndakota said:**
> thanks guys for the replies.. problem solved.
windows disk check deleted everything.. so its a brand new lappy, except for the full 400 GB of HD movies and games.

Glad your data seems to have been fine! Please mark the thread as solved if your problem has been fixed.

---

