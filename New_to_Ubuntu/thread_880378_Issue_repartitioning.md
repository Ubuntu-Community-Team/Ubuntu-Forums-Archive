---
title: "Issue repartitioning"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-08-04
So, two weeks ago I bought a new hard drive for my little Dell laptop and with the added space, figured I've give Ubuntu a shot and made a small partition for it while giving Windows the lion's share of the space. 

After going two weeks only booting into Windows something like three times, I realized Ubuntu had become more than just a play thing and I needed to reverse the partitioning. 

I shrank the Windows partition without a hitch in GParted then went to expand the Ubuntu partition. The second part took a while but worked until the last second when I got a message informing me there was an error. 

I rebooted (was running GParted from the live CD) to see that the Ubuntu partition did indeed expand except for some reason, it lists the extra 80GB I gave it as used up, leaving me only with the space I already had free...anyone know what went wrong and how to fix it?

---

### Post by cdtech on 2008-08-04
Would be nice to see a screen shot of the gparted. Also could you post the output of "df -H".

**P.S.**
I'm sorry, I forgot to ask if you could boot into the Ubuntu OS.
I'm just jumping way ahead of myself here. Sorry.......

---

### Post by beanhead on 2008-08-04
if you have any files you want to save, id pull them off to a usb stick, then just do a fresh install. better to just wipe it clean and start fresh easyier too, simple is beautiful, dont make it harder then you have to, then maybe go to the gparted page to learn more, also remember its free dont let it get you stressed :D welcome to ubuntu :D

---

### Post by cdtech on 2008-08-04
> **beanhead said:**
> if you have any files you want to save, id pull them off to a usb stick, then just do a fresh install. better to just wipe it clean and start fresh easyier too, simple is beautiful, dont make it harder then you have to, then maybe go to the gparted page to learn more, also remember its free dont let it get you stressed :D welcome to ubuntu :D

Simply wiping a drive is not always the best method to correct issues. It's best to solve it now so in the end if the problem arises later (when everything is configured the way you want) you'll be able to tackle the issue (providing you've kept a log of your journey).

I say keep notes and work it out........

---

### Post by shatteredmindofbob on 2008-08-04
> **cdtech said:**
> Would be nice to see a screen shot of the gparted. Also could you post the output of "df -H".

**P.S.**
I'm sorry, I forgot to ask if you could boot into the Ubuntu OS.
I'm just jumping way ahead of myself here. Sorry.......

robert@robert-laptop:/usr/bin$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda6               50G   5.6G    42G  12% /
varrun                 1.1G   136k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G    50k   1.1G   1% /dev
devshm                 1.1G    13k   1.1G   1% /dev/shm
lrm                    1.1G    41M   1.1G   4% /lib/modules/2.6.24-19-generic/volatile


There's your output...not that I've used less than 6GB

and here's the screenshot which claims I'm using closer to 80

---

### Post by shatteredmindofbob on 2008-08-04
> **beanhead said:**
> if you have any files you want to save, id pull them off to a usb stick, then just do a fresh install. better to just wipe it clean and start fresh easyier too, simple is beautiful, dont make it harder then you have to, then maybe go to the gparted page to learn more, also remember its free dont let it get you stressed :D welcome to ubuntu :D

Everything's already backup, I was prepared for something horrible to go wrong during the repartition taking everything with it, so I'm certainly tempted to do a wipe aside from the time it'll take. 

And trust me, it's not stressing me out in the least...the initial reinstall of Windows was far more painful...took me nearly an hour to get it to recognize, let alone USE my wireless card...which worked instantly in Ubuntu, so I have no idea why I'm always hearing complaints about wireless compatibility. 

Heh, and just to top it off, when I was reading up on Ubuntu and Linux in general, I always seem to find someone mocking the use of the command line interface...well, talk about some irony. In trying to install a few Microsoft programs, I ended up having to manually register DLL files...from the command line...to get them to work. 

So yes, so far I'm satisfied with my experience....

---

### Post by beanhead on 2008-08-05
YES cdtech you are absolutely correct, I just didnt want to put of a new user by making things overly complicated :D

That's cool too i was really happy when i fired up hardy and everything just worked instantly, :D

---

### Post by kansasnoob on 2008-08-05
I'm following this just to learn, so I have no answers but I can see an oddity:

df -H shows:

> Filesystem Size Used Avail Use% Mounted on
/dev/sda6 50G 5.6G 42G 12% /

But the screenshot indicates sda6 is over 117GB.

Odd indeed!

---

### Post by shatteredmindofbob on 2008-08-05
> **kansasnoob said:**
> I'm following this just to learn, so I have no answers but I can see an oddity:

df -H shows:



But the screenshot indicates sda6 is over 117GB.

Odd indeed!

therein lies my problem...I want start re-ripping my CD collection, but I want that extra space!

---

### Post by cdtech on 2008-08-05
I would create a mount point for the partition "sda6" and see what information you have within that partition. There is definetly data within that partition.

It looks to me that the data didn't have a chance to finish moving. Is your windows working ok? Do you have anything worth keeping in windows?

---

### Post by kansasnoob on 2008-08-05
> **shatteredmindofbob said:**
> therein lies my problem...I want start re-ripping my CD collection, but I want that extra space!

I hear you. I'm sure someone will have an answer. It's generally just a matter of being patient until the right person reads your post. But I'll be following this too because I'm constantly playing with things and I love to learn. For instance I just learned something new here: 

[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

(You may even need to know that when you're down).

One thing I'm thinking, but this is in no way an answer to your problem, is that it would be wise to have either a separate home partition, or (my personal preference) a shared partition(s) for storage (which I prefer to make NTFS, but there are many options).

---

### Post by shatteredmindofbob on 2008-08-05
> **cdtech said:**
> I would create a mount point for the partition "sda6" and see what information you have within that partition. There is definetly data within that partition.

It looks to me that the data didn't have a chance to finish moving. Is your windows working ok? Do you have anything worth keeping in windows?

Windows worked fine when I tested it quickly. Nothing worth keeping other than the configuration, though. 

And well, showing my true noob stripes here, how do you create a mount point for sda6? GPart shows it as mounted...

---

### Post by shatteredmindofbob on 2008-08-05
Alright, I decided to double-check and Windows boots just fine

---

### Post by cdtech on 2008-08-05
Are you using the live cd or are you booted into Ubuntu?

If your in Ubuntu, just go to places and you can browse the partition there. If your using the live cd you need to go to the mnt directory to browse the partition.

I'm thinking if there's nothing worth keeping on that partition you can just umount /dev/sda6 or umount /mnt/sda6 and use gparted to reformat that partition.

---

### Post by kansasnoob on 2008-08-05
> I'm thinking if there's nothing worth keeping on that partition you can just umount /dev/sda6 or umount /mnt/sda6 and use gparted to reformat that partition.

Which means reinstalling Ubuntu, eh:confused:

---

### Post by shatteredmindofbob on 2008-08-05
> **cdtech said:**
> Are you using the live cd or are you booted into Ubuntu?

If your in Ubuntu, just go to places and you can browse the partition there. If your using the live cd you need to go to the mnt directory to browse the partition.

I'm thinking if there's nothing worth keeping on that partition you can just umount /dev/sda6 or umount /mnt/sda6 and use gparted to reformat that partition.

I can boot into Ubuntu fine, browsing through I can't find anything supposedly taking up 80GB. In fact, Disk Usage Analyzer has me only using 5GB total...

---

### Post by cdtech on 2008-08-05
Can you run "gparted" once you boot into Ubuntu? Not the live CD, or have you tried that?

I would trust "df -H" more than I would trust a GUI program.

---

### Post by shatteredmindofbob on 2008-08-05
> **cdtech said:**
> Can you run "gparted" once you boot into Ubuntu? Not the live CD, or have you tried that?

I would trust "df -H" more than I would trust a GUI program.

Yep, the screenshot I posted earlier is from a hard drive boot

and checking df- H insisting the extra space doesn't exist.

---

### Post by shatteredmindofbob on 2008-08-05
So, do I have any options beyond reformating?

Also, I should have posted this earlier, the error from GParted:
[I]
grow filesystem to fill the partition  00:00    ( ERROR )
     	
resize2fs /dev/sda6
     	
resize2fs 1.40.8 (13-Mar-2008)
Please run 'e2fsck -f /dev/sda6' first.[/I]

---

### Post by shatteredmindofbob on 2008-08-05
So, any ideas or should I just reformat?

---

### Post by shatteredmindofbob on 2008-08-05
alright, final bump before I reformat to see if there are any other options

---

### Post by Paqman on 2008-08-05
Did you run the fsck like it suggested?

---

### Post by shatteredmindofbob on 2008-08-05
> **Paqman said:**
> Did you run the fsck like it suggested?

Yes, it didn't seem to do anything. 

However! I went back to the live cd and ran Check/Repair from GParted and that recovered MOST of the space...now I've got 106 of 117 GB free, though I'm apparently only using 5.8. 

I suppose I'm not going to freak out over the remaining 5GB though I can't help but wonder what's up with that. 

Consider this solved, though! 

Thanks everyone!

---

