---
title: "Ubuntu won't load, been at this for weeks, please help."
date: 2008-06-21
forum: New to Ubuntu
---

### Post by lukelongbeard on 2008-06-21
Hi, I am an absolute beginner to Ubuntu, but not to pcs.  I had a power surge that fried my old motherboard and cpu, put in a new combo, couldn't get XP to recognize the HDD, trying to use Ubuntu live CD to recover my work before wiping the drive and doing full Ubuntu install cuz I'm tired of Windows anyway.

The current system is an Athlon 64 3200, ECS MB, 2gig ram, ati radeon 200 onboard video (for now at least), 300 gig HDD, etc.  

It's a custom build.  I have tried four different versions of ubuntu, two different ones in the 5.0 series, 7.10 and 8.04, all with similar results.  I've been going to a computer co-op nearby for some help, but they aren't always available.  Apparently the older versions I was given probably weren't for use in a 64 bit system, so at the suggestion of the linux experts from the co-op I came home and downloaded 8.04 for 64 bit last night.  It didn't make any difference in my problem. 

When I boot from the live CD it will load all the way to the login/username screen, then it won't load Ubuntu and just keeps refreshing back to the login.  I have tried all kinds of suggestions from these forums and elsewhere.  I hit F6 to get other options and try putting in some xserver reconfig commands, tried hitting things like ctrl, alt + F1 at login, or ctrl alt backspace, these just cause it to freeze up.

I've tried everything I've been told with nothing going.  I have literally been at this since May.  I'm looking for some solid, patient and informative help here.  The standard responses don't seem to be working, because I've tried them all.

Several sources suggest it is either a video driver or monitor compatibility issue, but alas, the things suggested to resolve the issue fail to make any forward progress.

PLEASE help me before I throw this thing against a wall.

---

### Post by sailor2001 on 2008-06-21
Try a downloaded iso of 64 alternate.........this isn't a live disk....Also you could try downloading a 64 MEPIS as that distro is good for repair.(a live disk)

---

### Post by lukelongbeard on 2008-06-21
> **sailor2001 said:**
> Try a downloaded iso of 64 alternate.........this isn't a live disk....Also you could try downloading a 64 MEPIS as that distro is good for repair.(a live disk)


I thought I read elsewhere that an alternate CD won't let me recover my saved work from the old hard disk drive. Can you confirm or deny this for me?  I will try the MEPIS suggestion first I suppose.

Thanks.

---

### Post by richiewrt on 2008-06-21
Alternant cd will force you to install it to the HDD. Also, the 32bit versions should work on your computer. Its just the 64bit that wont work on a 32bit comp. My suggestion would be to maybe try a different live cd.

---

### Post by avtolle on 2008-06-21
To save your work from the old hard disk drive, this will need to be done before booting any install CD for any OS that doesn't have a Live CD feature, unless you will do a manual partitioning; in which case, you can elect to not touch the partitions which hold the old work. Or, in the Ubuntu case, you could create free space on the HDD, and using the guided partitioner, direct installation on the largest area free. HTH.

---

### Post by lukelongbeard on 2008-06-21
> **richiewrt said:**
> My suggestion would be to maybe try a different live cd.

Like I said, I've tried at least four different ones. Actually, I also tried some of these ultimate boot CDs and they wouldn't even run.

---

### Post by lukelongbeard on 2008-06-21
> **avtolle said:**
> Or, in the Ubuntu case, you could create free space on the HDD, and using the guided partitioner, direct installation on the largest area free. HTH.

Wouldnt this require that the Ubuntu live CD load up properly in the first case?  So again, can someone help me get the thing to load?

---

### Post by richiewrt on 2008-06-21
I actually ment a different distro, such as Fedora, OpenSuse, ect.  just go to distrowatch.com and search for livecd's. If if is a video card or monitor problem, perhaps one of them will have the proper drivers installed on the live cd to allow it to boot properly. 

Secondly, since you seem to have access to a second computer, you may try pulling the HDD out and installing it into another computer and see if it will mount there. May not be practical in your situation, but just a suggestion.

You could use the alt cd and the "install to largest freespace " option, but what this does is it will shrink your windows partition, and with the power surge, and other subsequent problems this would be a last resort, because if something screws up while the partitioner is working, you will loose all your data. I have never had it happen to me, but it does happen.

---

### Post by lukelongbeard on 2008-06-21
The second computer is a laptop =/

If I were to try the alternate CD and do the "install to largest partition" thing, is there a way to go back and get rid of the Windows partition once I have recovered everything I want?  I don't want two operating systems running truthfully.  Windows has given me nothing but trouble over the years.

---

### Post by lukelongbeard on 2008-06-21
> **sailor2001 said:**
> Also you could try downloading a 64 MEPIS as that distro is good for repair.(a live disk)

Okay, I downloaded mepis and the live CD works!  now I don't know what I'm doing though.  How do I access my HDD so I can pull stuff off of it?

---

### Post by cariboo on 2008-06-21
If you've the 7.10 liveCD you should be able to boot up and run in safe graphics mode.

As far as what to do next. Mount your hdd and start copying files to whatever media you plan on using for backup. I don't have Mepis installed on anything and it's been about 2 years since I looked at it, but it is Debian based so most of the commands you'd use in Ubuntu would work on Mepis.

Jim

---

### Post by lukelongbeard on 2008-06-21
> **cariboo907 said:**
> If you've the 7.10 liveCD you should be able to boot up and run in safe graphics mode.

As far as what to do next. Mount your hdd and start copying files to whatever media you plan on using for backup. I don't have Mepis installed on anything and it's been about 2 years since I looked at it, but it is Debian based so most of the commands you'd use in Ubuntu would work on Mepis.

Jim

The 7.10 liveCD will not let me boot in safe graphics mode.  Tried it.  Neither will 8.04.

Mounting my HDD is what I'm having trouble with on Mepis right now.  Anyone able to tell me how to do that either on Ubuntu or Mepis seeing as the process might be pretty similar?  Remember, <------ absolute beginner here.

---

### Post by lukelongbeard on 2008-06-21
keeping this alive in the hopes that someone will see it and tell me how to mound a hard drive in mepis or ubuntu. i can't seem to find it.

---

### Post by richiewrt on 2008-06-21
Easy way to do it in mepis is open gparted, and right click on the windows partition and click mount.. then browse to it in konqueror

**Edit** I was playing arround with a mepis live cd and realized there is a much easier way. On the bottom right there is an icon that has like three cubes (red, green, and orange). click it and you should be able to mount your partitions there.

---

### Post by lukelongbeard on 2008-06-22
> **richiewrt said:**
> Easy way to do it in mepis is open gparted, and right click on the windows partition and click mount.. then browse to it in konqueror

**Edit** I was playing arround with a mepis live cd and realized there is a much easier way. On the bottom right there is an icon that has like three cubes (red, green, and orange). click it and you should be able to mount your partitions there.

okay, so i used gparted like stated, and i was able to see the partitions.  there are a list of two ntfs partitions, one with 19 gigs used, and the other unused, which makes sense b/c i partitioned it twice and didn't really use the second one.  

when i go to mount the boot one, the one i need access to, it says "mount on" and the only option is '/mnt/sda1'  i don't know what that means, but when i mounted it there and opened konqueror i was unable to find it.

what next?  thanks in advance...

---

### Post by lukelongbeard on 2008-06-22
okay, i was actually able to find /mnt/sda1 myself now, but it says i don't have access rights to this location.  how can i get access rights to it?  

thanks again.

---

### Post by lukelongbeard on 2008-06-22
holy smokes, i am well on my way, i got access to the old hard drive partition and think i am able to copy my work onto a micro disk now.  i'll keep posting my efforts, and uh...any more questions i have >.<  

what a long and frustrating month, but i'm making some progress.  i really want ubuntu as opposed to mepis though, i'll have to try the alternate CD once i get my saved files recovered.

---

### Post by lukelongbeard on 2008-06-22
okay, now i am at another empasse.  when i try to copy my 'my documents' folder onto my usb storage device i get a message that /mnt/sda1/documents and settings/etcetc does not exist.  and it won't let me copy the folder.  any ideas?

---

