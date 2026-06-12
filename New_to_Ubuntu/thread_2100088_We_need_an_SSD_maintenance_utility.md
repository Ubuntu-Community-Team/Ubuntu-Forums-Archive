---
title: "We need an SSD maintenance utility"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by gonzo74405 on 2012-12-31
I have installed Ubuntu 12.10 on a solid state disk on my desktop computer.
   I know SSDs need periodic maintenance to keep their performance up to their full capability, since I ported Windows 7 to an SSD I installed in my laptop and I use the Intel utility to keep the drive cleaned/trimmed/happy or whatever you call it. 
   I tried to find out how to do this for my Ubuntu drive but frankly I am not sufficiently experienced in programming to understand and implement the fixes suggested in the forums. I know that the respondents think their answers are helpful but they're just too far above my user level to help. 
   If Ubuntu wants to appeal to a larger user community, I think this will become a problem area in the future. I always recommend Ubuntu to my friends but I really don't want to have to add a 'but it's not really easy to use it with an SSD'.
   Can't we develop an SSD cleanup/tuneup utility program that could be downloaded from the Ubuntu Software Center and used by those of us with low levels of technical expertise? Sure would be helpful to me.

---

### Post by sudodus on 2012-12-31
I think it is a good idea. But the development guys don't spend much time at the Ubuntu Forums. Maybe you have better luck publishing your idea at

[[COLOR="Red"]http://brainstorm.ubuntu.com/[/COLOR]]("http://brainstorm.ubuntu.com/")

---

### Post by haqking on 2012-12-31
> **gonzo74405 said:**
> I have installed Ubuntu 12.10 on a solid state disk on my desktop computer.
   I know SSDs need periodic maintenance to keep their performance up to their full capability, since I ported Windows 7 to an SSD I installed in my laptop and I use the Intel utility to keep the drive cleaned/trimmed/happy or whatever you call it. 
   I tried to find out how to do this for my Ubuntu drive but frankly I am not sufficiently experienced in programming to understand and implement the fixes suggested in the forums. I know that the respondents think their answers are helpful but they're just too far above my user level to help. 
   If Ubuntu wants to appeal to a larger user community, I think this will become a problem area in the future. I always recommend Ubuntu to my friends but I really don't want to have to add a 'but it's not really easy to use it with an SSD'.
   Can't we develop an SSD cleanup/tuneup utility program that could be downloaded from the Ubuntu Software Center and used by those of us with low levels of technical expertise? Sure would be helpful to me.

if you are using Linux then it will be using Ext3 or 4 or other Linux Filesystem which does not need maintenance like windows does using NTFS, no defragmention is really needed.

As long as you set up your FSTAB to enable TRIM and the like then there is nothing really to do.  it only take a few seconds to enter the entries into /etc/fstab and then you pretty good to go.

---

### Post by sudodus on 2012-12-31
> **haqking said:**
> if you are using Linux then it will be using Ext3 or 4 or other Linux Filesystem which does not need maintenance like windows does using NTFS, no defragmention is really needed.

As long as you set up your FSTAB to enable TRIM and the like then there is nothing really to do.  it only take a few seconds to enter the entries into /etc/fstab and then you pretty good to go.
Please explain with an example!

---

### Post by Cheesemill on 2012-12-31
Edit your /etc/fstab file using the following command:
```
gksudo gedit /etc/fstab
```And add the discard option to any partitions that live on your SSD, mine looks like this:
```
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>            <type>    <options>          <dump>  <pass>
LABEL=arch-root        /                ext4      discard,noatime    0       1
LABEL=arch-home        /home            ext4      discard,noatime    0       2
LABEL=data             /mnt/data        ext4      defaults           0       2
LABEL=emulation        /mnt/emulation   ext4      defaults           0       0
```Adding noatime as well will reduce the number of writes to the SSD.

---

### Post by haqking on 2012-12-31
> **sudodus said:**
> Please explain with an example!

In addition to cheesemill ninja'in me above.

[http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm](http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm)

[http://wiki.freeswitch.org/wiki/SSD_Tuning_for_Linux](http://wiki.freeswitch.org/wiki/SSD_Tuning_for_Linux)

an example from my fstab
```
UUID=de961735-1d84-4c72-8abe-fefa7b03a708 /SSD2DATA       ext4    defaults,noatime,discard,errors=remount-ro
```I also place /tmp in ram
```
# Place tmp into ram
tmpfs       /tmp        tmpfs       defaults,mode=1777      0   0
```

Along with a few other options

---

### Post by pompel9 on 2012-12-31
I have had a SSD disk for about 6 months now. I have not noticed any slow down or lack of performance. It is just as fast as when I bought it.

My PC is on 24 hours a day, and is only restarted when a update requires it. My SSD is formated in ext4 format.

[Cheesemill]("http://ubuntuforums.org/member.php?u=559258"), what does discard do?
I haven't done any of this, so will my SSD have a shorter lifespan?

---

### Post by Penguinnerd on 2012-12-31
I don't use ubuntu anymore (switched to debian) I have recently figured out this stuff for myself.
Here's my understanding:

TRIM is just a fancy set of rules that the PC will use when you write and erase data. It sounds harder than it actually is. There's a file called /etc/fstab that controls the way your system uses different partitions and you need to change a line of text in that file with a text editor like "gedit" or "nano".

Go to youtube if you want some examples of how trim actually works. Basically, it's nicer about how it erases stuff, minimizing the number of writes to the drive. I recommend it for anyone with an ssd.

Just do what cheesemill said. If you're not sure, just post the text from your /etc/fstab and we can show you what changes to make. Yours might look different from cheesemill's one. 

/etc/fstab it very important, so you might want to back it up first with "sudo cp /etc/fstab ~/fstab-backup" in case of mistakes.

I hope you can find what you are looking for, I fully agree that there should be a graphical utility for this in Ubuntu. Admittedly, such problems are what got me enough hands-on experience that I've come to prefer debian even though it's like that all the time.


EDIT: pompel9. I recommend enabling trim. SSD drives have a limited number of writes before they wear out. Also, because modern operating systems keep lots of log files that are updated constantly, I do not recommend leaving it on continuously. This constant writing means that it wears out your PC even when its idling. But, the fast startup time makes it more convenient to just turn it on when you need it. It also saves electricity, lol.

---

### Post by sudodus on 2012-12-31
Thank you :-)

I found the following text about discard in ```
man mount
```

```

discard/nodiscard
       Controls whether ext4 should issue discard/TRIM commands to  the  underlying
       block  device  when  blocks  are  freed.  This is useful for SSD devices and
       sparse/thinly-provisioned LUNs, but it is off by  default  until  sufficient
       testing has been done.

```

---

### Post by pompel9 on 2012-12-31
Thank you for the information [sudodus]("http://ubuntuforums.org/member.php?u=1499021").

I think I will not use that until they have completed the testing. I do not want to damage my SSD.

---

### Post by pqwoerituytrueiwoq on 2012-12-31
> **pompel9 said:**
> I have had a SSD disk for about 6 months now. I have not noticed any slow down or lack of performance. It is just as fast as when I bought it.

My PC is on 24 hours a day, and is only restarted when a update requires it. My SSD is formated in ext4 format.

[Cheesemill]("http://ubuntuforums.org/member.php?u=559258"), what does discard do?
I haven't done any of this, so will my SSD have a shorter lifespan?
are you using AHCI in your BIOS on your sata adapter?
this is required for trim to work

discard=trim
noatime extends the life of the ssd by not writing a timestamp every-time a file is accessed

---

### Post by Penguinnerd on 2012-12-31
Pompel9, 
TRIM is fairly tested at this point. please look at the edit in my prior post. 

Really, it's only disabled by default so users are aware that it is being used on their system, not because it's dangerous. It's not the kind of thing that will damage an ssd. Worst case, it could corrupt data but I've never even heard of that happening. On the other hand, keeping trim disabled and leaving your PC on for 24 hours per day is exactly the sort of thing that damages ssd's.

And yes, pqwoerituy... is right, AHCI must be enabled in bios for trim to work.

---

### Post by Pjotr123 on 2012-12-31
You might find my how-to for SSD's in Ubuntu useful:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

TRIM is essential, and no bother at all. Especially when TRIM is only applied during mounting (in the course of booting), it's hardly noticeable (slows booting down by just a few seconds).

---

### Post by pompel9 on 2013-01-01
> **pqwoerituytrueiwoq said:**
> are you using AHCI in your BIOS on your sata adapter?
this is required for trim to work

discard=trim
noatime extends the life of the ssd by not writing a timestamp every-time a file is accessed

If it's not default, then no. I haven't changed anything in bios. As long as bios works, it's best not to mess with it. You have to know exactly what you do when you alter the bios.

I know, it's probably just a setting. But I rather not, since doing something wrong can brick my motherboard.

So until there is a safe way, I take my chances on my deafult setup.

---

### Post by Pjotr123 on 2013-01-01
> **pompel9 said:**
> If it's not default, then no. I haven't changed anything in bios. As long as bios works, it's best not to mess with it. You have to know exactly what you do when you alter the bios.

I know, it's probably just a setting. But I rather not, since doing something wrong can brick my motherboard.

So until there is a safe way, I take my chances on my deafult setup.

Rest assured, changing *a setting* in the BIOS, could *never* brick your motherboard (with the possible exception of overclocking, but that's not the case here). Absolutely, definitely impossible. Whatever gave you that idea? :shock:

Would be a bit silly otherwise, right? A manufacturer selling a motherboard that would be bricked *by changing a bloody setting* that he put in it in the first place? :biggrin:

---

### Post by Paqman on 2013-01-01
> **pompel9 said:**
> Thank you for the information [sudodus]("http://ubuntuforums.org/member.php?u=1499021").

I think I will not use that until they have completed the testing. I do not want to damage my SSD.

TRIM is absolutely fine. I've been using it for a couple of years now, as have countless other Linux users with SSDs. 

Go ahead and enable it, you need it to keep your SSD in top condition.

---

### Post by Cheesemill on 2013-01-01
Also the TRIM command that gets sent to the disk is exactly the same command it would get sent by Windows, and TRIM is automatically switched on for all SSD's by default in Windows.

---

### Post by sudodus on 2013-01-01
Yesterday (last year) I added the

[FONT="Courier New"][SIZE="3"]discard,noatime[/SIZE][/FONT]

options to my line for the ssd root partition in /etc/fstab. I see no reason to hesitate, on the contrary. I would have done it earlier last year ;-) if I had known about it.

Actually, I used noatime before, but discard is new to me.

---

### Post by haqking on 2013-01-01
> **sudodus said:**
> Yesterday (last year) I added the

[FONT=Courier New][SIZE=3]discard,noatime[/SIZE][/FONT]

options to my line for the ssd root partition in /etc/fstab. I see no reason to hesitate, on the contrary. I would have done it earlier last year ;-) if I had known about it.

Actually, I used noatime before, but discard is new to me.

discard = TRIM

---

### Post by sudodus on 2013-01-01
What about discard=TRIM on an installed portable system on a USB pendrive? Will it make the system significantly slower?

I mean installed as if to an internal drive, not a persistent system, but would be happy to get recommendations for both kinds of systems.

---

### Post by audiomick on 2013-01-01
I posted something about SSD endurance here. I am not intending to contradict anything in this thread, in fact I will be bookmarking it because it has collected info on a number of things I was intending to look up and use. I just wish to add a little perspective to the idea that an SSD might wear out through normal use.

[http://openubuntu.com/index.php/topic,2414.msg87847.html#msg87847]("http://openubuntu.com/index.php/topic,2414.msg87847.html#msg87847")

---

### Post by Paqman on 2013-01-01
> **sudodus said:**
> What about discard=TRIM on an installed portable system on a USB pendrive? Will it make the system significantly slower?


That won't do anything. TRIM is an ATA command sent from the OS to the drive's on-board electronics. The drive itself does a fair bit of self-management (such as cleanup and wear-levelling), they're quite clever beasties these days.

USB flash drives lack all these sorts of things. Issuing a TRIM command to them won't do anything.

By way of analogy a proper SSD is a bit like a high-tech storehouse with it's own fleet of forklifts and in-house inventory system, that you only interact with through a hatch in the wall. The OS requests boxes to come in and out of storage, but doesn't play any part in where or how they're actually stored. Using TRIM would be like stapling a note to every box saying "clean up after moving this box", which the gnomes in the warehouse obey.

A USB stick is more like a simple set of shelves that you can put boxes on yourself. You can stick as many notes saying "clean up" as you like to the boxes, but there's no one there to do it for you.

---

### Post by Cheesemill on 2013-01-01
> **Paqman said:**
> By way of analogy a proper SSD is a bit like a high-tech storehouse with it's own fleet of forklifts and in-house inventory system, that you only interact with through a hatch in the wall. The OS requests boxes to come in and out of storage, but doesn't play any part in where or how they're actually stored. Using TRIM would be like stapling a note to every box saying "clean up after moving this box", which the gnomes in the warehouse obey.

A USB stick is more like a simple set of shelves that you can put boxes on yourself. You can stick as many notes saying "clean up" as you like to the boxes, but there's no one there to do it for you.
Brilliant analogy :)

---

### Post by sudodus on 2013-01-01
> **Paqman said:**
> That won't do anything. TRIM is an ATA command sent from the OS to the drive's on-board electronics. The drive itself does a fair bit of self-management (such as cleanup and wear-levelling), they're quite clever beasties these days.

USB flash drives lack all these sorts of things. Issuing a TRIM command to them won't do anything.

By way of analogy a proper SSD is a bit like a high-tech storehouse with it's own fleet of forklifts and in-house inventory system, that you only interact with through a hatch in the wall. The OS requests boxes to come in and out of storage, but doesn't play any part in where or how they're actually stored. Using TRIM would be like stapling a note to every box saying "clean up after moving this box", which the gnomes in the warehouse obey.

A USB stick is more like a simple set of shelves that you can put boxes on yourself. You can stick as many notes saying "clean up" as you like to the boxes, but there's no one there to do it for you.
Thank you for the good description :-)

---

