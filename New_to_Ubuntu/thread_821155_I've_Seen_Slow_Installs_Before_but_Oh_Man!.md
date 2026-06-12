---
title: "I've Seen Slow Installs Before but Oh Man!"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by tmjva on 2008-06-06
I'm not sure about being newbie, I'm an aging Sysop but only using Ubuntu this past year.

I was happily on 7.10, a decent enough computer somewhere over a GHz, I suppose my first mistake was to say "yes" to the Hardy Heron upgrade.  It said it would be a 10 hour download, and I though I had a decent high speed internet at home.  So I got it started, watched TV and went to bed.  The next morning all there was was a mouse cursor that moved on a blank screen.

Giving up, I powered down and took the PC to work, downloaded 8.04 ISOI to a CD on my XP machine.  (Having a T3, it only took a few minutes.)  I attempted a reinstall from CD at work.  It hung all day on step 2 of 7, trying to decide what time zone it was in.  I aborted the install and took it home, and tried again tonight from CD.

After 3 hours of again deciding what time zone it is in, it finally woke up.  Now I'm in Step 4 of 7 and it is "Warning" me, that partitioning will take a long time!  

I suppose I't will take a week at this rate.

Oddly enough the jump away from step 2 occurred only after I fired up my internet so I could register here.  (I registered on my old XP laptop and am typing from it at this point.)  So I'm wondering, if I'm installing from CD, did it care about having the internet available?

Of course the other thing I'm worried about is will I lose all my old files?  Grumble, grumble, grumle.

---

### Post by Bubba64 on 2008-06-06
> **tmjva said:**
> I'm not sure about being newbie, I'm an aging Sysop but only using Ubuntu this past year.

I was happily on 7.10, a decent enough computer somewhere over a GHz, I suppose my first mistake was to say "yes" to the Hardy Heron upgrade.  It said it would be a 10 hour download, and I though I had a decent high speed internet at home.  So I got it started, watched TV and went to bed.  The next morning all there was was a mouse cursor that moved on a blank screen.

Giving up, I powered down and took the PC to work, downloaded 8.04 ISOI to a CD on my XP machine.  (Having a T3, it only took a few minutes.)  I attempted a reinstall from CD at work.  It hung all day on step 2 of 7, trying to decide what time zone it was in.  I aborted the install and took it home, and tried again tonight from CD.

After 3 hours of again deciding what time zone it is in, it finally woke up.  Now I'm in Step 4 of 7 and it is "Warning" me, that partitioning will take a long time!  

I suppose I't will take a week at this rate.

Oddly enough the jump away from step 2 occurred only after I fired up my internet so I could register here.  (I registered on my old XP laptop and am typing from it at this point.)  So I'm wondering, if I'm installing from CD, did it care about having the internet available?

Of course the other thing I'm worried about is will I lose all my old files?  Grumble, grumble, grumle.

The upgrade should have never taken 10 hour unless you were using a dialup, also during any download or update or upgrade you will se the time flex all around the place. Have you checked the CD for a good burn, and how fast did you burn it at.

---

### Post by ardvark71 on 2008-06-06
Hi...

Wow! What you're describing should only take a few seconds at most! :o

You might want to refrain from the upgrade if it's not a problem with your CD, I'm smelling disaster here, including the loss of your files. :(

Best Regards...

---

### Post by drs305 on 2008-06-06
I agree with Bubba64 about a posible bad disk. I tried inserting the LiveCD without an internet connection. It went through welcome, language and keyboard in about 10 seconds - so it wasn't trying to connect to the internet.

Did you run md5sum on the .iso? Burning at a slow speed also may help. I don't think this is an ubuntu issue ;-)

Best of luck with the install.

---

### Post by rogerdpenguin on 2008-06-06
Try wubi, thats what I did and it worked beautifully :)

---

### Post by Bubba64 on 2008-06-07
If it was me and I wanted to save stuff, a backup with a fresh install with a daily ISO is what I would do. If you find Hardy is not what you want after a install you would still have the backup for a downgrade to another distribution. If you burn a new CD don't burn it any faster than 4x and have the computer scan it for a good download and burn before installing.

---

### Post by arpanaut on 2008-06-07
I feel your pain!

A while back I upgraded a machine from 7.04 to 7.10 W/ broadband connection and I figured it would take an hour or two.... 6 hours. later I was still configuring things, and cleaning up. Three or four times I came back to the room to find a prompt asking for choices and to continue?  I never did get it cleaned up to my satisfaction. Never again.

I grabbed an 8.04 disk and was up and running, tweaked out and back to normal in less than 2 hours.(kept kicking myself for not doing that in the first place for another two hours, LOL)

Yes the install can stall trying to set up "network interfaces" and "time servers" if not connected to the internet, been there, hate that!

That said, something does seem problematic with your hardware, or disk.
How long did it take to install the first time?

I do hope that you have backed up your data, always do that myself as a matter of course anytime I'm doing anything "radical" with my boxes... 

Hope you get it sorted!

---

### Post by tmjva on 2008-06-07
Anybody still following the thread I got to step 5 of 7 eighteen hours ago and still waiting for step 6.

---

### Post by anjilslaire on 2008-06-07
Man, there is something seriously wrong with your setup. Quite possibly the disc, perhaps a bad burn as mentoned previously.

I certainly hope you have a backup of your data, or at least have /home on a separate partition.

If it were me, I'd wipe all partitions & start from scratch. OR if worse came to worse, zero the drive and start over. There is no way it should be doing this.

---

### Post by perlluver on 2008-06-07
> **tmjva said:**
> Anybody still following the thread I got to step 5 of 7 eighteen hours ago and still waiting for step 6.

What is step 5 of 7?  I can't remember right this minute.

Edit:  Looking at the step by step installation guide, that is where you type in all your info.  Is it hanging when you press next?  If so, it seems your disk is bad.

---

### Post by tmjva on 2008-06-08
Thanks!  I check into it at work on Monday.  Maybe cut a new disc and check it this time.  Meanwhile, it is just fun to see how long it takes before it gives up or goes to step 6.  I'm at 21 hours for Step 5 and counting!

Step 5 is where you enter your name and password twice, and name the computer also.

---

### Post by tmjva on 2008-06-14
Gave up, switched to Debian, installed fine.

---

