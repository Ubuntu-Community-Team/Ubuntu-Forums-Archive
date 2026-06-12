---
title: "(gived up)device order changed after boot up"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by lou2 on 2013-10-02
Hi, first time post, not sure if I'm at the right section.

I got a laptop with one storage, which I replaced it with a ssd.
then I installed both ubuntu 12.04 and windows7, 
one day I found my disk space not enough, so I replace my cd-rom with a hdd, and it work well as usuall.
then sometimes later I can't boot.

I used window repair disk and I can boot into Windows.
I've checked my bios, it's not detecting my ssd (even if I switch the ssd to the cdrom slot and put the hdd into the original slot)
but I can use both ssd and hdd well in Windows(weird?)

then I reconstruct my MBR in hdd and installed grub2, then configured, but I still can't get into ubuntu.
after days of troubleshooting I think I found the problem:
my device number changed during the boot.
during boot( which I verified with Grub2 command line):my ssd is(hd1), hdd is (hd0); 
but then it changes sometimes later( I don't know in which stage it changes): ssd become (hd0), hdd become(hd1)

I've edited and changed the entry of ubuntu in grub 2 menu, and set root to hd1(and tried hd0, too)
no matter I set it's root to hd0 or hd1 it only loads the initrd and go into the a command prompt of initrd.
I don't know why it just can't load the kernel.......I can't read the messages cuz I don't know how to scroll up....


Pretty complicated, hope someone can help me...
I've been troubleshooting it for few weeks and finnally decided to ask...

---

### Post by whitesmith on 2013-10-02
Hi** lou2** and welcome! Please boot from an active Unbuntu CD/DVD. Select try instead of install. After the dust settles open a terminal (ctrl+alt+t) and enter this command:```
sudo fdisk -l
```Post the result here so we can see what's going on.

---

### Post by lou2 on 2013-10-02
hi, thx for reply
I forgot to metion that in order to install grub on boot drive, I installed a ubuntu on that drive, too
dev/sda3/ : my windows 7 installation
dev/sda4/ : data drive for windows
dev/sda6/ : ubuntu 12.04 installation
dev/sdb7/ : ubuntu 13.04 installation(not important, will format it if the problem is solved)
dev/sdb3/ : data drive for ubuntu 12.04(which I formated and mounted for ubuntu 12.04  at the time it still worked)
other ntfs partition on sdb is for data storage of windows 7


```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd21767a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    35096575    17547264   27  Hidden NTFS WinRE
/dev/sda2        35096576    35151871       27648    7  HPFS/NTFS/exFAT
/dev/sda3   *    35151872   146303954    55576041+   7  HPFS/NTFS/exFAT
/dev/sda4       146320017   234440703    44060343+   f  W95 Ext'd (LBA)
/dev/sda5       146320080   207816839    30748380    7  HPFS/NTFS/exFAT
/dev/sda6       207818752   226371583     9276416   83  Linux
/dev/sda7       226385920   234440703     4027392   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x566b9230

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    37750783    18874368   27  Hidden NTFS WinRE
/dev/sdb2   *    37750784    37955583      102400    7  HPFS/NTFS/exFAT
/dev/sdb3        38186552   976768064   469290756+   f  W95 Ext'd (LBA)
/dev/sdb5        38186554   425449394   193631420+   7  HPFS/NTFS/exFAT
Partition 5 does not start on physical sector boundary.
/dev/sdb6       507364893   976768064   234701586    7  HPFS/NTFS/exFAT
Partition 6 does not start on physical sector boundary.
/dev/sdb7       425449472   507363327    40956928   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 4043 MB, 4043308544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7897086     3948512    c  W95 FAT32 (LBA)
```

---

### Post by whitesmith on 2013-10-02
The bootable partitions on your system are /dev/sda3, /dev/sdb2 and /dev/sdc1. This is at variance with your intentions. I think running the boot-repair disk might help untangle the mess. You only need 2 bootable partitions: one for Windows and one for Ubuntu. If boot-repair doesn't fix the problem, write down the URL it gives you when it finishes. It will take this form: paste.ubuntu.com/xxxxxxxx. Post that in this thread. You can also email the same URL to [email]boot.repair@gmail.com[/email] with an explanation of the problem. Dual-booting Ubuntu/Windows is normally pretty reliable, but it can quickly go south into deep water. That seems to be what happened here. Don't give up!

---

### Post by DuckHook on 2013-10-02
Before doing anything else, back up your critical data *right now*. If you do not have Win7 OS installation disks, create them *right now*. Do not make any further changes to your system until you are absolutely confident that you have made all provisions and completely shielded yourself against catastrophe. I trust that you took these steps before adding your new drive. If not, you were lighting matches in a room filled with gasoline.

I am out of my depth firstly with Win7 and secondly with the complexity of both your drives, but I assume that you are using Win 7's Dynamic Disk? All I know is that this forum used to be filled with issues from trying to install Ubuntu onto Win 7 Dynamic Disks. Most solutions involved converting the dynamic disk back to a basic disk before anything would behave. **NOTE** This *used* to be a big issue, but I haven't seen anything like it for a long time, so perhaps Ubuntu has found a way to live with Dynamic Disks in the newest versions. I sure hope *oldfred* sees this thread and gives you the benefit of his knowledge. [This]("http://ubuntuforums.org/showthread.php?t=1705481") is a very old thread I found dealing with the matter. **WARNING** It is meant only as food for thought because it may be completely obsolete. My recommendation is to not do anything further until other posters--more knowledgeable than me--can give you solid feedback and instructions.

---

### Post by whitesmith on 2013-10-02
I totally concur with **DuckHook**. Backing up is so important I give it top billing in my signature line. The site I mention next is intended to inform the unwary that Linux isn't "free Windows," or anything of the kind. Changing OSes is a serious step that deserves careful--and enlightened--attention before anything further is done. "Jump right in" rarely works with matters as complex as this...even though the new OS is both free and enormously feature-rich compared to poor old Windows.

---

### Post by DuckHook on 2013-10-02
:lolflag: ...we are legion!

---

### Post by lou2 on 2013-10-03
thx for reply
I've run the boot repair from live usb
it seems to have reinstalled my grub and the new menu have lots more entrys...
but I still can get into my ubuntu 12.04.(It's on the menu)
when I select that entry, it loads into the initrd command line ...

[http://paste.ubuntu.com/6187479/](http://paste.ubuntu.com/6187479/)

---

### Post by heir4c on 2013-10-03
How you made your partitions? Because I see this:
/dev/sdb4         146,320,017   234,440,703    88,120,687   f W95 Extended (LBA)
and:
/dev/sdc3          38,186,552   976,768,064   938,581,513   f W95 Extended (LBA)

Your extended partitions are not from Linux. Normally it's just say: 5 Extended ,and not: f W95 Extended (LBA)
Your boot-repair log rapport of that. 
So maybe there is the problem?
Somebody with more experience with that? ...

---

### Post by lou2 on 2013-10-03
hi, heir4c
I'm not sure how the partiontion was made....
but I didn't make those partition.
And it start from almost the same sector of the other partition( ie.[COLOR=#000000]/dev/sdb4         146,320,017,[/COLOR][COLOR=#000000]/dev/sdb5         146,320,080)
maybe it's automatically generated?

[/COLOR]

---

### Post by heir4c on 2013-10-03
No, it can't be automatic. You must do that by hand in the install procedure. 
I think, you can't change it without reinstall. 
For that reason I ask for help from someone more experienced with this specific issue.
So, we wait and be patient :)

---

### Post by lou2 on 2013-10-03
but what's on that partition?
why can two partition have same parts of sectors?
like if sector 1~5 is for partition 1, then partition 2 must start from 6, right?

thx for your help~~

---------------update--------------
I just boot into my ubuntu 12.04 by selecting the second entry(which named by its kernel version)
but after I reboot is shows " low-graphic mode" error...
I've searched for answer but all the solutions requires entering command line( I pressed Ctrl+Shift+F1, then system freezed)

seems like I got another problem........

---

### Post by heir4c on 2013-10-03
No, normally you can have only 4 partitions on a Hard Disk.
But with de extended function you can add more partitions.
Normal partitions are Primary partitions.
In the Extended partition you have the Logic partitions.
The Extended partition on his self is nothing, you can't use that for anything. You can't boot from the Extended and you can't inside or mounted the partition. It's just a name for the Partitions inside. (The extended partition is the sum of the logic partitions)

So, normally when you create 4 partitions you have this:
sda1 Primary partition
sda2    "            "
sda3    "            "
sda4    "            "


But when you create 1 primary partitions and 3 Logic partitions you have this:
sda1 Primary partition
sda2 Extended partition  
           ----sda5  Logic partition 
           ----sda6  Logic partition 
           ----sda7  Logic partition

the numbers in the extended partition begin automatic from 5 (always)

See the image (the orange partition is the extended, the 2 Logic partitions below are IN the extended partition):
[IMG]http://i.imgur.com/g1AjzGE.png[/IMG]

---

### Post by lou2 on 2013-10-03
wow, I see...
thx for the lesson :)
I think I've learned much more than expected from troubleshooting the boot up issue.

btw, may I ask what limits the number of partitions on a harddisk to 4?

---

### Post by heir4c on 2013-10-03
Oo, now you asking me something ...  :D 
It's something to do with the MBR. (I am not a expert on that so.....) In the past the MBR was small (even so the Hard Disks) and the info that was stored in the MBR limited it to info of 4 partitions. But now you can at more partitions with the trick of the Extended partition (that is 1 of the 4 primary partitions) But it's to technical for me at the moment to explain that in English (I am Dutch speaking) So, maybe somebody else can explain it better or look for it via google.

---

### Post by heir4c on 2013-10-03
> **lou2 said:**
> 
I think I've learned much more than expected from troubleshooting the boot up issue.


So do I. Every time I help somebody I learn even more. So that's one of the reasons I help people. I look for the error or the problem with Google and read 10 or more links. When I understand what and how, I write it down and try to be complete but so simple as possible. And with images/screenshots. Because, when you see what I see you understand it better. Like in my post above.
(Normally I help on the Dutch Ubuntu forum.)

---

### Post by DuckHook on 2013-10-03
> **lou2 said:**
> I'm not sure how the partiontion was made....
but I didn't make those partition.Your extra partitions in fact were made by you, although you may not have known that you were doing so. When you asked Win 7 to make partitions for you, it defaults into creating "Dynamic Disks" instead of basic disk and that is what you have in your disk right now. As I mentioned in my first post, Dynamic Disks are a crazy Windows-specific way of making logical block addressed (LBA) partitions and these don't play nicely with anything but Windows. In particular, Ubuntu has nothing but trouble with them, which is why you can't seem to get it running right now. Ubuntu installs, but only into one of these crazy LBA partitions, and then GRUB can't make heads or tails out of finding where it is. This is why I linked you to the other thread that deals with solving this issue (although it is 2-years old).

I don't run Win7 so am advising you second-hand. You need to know that.

Did you take the precautions I recommended? Have you backed up your data to an outside media? Have you created your Win 7 install disks?

---

### Post by heir4c on 2013-10-03
ThanX DuckHook for this, I must better read the posts in the treads.
I never heard of the Dynamic Disks, so today I learned a lot. ThanX!!!

---

### Post by DuckHook on 2013-10-03
> **heir4c said:**
> ...I must better read the posts in the treads.> **DuckHook said:**
> Did you take the precautions I recommended? Have you backed up your data to an outside media? Have you created your Win 7 install disks????!

---

### Post by heir4c on 2013-10-03
> ???! 
It's about your first post. I don't read all of that, I moved to fast in this tread not paying attention to all of the posting. 
(Dutch speaking and slow with writing English)

---

### Post by DuckHook on 2013-10-03
You misunderstand. I greatly respect people like you who post on these forums despite the fact that your first language is not English. I would find it impossible to post on a Dutch forum asking for help. So you have my admiration. I was asking about whether you followed my advice to back up and make Win 7 install disks.

---

### Post by heir4c on 2013-10-03
DuckHook, that is also a misunderstand. I am not the one who started the tread and need help but lou2 is. :) 

Beside that, My English is good for reading (I understand not everything) but writing (sentence structure (if this is the right words I use, I search for it with Google)) is a little bit difficult. 
It's normal that you can't post on a Dutch forum in Dutch but English is a Universal language (Film, TV, e.d.) and computer tutorials are most of the time in English. So we learned on TV the English language and now that is a + for me. 
But I use also Google to translate some words or look for the right spelling. That's not always easy. So, I do my best, but it's a little bit slow when I respond on a tread and sometimes I am to late. :D

---

### Post by DuckHook on 2013-10-03
> **heir4c said:**
> ...not the one who started the tread and need help but lou2 is...<Sigh> My brain is clearly going to pot. Sorry for the confusion and thanks for your understanding and clarification.

---

### Post by JKyleOKC on 2013-10-03
> **lou2 said:**
> wow, I see...
thx for the lesson :)
I think I've learned much more than expected from troubleshooting the boot up issue.

[COLOR="#0000FF"]btw, may I ask what limits the number of partitions on a harddisk to 4[/COLOR]?The 4-partition limit is a relic of the very old days, when IBM introduced its first PC in 1981. It rapidly became the "standard" system for industry and ever since, "PC compatibility" has been a major driving force.

To boot the system requires much more code than the Read-Only Memory chips available 32 years ago could provide. They were being stretched to provide even 1,024 bytes -- and that's not nearly enough to contain a full operating system. For that reason, IBM's system architects devised a process that began with a very basic program contained in the ROM, that had just enough ability to load the system itself from floppy disks.

When hard disks came along a few years later, they required much bigger operating system programs, beyond the capacity of floppy disks. Some of them required as many as a dozen floppies for installing them! That was clearly impractical for daily use, so the procedure got modified again. The ROM code now loads a tiny boot loader program that's contained in the disk's Master Boot Record, which is the first 512 bytes of the first track, into memory. It then transfers control to that program, which in turn loads an abbreviated copy of the operating system. When that's fully loaded, it in turn loads the rest of the system. Both Windows and Linux follow this same approach, although their details differ quite a bit.

The 512-byte size of the MBR is what puts a hard limit on the number of partitions. The boot loader program occupies about 400 bytes; 64 bytes of the rest becomes the Primary Partition Table, consisting of four 16-byte entries that provide the starting and ending addresses for each partition.

As disk sizes increased from the original 5 MB of IBM's XT machine, more partitions were needed, but no more space was available. That's when the "extended partition" was invented. It serves as a container for the "logical partitions" needed, so its addresses seem to duplicate theirs or at least include them.

Once disk sizes passed the 1-TiB mark, the MBR system ran into problems, so a new and totally different system is coming into use. It's called GPT and does not have the 4-primary limit; my lone GPT-based system provides for 128 primary partitions. This technique began hitting the mainstream with Windows 7 and just about all Win8 systems seem to use GPT partitioning -- which causes loads of confusion since much of the information you find on the web actually refers only to the MBR approach, and isn't applicable to GPT systems, but never says as much! This, however, is a bit off topic for this thread.

Hope this helps answer at least one of your questions...

---

### Post by lou2 on 2013-10-05
Yes, I've already backed up. And most of my data is on Dropbox, the rest is not that important....
So what should I do next?
I've found the entry that leads to the right root of my ubuntu partition, but I can get in. (low graphic mode..., and I cannot enter command line mode, it just freezes)

[COLOR=#000000]thx for the explaination, JKyleOKC, it's just like taking history class[/COLOR]:D


BTW, I not a native english speaker, too. So bear with my broken english....(I speak chinese)

---

### Post by lou2 on 2013-10-06
Thx those who replied and help :)
since the semester already started and I got a lots of homeworks to do, I give up.....
decided to format all the old ubuntus and install a new one.
Learned a lot anyway :)

I really appreciate your help :)
u might have prevent some super star in IT industry from giving up due to minor issue like can't install a ubuntu os on his computer....

---

### Post by heir4c on 2013-10-06
@lou2, ok, and if you want go further with this, come back and bump this thread up and we can go on with your problems.

---

