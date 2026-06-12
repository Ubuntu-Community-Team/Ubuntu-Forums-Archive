---
title: "Help setting up dual boot using Media Direct button"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Hikertrash on 2008-07-28
Hey, I'm thinking of taking the plunge and trying Ubuntu but I have a few specific questions.

As it is now I have a Dell diagnostics partition, a C drive which holds XP and a extended partition D drive with My Documents, settings for Firefox and Thunderbird etc. Is 10GB enough for Ubuntu and 4Gb for the swap file (grub)? I'd be shrinking my D drive using PartedMagic. As I understand, these would need to be ext3, correct? Also, I'm not sure if I can shrink D: within an extended partition. Assuming I can , is it OK to have Ubuntu in an extended partition and the swap file?

Also, not long ago I upgraded my internal HDD and wiped out Media Direct which was on a hidden partition which was easier said than done. I'd like to be able to use the button to boot into Ubuntu and the normal power button to boot into XP as it is now. From a cold boot if I press the MD button now I'll get a MD slash screen before booting into XP.

I've read a few threads about using the MD button but I'm kind of lost here and would appreciate specific directions for the above.

---

### Post by kansasnoob on 2008-07-28
It would be really helpful to see a screenshot of your hard drive, via Gparted.

You can install gparted from synaptic, if it's not already, and then just go to Administration > Partition Editor.

That would give us a much better idea of what your drive(s) look like.

Notice I say "drive(s)". If you have more than one drive give us screenshots of all.

---

### Post by SpenceMakesSense on 2008-07-28
well to simply answer one of your questions. Yes 10 gbs will be a good amount for trying ubuntu. and 4 gb is also pretty good for swap

---

### Post by Hikertrash on 2008-07-28
Here's a screenshot using Partition Magic.  I can do one with gparted if need be (I think).

---

### Post by Hikertrash on 2008-07-28
> **SpenceMakesSense said:**
> well to simply answer one of your questions. Yes 10 gbs will be a good amount for trying ubuntu. and 4 gb is also pretty good for swap

Good, that will leave amble room for Windows, which I'll mostly be using, until I get the hang of Ubuntu.

Here's another thread on the topic.  The differences I see being in the notebookreview thread is that they had Vista and used that CD to partition, whereas I'll be using gparted

[http://ubuntuforums.org/showthread.php?t=853716](http://ubuntuforums.org/showthread.php?t=853716)

I need to read the Ubuntu forum thread.

Ideally, I'd like step by step instructions for my situation.

---

### Post by Sef on 2008-07-28
> well to simply answer one of your questions. Yes 10 gbs will be a good amount for trying ubuntu. and 4 gb is also pretty good for swap

8 - 10 GB for root (Where Ubuntu goes) is fine.

4 GB swap is too much.   I assume you have 2 - 3 GB ram.  If that is the case, then 1 GB swap would be just fine.  I have 2 GB ram and 1 GB swap and rarely use it.

---

### Post by Hikertrash on 2008-07-28
> **Sef said:**
> 8 - 10 GB for root (Where Ubuntu goes) is fine.

4 GB swap is too much.   I assume you have 2 - 3 GB ram.  If that is the case, then 1 GB swap would be just fine.  I have 2 GB ram and 1 GB swap and rarely use it.

That's good.  I have 2GB but read somewhere where double the RAM was recommended.

Here's a screen shot from the other forum.

---

### Post by kansasnoob on 2008-07-28
> **Hikertrash said:**
> That's good.  I have 2GB but read somewhere where double the RAM was recommended.

Here's a screen shot from the other forum.

You're losing me somehow.

Is that last screenshot a shot of your own partitions? The previous one was garbage!

---

### Post by kansasnoob on 2008-07-28
> **Sef said:**
> 8 - 10 GB for root (Where Ubuntu goes) is fine.

4 GB swap is too much.   I assume you have 2 - 3 GB ram.  If that is the case, then 1 GB swap would be just fine.  I have 2 GB ram and 1 GB swap and rarely use it.

Exactly right! No need for a large Swap unless you plan to hibernate.

---

### Post by Hikertrash on 2008-07-28
> **kansasnoob said:**
> You're losing me somehow.

Is that last screenshot a shot of your own partitions? The previous one was garbage!

I'm sorry didn't mean to get confusing.  By garbage do you mean you couldn't see it?  It's my HDD now with Dell Diagnostics, C:XP and D: Data 

The second screenshot is from the guy that was able to boot Ubuntu from the MD button and Vista from the power button.  I imagine I need a similar set up.

Side thought, after installing Ubuntu, what happens  to the lettering of my drives?  As it is C:XP, D:data, E:CD/DVD, F:One external drive, G:another external drive.  Only occasionally do I have one or both external HD's attached.

---

### Post by kansasnoob on 2008-07-29
> **Hikertrash said:**
> I'm sorry didn't mean to get confusing.  By garbage do you mean you couldn't see it?  It's my HDD now with Dell Diagnostics, C:XP and D: Data 

The second screenshot is from the guy that was able to boot Ubuntu from the MD button and Vista from the power button.  I imagine I need a similar set up.

Side thought, after installing Ubuntu, what happens  to the lettering of my drives?  As it is C:XP, D:data, E:CD/DVD, F:One external drive, G:another external drive.  Only occasionally do I have one or both external HD's attached.

Well, by garbage, I mean I can't even see one end of it! I'm certainly NOT going to base any suggestion on something I can't see 100%.

Throwing in some "unrelated" screenshot is a horrible idea.

We need to know what your hard drive(s) looks like.

---

