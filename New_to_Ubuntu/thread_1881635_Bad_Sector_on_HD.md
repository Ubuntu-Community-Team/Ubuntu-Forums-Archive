---
title: "Bad Sector on HD?"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by Call My Function on 2011-11-15
I just checked out the state of my disks after some mysterious errors in Windows regarding my external HD. The external seems to be fine, but I discovered that my main HD, the one that hosts my OS's, has a bad sector.

I'm not familiar with hardware, so I wanted to ask you guys: If it has a bad sector (and no other errors from what I can tell), can I assume it will survive a bit longer, or should I automatically skip to "EVERYBODY PANIC" mode?

Like I said, SMART didn't list any other problems, however it *is* an extremely old disk-- 8 years and counting. I'm going to run some more tests on it to ferret out anything else. Any recommendations for what else I should do are welcomed. (I'm already working on backing up data.)

---

### Post by 3rdalbum on 2011-11-15
One, single, solitary bad sector is no cause for alarm. However, keep an eye on it; if a few more sectors go bad within a few months then you should make regular backups and arrange to buy a new disk.

I think the "OMG DANGER WILL ROBINSON!" point is around 25 bad sectors, but remember that a bad sector could occur in the middle of the most important document on your computer, rendering that document unreadable.

---

### Post by lolpenguin on 2011-11-16
chkdsk (no GNU/Linux equivalent yet) will find and fix most disk problems, but if more bad sectors start occurring to arrange for a new hard disk (and backup frequently in the meantime).

---

### Post by jjex22 on 2011-11-16
+1 on 3rdalbum and lolpenguin - no need to panic just yet! bad sectors happen, if you're getting one its not too bad, check disk resolves the issue for you, but keeping an eye on it is really important as these can be the warning signs of trouble to come - if you run a scan one day and have to sit through pages of errors popping up that's time to panic, run for the hills/ duck and cover!

Obviously if you were a very very naughty youngster, now would be the time to just double check you are backing up everything off your hdd.

If you're dual booting, you can check your linux partition isn't suffering the same aging effect with fsck for example:

fsck /dev/sda2 

for full options check out the man page.

this can't check the ntfs partition to the best of my knowledge though, - but ntfsfix may well be able to help - I've not used it personally, so I'll bump you on to [here]("http://manpages.ubuntu.com/manpages/hardy/man8/ntfsfix.8.html")

Hope you're HDD holds out - with SSD's bound to start falling in price in the not too distant future it's be nice if it could hold out 'til then for you!

---

### Post by ofnuts on 2011-11-16
Also, world of advice: if you find a file with a bad sector, don't erase it... that would return the bad sector to the free pool and it could be used again for a more important file. So just rename the file and move it to some ""garbage" directory.

---

### Post by Call My Function on 2011-11-16
Thanks for all the advice. My backup drive arrived today, so even if things suddenly go to hell I should be alright.

I've been trying to figure out how to run a proper scan on the disk. If I understand correctly, chkdsk will only scan *Windows'* partition? And fsck will scan Ubuntu's? (I thought that only checked the filesystem.) They're both on the same drive.

While I'm at it, I might as well ask: I've been trying to self-check my new HDD with Disk Utility (because paranoia), but 30-40 mins after starting the scan stops with the message "canceled by either soft or hard reset." What's that about?

---

### Post by Call My Function on 2011-11-16
OH GOD, a turn for the worse... I restarted Windows, and shortly after the system loaded to desktop this HORRIFIC WHINE starting shrieking inside my computer. To use the words of someone else who had heard this, it is like a "laser beam" noise.

I shut it down immediately and I'm afraid to turn it back on. ;_; Is it safe to run?

---

### Post by jjex22 on 2011-11-16
Well it's safest to assume it is the hdd - at the end of the day only three things make a mechanical noise in a modern pc - disk drive, hard drive and fan. 

If the hdd is dying then there's sadly no way to stop it - if you don't have a back  up, download a [clonezilla]("http://clonezilla.org/downloads.php")  live cd to attempt copying the contents to another drive. 

If you did back up earlier, then there's no harm in seeing if something else caused the noise - it could always be a coincidence, and if the noise was coming from the psu / heatsink you'd want to know so no damage can be done. but like I say if you don't have a back up, that's the number1 priority.

---

### Post by jjex22 on 2011-11-16
reading back through I'm leaning towards a fan noise to be that loud - make sure you've got the hdd backed up, then disconnect the pc from mains and check inside for excessive dust blocking airflow - then try starting - i'd recommend starting it by pushing the power button with a pencil, just until we know it's not the psu. let it run, if the noise come back, try and determine if its comming from the psu - if it is shut it down right away.


next check the noise desn't come from any other fans - if it does, this is a sign that they'll need replacing if you add sensors-applet from apt-get, you can keep an eye on the cpu temp while you work to determine how urgent the fan replacement would be, and if you can safely use the pc in the mean time.

as for the disk hard drive - should be easy to tell if they're making the noise, and easy to replace.

---

### Post by Call My Function on 2011-11-16
> **jjex22 said:**
> Well it's safest to assume it is the hdd - at the end of the day only three things make a mechanical noise in a modern pc - disk drive, hard drive and fan. 

If the hdd is dying then there's sadly no way to stop it - if you don't have a back  up, download a [clonezilla]("http://clonezilla.org/downloads.php")  live cd to attempt copying the contents to another drive. 

If you did back up earlier, then there's no harm in seeing if something else caused the noise - it could always be a coincidence, and if the noise was coming from the psu / heatsink you'd want to know so no damage can be done. but like I say if you don't have a back up, that's the number1 priority.

Unfortunately, I haven't backed up the data yet. I was hoping to scan my new drive before I used it. I'm just about to burn a clonezilla disk now.

My guess was the HDD because knowing my computer, that's what I most expect. This computer is eight years old. It has fan problems, but it definitely didn't sound like the fan. (It sounded too fast and metallic.) The CD drive wasn't in use. Afraid I don't exactly know what a PSU is, or what a heatsink looks/sounds like. (I don't even think this thing has heat sinks.) You could be right, maybe it was something else.

Wish me luck.

---

### Post by Call My Function on 2011-11-16
> **jjex22 said:**
> i'd recommend starting it by pushing the power button with a pencil, just until we know it's not the psu. let it run, if the noise come back, try and determine if its comming from the psu - if it is shut it down right away.

Could you describe this a little more? What/where is the PSU? Could I run it with the case opened so I can see directly inside?

If it IS the PSU, what are the consequences of *that* going bad? Will it explode? LOL

---

### Post by jjex22 on 2011-11-16
best of luck!

The Power Supply Unit is at the top/back of the case - what you plug the power cable into - it has a fan that blows out.

the heat sink cools your cpu - metal radiator covering the processor. I only mentioned it as some also have fans.

Really hope it all goes okay for you!


Edit: in short they kind of can - basically when they fail, they often short out (if the fan dies heat can cause this very quickly) that shorting out can send too much current to any component and damage it or make the case live in the worst (very very rare) case. obviously they usualy just spark and everything goes off, but it's always safest to assume the worst could happen.

---

### Post by Call My Function on 2011-11-16
Power Supply Unit. I should've known that. Ignore my last post.

You know what, it might actually be that. The fan on it has had problems, and I've smelt bad things from it in the past.

Is it still safe to back up my drive if it is the PSU? Or should I keep it off and do something else to save the data, like installing the drive in a different computer, or something like that?

---

### Post by jjex22 on 2011-11-16
for the moment, getting the data backed up is the priority, so if possible, yeah i'd agree with connect it to a different pc. When you open the case to get it out, unplug the pc and push the power button a couple of times to dissipate any charge (normal step).

once it's out you could try running a live cd on the pc (wouldn't need a hdd) this should tell you if it's being caused by other hardware?

---

### Post by Call My Function on 2011-11-17
For reference, here are a few videos that feature a sound similar to the one I heard. The video/recording quality wasn't enough for me to be sure:

This is the best example: [http://youtu.be/UZU9JKCdCVg](http://youtu.be/UZU9JKCdCVg)
The first one is close: [http://youtu.be/qT51Pi_dues](http://youtu.be/qT51Pi_dues)
This is also close: [http://youtu.be/mQa79pWC0OQ](http://youtu.be/mQa79pWC0OQ)

> **jjex22 said:**
> for the moment, getting the data backed up is the priority, so if possible, yeah i'd agree with connect it to a different pc. When you open the case to get it out, unplug the pc and push the power button a couple of times to dissipate any charge (normal step).

once it's out you could try running a live cd on the pc (wouldn't need a hdd) this should tell you if it's being caused by other hardware?

I didn't realize I could use a live CD without a HDD. I'm going to try this so we can find out for sure.

Thank you very much for the help, btw. I really appreciate it. :)

---

### Post by jjex22 on 2011-11-17
just to reassure you if the noise was that loud/ high pitched, i'd be surprised if it was the hdd - hdd noises tend to be deeper, more whirry if that's a word!

---

### Post by Call My Function on 2011-11-17
Well, after some futile fussing with my drive, I risked reinstalling it and running it on my PC again. So far the terrible screech hasn't returned, and the drive still seems to be working. I HAVE backed up everything I want to keep, so if it fails now, I don't care.

> **jjex22 said:**
> just to reassure you if the noise was that loud/ high pitched, i'd be surprised if it was the hdd - hdd noises tend to be deeper, more whirry if that's a word!

It wasn't high pitched, as in difficult to hear. It was LOUD! Like a metallic screeching noise. It's so hard to describe sounds; unfortunately I don't have any means of recording it if it happens again.

Since I'm no longer worried about losing data, I'm going to go ahead and close this thread. Thanks again for all the help. :)

---

