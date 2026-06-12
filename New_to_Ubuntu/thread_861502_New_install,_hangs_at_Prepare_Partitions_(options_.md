---
title: "New install, hangs at Prepare Partitions (options greyed out)"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Schamess on 2008-07-16
I have an old Dell desktop (Intel Pentium 4 )that was discarded by a friend's college.  It had been running Windows but when I got it they must have wiped the OS - would not boot beyond the initial "press F1 to re-try" screen.  I have no Linux experience but have been interested and thought this would be a good opportunity to try it out.  Made iso disc. etc.  So here's the problem:

I am going through the install interface that comes up when I boot from the live CD.  Chose English as language, chose time zone and keyboard layot.  Then I get to Step 4, "prepare partitions".  Here, it just hangs.  I see a window with column headers that say Device, Type, Mount point, Format?, Size and Used.  Underneath them is a blank screen, not writable.  Beneath that are buttons that say "new partition table", "new partition" and other partition options but they are greyed out, cannot be clicked.  

When I press the "forward" button it says "No root file system is defined.  Please correct this from the partitioning menu."

Any suggestions?

I know very little about the machine, though I did open it up and make sure it had a hard drive (it does).  I ran a memory check from the Linux disc and it seems to have reasonable RAM, cache memory etc.

Note: I'm not particularly computer saavy so I would be grateful for "beginner-level" answers or suggestions.  I do not need a dual boot or any thing, perfectly happy to format the hard drive and start from scratch if someone can tell me how to do this.

Thank you very much!

---

### Post by arochester on 2008-07-16
There are two different install disks. The Desktop disk is a LiveCD and needs a lot of RAM  to install. The Alternate Install disk is a straight install disk and uses a lot less RAM to install.

Do you know how much RAM you have? You might be better with the Alternate Install Disk.

---

### Post by appi2012 on 2008-07-16
Not the answer to what your problem really is

---

### Post by appi2012 on 2008-07-16
Don't mind my previous post - I didn't read the body of your post (just the title). What you should do is choose the "guided - use entire disk option" not manual, which is what I think you did.

---

### Post by avtolle on 2008-07-16
Reading the first post, it almost seems the drive was mounted or, alternatively, not being recognized (although if it wasn't recognized, I'd not think the partitioner would have shown what it did). Otherwise, the questions about RAM are appropriate.

---

### Post by Schamess on 2008-07-16
First of all, thanks for both replies.  It has 196 MB of RAM.  

I fooled around a bit with the BIOS - I found one that says OS Install Mode and switched it from off to on.  This did have the interesting effect of reducing the available memory to something like 256 kb.  Not suprisingly, when I tried the install again, the CD spun around vigorously, without anything happening on the screen, and I finally had to boot down manually.

So I am downloading the alternate installer to see if that would work with the OS Install Mode on.

Meanwhile, I have turned OS Install mode off and I am back to the Ubuntu start screen.  My options are:

-Try Ubuntu without any change to your computer
-Install Ubuntu
-Check CD for defects (did this, no defects)
-Test memory (did this, seems adequate)
-Boot from first hard disc (didn't work)

Alternative modes when I pres F4:
-Normal
-Safe graphics mode
-Use driver update CD
-OEM install (for manufacturers)

So I am not sure how to access the Guided option...?

Again, I really appreciate the help and any further suggestions.

---

### Post by sarc on 2008-07-16
I had many cases of hanging during install due to POOR QUALITY CD MEDIA.  The CD was new, but of the cheap sort.  When I burn the disk on good quality CDs I don't get hangs.  Happened to me several times.

---

### Post by ubume2 on 2008-07-16
Try Ubuntu without any changes. When the desktop comes up you will have an opportunity to install.  You can also play around with Ubuntu before installing, just to see whether you and Hardy, and the machine is a fit.

I wonder if your RAM is slightly insufficient for 8.04, though.

---

### Post by Schamess on 2008-07-16
Thanks, I did check the CD for errors and it is fine.  I tried installing from the desktop and get the same problem.  It can't seem to partition the hard drive.

---

### Post by seagullplayer77 on 2008-07-16
Just a wild idea: if they wiped out the hard drive, perhaps they wiped out the existing partition table as well? Maybe you could try making a new partition table when Ubuntu gives you the option, and then try to partition. I don't know if that's the problem at all, but it's just a guess. 

I suppose the other thing you could do is download an ISO of the Ultimate Boot CD (just Google "UBCD" and find the free download) and mess around with that for a little while. Good luck!

---

### Post by ubume2 on 2008-07-17
If you haven't already tried this:

From Live CD try System>>Administration>>Partition or Gparted and set up a partition that way.You need to set up one partition as ext3 and another as swap. After you set it up click apply. And then exit the partitioner and click the install button on the desktop.

In install you can set up the root, etc, with the "ubiquity" partitioner.  And hopefully, the grayed out area, won't be grayed out anymore.

Actually, the other method should have worked, but I recall I had similar problems.

---

### Post by Schamess on 2008-07-17
Aha, that sounds promising.  I just need to finish seeing patients today and I will try some of the above suggestions, and report back.   

For now: Thanks very much to all!

---

### Post by avtolle on 2008-07-17
You have indicated that the computer has 192 mb RAM. Be apprised the Live CD requires 384 mb RAM to install, due to the graphical installer; Ubuntu will run on 256 mb RAM, and thus the alternate installer (text based) will also run on 256 mb RAM. I think that given the small amount of RAM, you will encounter difficulties with any attempt to install, including partitioning, from a Ubuntu install disk, regardless of which one you are using.

EDIT: Even though [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) has some age on it, I'd encourage your reading of the same to give you some ideas.

---

### Post by Schamess on 2008-07-18
"From Live CD try System>>Administration>>Partition or Gparted and set up a partition that way."

From Administration I opened Partition Editor, it opens a GParted window - but at the bottom of the screen I get a message "No devices detected" - and the buttons are again greyed out.

Re RAM - the live CD seems to be running OK, maybe a little slow - but it loads applications adequately. I'm hesitant to drive out to Best Buy and get more RAM unless it would really help.  I have the feeling something is blocking the installer from finding the hard drive...?  Would this really be a RAM problem?

---

### Post by ubume2 on 2008-07-18
> **Schamess said:**
> 

Re RAM - the live CD seems to be running OK, maybe a little slow - but it loads applications adequately. I'm hesitant to drive out to Best Buy and get more RAM unless it would really help.  I have the feeling something is blocking the installer from finding the hard drive...?  Would this really be a RAM problem?

I think your problem may be over my head.

Have you checked the bios settings?

You may have the same problem if you tried something like Parted Magic, which is only about 50MB in size. I've had better luck with Parted over gparted.

If you succeed in getting the HD partitioned, I would consider a lighter distro such as Xubuntu.  It requires less memory than Hardy.

---

### Post by romitm on 2009-03-12
Ive had exactly the same issue and experience as the original post.

I'm now logged in via the LiveCD from by CD Drive, and while my computer is not the freshest, it does have at least 1G of RAM.

The Partitions menu and gparted show no devices. 

What are my options now?
Thanks a lot

---

### Post by alexanderbow on 2009-11-03
>  By **Romitm**: 

Ive had exactly the same issue and experience as the original post.
 
 I'm now logged in via the LiveCD from by CD Drive, and while my computer is not the freshest, it does have at least 1G of RAM. 
 Hey Romitm,

     Might I ask if yours would be a Dell as well? I have one of their ugly "DHM" towers and the 9.10 wizard is throwing me the same response. 

     As for its memory, it has 370 MB which is obviously "no bueno" as Avtolle previously said (thank you), but it doesnt seem to be a serious enough factor to cause the dilema at hand. 


          Thanks to all for any strenuous thinking you would have on this.

---

### Post by romitm on 2009-11-03
> **alexanderbow said:**
> Hey Romitm,

     Might I ask if yours would be a Dell as well? I have one of their ugly "DHM" towers and the 9.10 wizard is throwing me the same response. 
.

Hi alexanderbow,

the machine in question was a samsung laptop - quite alright in all respects except the fact that its hard drive degraded over time. 

Incidentally, after I changed the hard drive, this problem went away. Maybe your dell is suffering from a rusty hard drive too?

cheers

---

### Post by alexanderbow on 2009-11-09
I wouldnt doubt it, it seems that 9.10 cant work with older hardware. What a sad state of affairs that I have to stick with XP; first time I've ever seen windows legitimately one-up Linux :-(

---

### Post by lazyastronomer on 2009-11-09
Same story here. I don't remember how much RAM I have, but it is something less than the required. I think it was 226 or something.
I've tested the CD; it seems ok. Did the memory test, and it said that I was ok. What can I do now? Please help me out?

---

### Post by strat1227 on 2009-11-25
hmm, i have a dell with the exact same issue

my best guess is that it's a faulty hard drive, mine's been acting up and if changing it fixed the problem for someone else it probably would for me as well

however if anybody else has any better educated guesses for me to try, i'd definitely appreciate it

thanks in advance

---

### Post by sgusto on 2009-12-05
I'm having the same issue with a new install on the following system;
Gigabyte MA785GM-US2H  (SATA set to AHCI & IDE controller disabled)
3 GB Kingston DDR2-800
Sapphire 5770
LG CD/DVD (SATA)
Seagate 160GB SATA  

During install it won't bring up the partitions -manually or guided. However, GParted, sees them fine and I can do partition work on the drive with it even as the installer sits there stuck. It's the "Prepare Partitions" segment of the installer that fails. Normally you can see a graphic display of detected partitons but the whole display area of the "Prepare Partitions" window is blank and the buttons at the bottom are all greyed out. 

A slipped-streamed XP 32 install went fine on an identical drive the day before with this same system.  (that drive disconnected for Ubuntu install)

I've tried three different tested/passed install disks too - a DVD i386, a CD i386, and a CD amd64. I tried amd64 both from the Live desktop and from the "Install" option from the boot menu. 

I haven't tried changing the BIOS to IDE yet. It seems odd that GParted can edit the disk but not the installer.

---

### Post by arm000 on 2009-12-09
> **sgusto said:**
> 
During install it won't bring up the partitions -manually or guided. However, GParted, sees them fine and I can do partition work on the drive with it even as the installer sits there stuck. It's the "Prepare Partitions" segment of the installer that fails. 
 
Same problem here, AHCI mode seems broken in Ubuntu 9.10. I reverted to 9.04 and everything installs fine.  I'm also able to drop into fdisk and mess with partitions in 9.10, but no matter what I do the installer fails to see any disks.

---

### Post by Ross_and_Eye on 2009-12-11
I am having the same problem as the original Post, I have a Dell PowerEdge 1850 with SCSI RAID I have 2 GIG of RAM in it and 4 more on the table if I thought it would help, I would add it. I am no expert but I do not believe the partition table being grayed out is related to how much RAM is available, My computer is neither old or slow, it is 4 years old and state of the art, Still the partition table remains gray and entering set-up from the installation or from the icon on the desktop makes no difference. I could maybe change from RAID to SCSI in the bios, but I would prefer to use RAID, I look hopefully toward a solution.

---

### Post by NubJub on 2009-12-14
In the alternate install when you are detecting and partitioning drives you can choose to activate serial-ata devices. I have found that on some motherboards, generally using standard intel pata controllers, it is necessary to say NO here to see your partitions.

If anyone knows how to cause a similar affect on a live disk that'd be cool

It seems to me that when you're having a problem with a partitioner RAM should be pretty low on your list of causes. Start with the controller, the bios, then the partition information.

---

### Post by sgusto on 2009-12-16
I gave up on this and installed 9.04, then immediately did an upgrade to 9.1. 

No problems. I guess it's just an installer bug.

---

