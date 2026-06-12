---
title: "hard drive light never stops blinking -- Ubuntu 7.10"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by socref on 2008-06-05
Sorry, don't know where else to post this (and I am new to Ubuntu in any case)...

Ubuntu 7.10 on a Dell Inspiron 530 with 2 GB memory.

The hard drive light never stops blinking. It flashes every second, or second-and-a-half. Even after the computer has sat overnight, powered up but without anything running and also disconnected from the Internet, it still is flashing when I sit down to the computer first thing in the morning.

It's as if the system is indexing or checking for something, but it never stops. Has been this way now for weeks.

What to do, gurus? I don't think it can be good for the HD to be constantly turning and active 24/7/365.

Thanks.
socref

---

### Post by logos34 on 2008-06-05
I had the same problem in Feisty.  Drove me bananas, if only because I could never figure out what it was.  It definitely was not indexing.  Some daemon snuck in there. 

Maybe it's NSA surveillance.  Boo.

---

### Post by FuturePilot on 2008-06-05
Try running 
```
top
```
in a terminal. If a process is thrashing the disk around it's probably using a bit of CPU was well.

> **logos34 said:**
> 
Maybe it's NSA surveillance.  Boo.

:lolflag:

---

### Post by walker9010 on 2008-06-05
See [http://ubuntuforums.org/showthread.php?t=484941]("http://ubuntuforums.org/showthread.php?t=484941")

---

### Post by socref on 2008-06-05
> **FuturePilot said:**
> Try running 
```
top
```
in a terminal. If a process is thrashing the disk around it's probably using a bit of CPU was well.



:lolflag:


Thanks, but I tried that already. Nothing unusual that I can see. 1% CPU, maybe 2%. But nothing running up CPU usage constantly.
socref

---

### Post by socref on 2008-06-05
> **walker9010 said:**
> See [http://ubuntuforums.org/showthread.php?t=484941]("http://ubuntuforums.org/showthread.php?t=484941")

OK, I read that thread. My Dell is a desktop, not a laptop, so unless I am not understanding something the solution at the URL shown above would not help. 

Am I not understanding or should I run that set of laptop commands on my desktop?
Thx
socref

---

### Post by socref on 2008-06-10
Can anyone provide some guidance here? I am really concerned about all the unnecessary wear and tear on the hard drive.
Thxs

Socref

---

### Post by socref on 2008-07-07
Interesting new information on non-stop H/D activity.

This morning I powered-up my computer. When the log-on screen came up, and before I entered my user name, I looked to see if the H/D light was blinking. It was. 

So before I had even logged-on and before I had my desktop on-screen the H/D light was flashing every one or two seconds.

Any ideas? Somebody must have some insight into this non-stop H/D spinning.
Thx
socref

---

### Post by Linux_Man on 2008-07-07
Is your HD light broken possibly? Have you tried booting into a live-CD and when it is finished loading does it still have the light flickering?

---

### Post by Dr Small on 2008-07-07
> **socref said:**
> Interesting new information on non-stop H/D activity.

This morning I powered-up my computer. When the log-on screen came up, and before I entered my user name, I looked to see if the H/D light was blinking. It was. 

So before I had even logged-on and before I had my desktop on-screen the H/D light was flashing every one or two seconds.

Any ideas? Somebody must have some insight into this non-stop H/D spinning.
Thx
socref
That is not surprising in the least. As logos34 stated, it is probably a daemon running.

---

### Post by socref on 2008-07-07
> **Dr Small said:**
> That is not surprising in the least. As logos34 stated, it is probably a daemon running.

OK then:

1) how do I identify it?
2) how do I kill it?

When I look at the process list I don't see anything that jumps out at me. Of course it would help if I knew what to look for...  :lolflag:

Can you help?
Thx
socref

---

### Post by socref on 2008-07-07
> **Linux_Man said:**
> Is your HD light broken possibly? Have you tried booting into a live-CD and when it is finished loading does it still have the light flickering?

OK, I booted to the Live CD and the H/D light still flickers. Does that provide important information for chasing down this problem?

Is there a way to check the integrity of the H/D light? It's a new pooter -- purchased in April.

Thx
socref

---

### Post by sydbat on 2008-07-07
Has this been happening since you first got the computer? If so, it might be the HDD LED is connected to the wrong lead on the motherboard. Also, is there any strange sound coming from the HDD? Like it's working overtime? Or grinding? Any performance issues?

---

### Post by socref on 2008-07-07
> **sydbat said:**
> Has this been happening since you first got the computer? If so, it might be the HDD LED is connected to the wrong lead on the motherboard. Also, is there any strange sound coming from the HDD? Like it's working overtime? Or grinding? Any performance issues?


I cannot say if it has been happening from day one, but I did notice this issue soon after I got the computer (a little more than two months ago). The pooter came with Ubuntu 7.10 loaded, and with a single partition. I partitioned the drive and reinstalled Ubuntu, thereafter adding various items using Synaptic and the add/remove software features. 

I do not hear any noises coming from the pooter. I have not noticed any performance issues, but then this computer is faster than the one it replaced, so I would not recognize if it is under performing.

Thanks!
socref

---

### Post by avtolle on 2008-07-07
Do you have a swap partition on the HDD? It (the computer) might be looking for a swap partition.

---

### Post by fiddledd on 2008-07-07
If you've only had it for a few months then it's the seller's responsibility, not yours, to sort it out. They were more than happy to take your money. I would get in touch with them. I wouldn't think partitioning the Drive would void any warranty.

---

### Post by unutbu on 2008-07-07
I'm not sure if the suggested fix

```
sudo hdparm -B255 /dev/sda
```
 
found on this thread
[http://ubuntuforums.org/showthread.php?t=590042](http://ubuntuforums.org/showthread.php?t=590042)
will work for you, but maybe it's worth a try.

If it doesn't work, please post```

sudo hdparm -cagiI /dev/sda
```

PS. I'm looking at a picture of the Dell 530:
[http://i1.iofferphoto.com/img/item/438/427/11/o_insp_530_300.jpg](http://i1.iofferphoto.com/img/item/438/427/11/o_insp_530_300.jpg)
where is the hard drive light of which you speak?

---

### Post by socref on 2008-07-07
> **avtolle said:**
> Do you have a swap partition on the HDD? It (the computer) might be looking for a swap partition.

Well, that is an interesting question.

I know that I did attempt to include a 2 GB  swap partition when I first installed Ubuntu. But now that you ask, I am not sure that I actually got that partition.

When I open System Monitor and look at the "Resources" tab in the middle graph ("Memory and Swap History") it indicates for "Used swap": "0 bytes of 1.9 GB, 0%." And the line on the graph is flat on the bottom of the graph. So I think (??) this means that 1.9 GB is supposed to be allocated to swap. However...

When I open the "File Systems " tab in System Monitor it shows only two partitions:
/dev/dsa1 which is the / directory and has 9.2 GB total space, and /dev/sda2 which is the /home directory and has 221.6 GB total space. It shows no swap partition.

The "type" for / is set to ext3 and /home is set to jfs.

I have 2 GB memory on this pooter. If, in fact, I have no swap partition, is that necessary, and should I go back and repartition the drive? 

If yes, should I take 2 GB from /home? 

If yes, do I risk the data that's on /home?

Thanks for your help.
socref

---

### Post by avtolle on 2008-07-07
It could be that in setting up the system, Dell elected to use a swap file rather than a swap partition (which is OK, BTW). If you want to resize /home to get a swap partition, you would need to use the Live CD to do so, assuming this will take care of the problem. Back up the files on /home for safety sake, of course, before doing anything with your partitions.

EDIT: Sorry for some erroneous stuff above, as I was confusing your situation with another poster. Did you install 7.10 yourself, or did the computer come with 7.10 already installed?

---

### Post by socref on 2008-07-07
> **avtolle said:**
> It could be that in setting up the system, Dell elected to use a swap file rather than a swap partition (which is OK, BTW). If you want to resize /home to get a swap partition, you would need to use the Live CD to do so, assuming this will take care of the problem. Back up the files on /home for safety sake, of course, before doing anything with your partitions.

EDIT: Sorry for some erroneous stuff above, as I was confusing your situation with another poster. Did you install 7.10 yourself, or did the computer come with 7.10 already installed?

It came from Dell with Ubuntu 7.10 installed. I reinstalled 7.10 when partitioning the drive.

socref

---

### Post by avtolle on 2008-07-07
Just as a bit of a "learned guess", I'd say that when you did your own install of 7.10 (did you use the Dell disks or did you download the iso yourself) that you may have done something with the swap file/swap partition. If that is anywhere near being correct, I'd create a swap partition and see whether that eliminates the problem.

---

### Post by socref on 2008-07-07
> **unutbu said:**
> I'm not sure if the suggested fix

```
sudo hdparm -B255 /dev/sda
```
 
found on this thread
[http://ubuntuforums.org/showthread.php?t=590042](http://ubuntuforums.org/showthread.php?t=590042)
will work for you, but maybe it's worth a try.

If it doesn't work, please post```

sudo hdparm -cagiI /dev/sda
```

PS. I'm looking at a picture of the Dell 530:
[http://i1.iofferphoto.com/img/item/438/427/11/o_insp_530_300.jpg](http://i1.iofferphoto.com/img/item/438/427/11/o_insp_530_300.jpg)
where is the hard drive light of which you speak?


Thanks for suggestion. Some questions: 

1) If I run the command you suggest, what happens? Can I do anything bad to the computer by running that command? If not, should I just run it and see what happens? I worry about doing this as I am not a sophisticated user and don't know enough to recover if the pooter crashes.

2) The thread you pointed me to seemed to describe a hard drive that was spinning up and down (I am guessing that this was noisy and noticable to the user). I do not hear the drive spinning up and down. I only get the flashing H/D activity light.

3) The H/D light is at the bottom of the thin column on the front, at the opposite end from the round power switch which you can see in the picture.

Thx
socref

---

### Post by socref on 2008-07-07
> **avtolle said:**
> Just as a bit of a "learned guess", I'd say that when you did your own install of 7.10 (did you use the Dell disks or did you download the iso yourself) that you may have done something with the swap file/swap partition. If that is anywhere near being correct, I'd create a swap partition and see whether that eliminates the problem.

I used a DVD that came as part of a Linux Magazine subscription. ([www.linux-magazine.com](www.linux-magazine.com))

socref

---

### Post by unutbu on 2008-07-07
socref, sorry -- I missed that you said there was no sound of incessant disk activity, only the blinking light. So, please ignore my suggestion about hdparm. 

Since you are only seeing a light and not disk activity, I'm inclined to believe there is no problem. If you are really concerned, however, a quick call to
Dell's Linux Tech support (866 622 1947) should allay or confirm your concern pretty quickly. They should be able to tell you if the blinking light is normal.

---

### Post by socref on 2008-07-07
> **unutbu said:**
> socref, sorry -- I missed that you said there was no sound of incessant disk activity, only the blinking light. So, please ignore my suggestion about hdparm. 

Since you are only seeing a light and not disk activity, I'm inclined to believe there is no problem. If you are really concerned, however, a quick call to
Dell's Linux Tech support (866 622 1947) should allay or confirm your concern pretty quickly. They should be able to tell you if the blinking light is normal.

OK, thanks for update on hdparm. I won't run that one. 

I sent an e-mail to Dell support last week. No reply yet, but I'll follow-up with a phone call. 

Thanks for your input.
socref

---

### Post by sdennie on 2008-07-07
Try this guide to reduce disk activity: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

---

### Post by socref on 2008-07-07
Well I called Dell Ubuntu support just now was told that the H/D light is supposed to blink constantly! :confused:

They said that from the moment the power is turned on the light will blink to show hard drive activity. They said that I should worry if the light does NOT blink constantly.

Any opinions? Does that sound reasonable? 

I have never had a computer where the H/D light flashed constantly. Rather, it only flashed when the drive was being accessed.

Should I call Dell again and speak to someone else? Or is the explanation reasonable?

Thx
socref

---

### Post by unutbu on 2008-07-07
This doesn't exactly prove that there is nothing wrong with a blinking blue light on the 530, but it does show that Dell has an affinity for blinking blue lights:

[http://www.allbusiness.com/technology/936893-9.html](http://www.allbusiness.com/technology/936893-9.html)
On Dell servers a blinking blue light means there is a system in the rack.

---

