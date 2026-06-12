---
title: "Disable Update Manager?"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-12
Update manager shows a huge list of sizable updates.

Do you download the entire list?

The list seems excessive to my needs.

What is your practice?

---

### Post by Elfy on 2012-04-12
When I do a clean install there is usually a long list of updates - this is normal, once that first is done then the frequency and quantity of updates reduces remarkably.

Development versions are different. 

Without knowing the specifics of your case it is hard to tell ;)

---

### Post by Paqman on 2012-04-12
> **Boyntonstu said:**
> 
The list seems excessive to my needs.


Anything listed as a security update is important. I always install everything, but if you're on metered bandwidth or a slow connection you might choose otherwise.

---

### Post by uRock on 2012-04-12
I install every update offered. The list should stay short as long as updates are run weekly.

---

### Post by Boyntonstu on 2012-04-12
> **forestpiskie said:**
> When I do a clean install there is usually a long list of updates - this is normal, once that first is done then the frequency and quantity of updates reduces remarkably.

Development versions are different. 

Without knowing the specifics of your case it is hard to tell ;)

A clean install.

I gather that I accept all of them or is there a 'preferred update list' that is 90% effective?

11.10 is on a 8 GB USB drive and I would like it to be as light as necessary.

For example, I do not use presentation, games, social networking,  or need any languages in addition to US English.

Suggestions?

---

### Post by mcduck on 2012-04-12
> **Boyntonstu said:**
> A clean install.

I gather that I accept all of them or is there a 'preferred update list' that is 90% effective?

11.10 is on a 8 GB USB drive and I would like it to be as light as necessary.

For example, I do not use presentation, games, social networking,  or need any languages in addition to US English.

Suggestions?

The updates are only offered for packages yu already have installed, so installing all the available updates will not make your system any less lightweight. It's simply replacing packages you already have with new versions that have security or bug fixes applied.

I would pretty much recommend just installing all the available updates. The policy for updating a package version in Ubuntu is pretty strict, so any updates you get are always for a good reason.

...besides, if it's a fresh install, the amount of updates you see now is a one-time-only situation,

---

### Post by Curtis6767 on 2012-04-12
Updates will only be detected for things already on your system so you should install everything.

Are you running that USB as a live USB or have you installed Ubunutu?

---

### Post by Boyntonstu on 2012-04-12
> **Curtis6767 said:**
> Updates will only be detected for things already on your system so you should install everything.

Are you running that USB as a live USB or have you installed Ubunutu?

Yes, on a 8 GB USB, and I am loving it.  Much better than Win7 except Netflix.

Yesterday, I bought a 16 GB Sandisk Cruzer at Staples for $12.99.

My plan is to use the live USB for programs only, and save data to 2 hard drives with a redundant save and backup.

This week, I have not used Win7 even one time.

BTW After many trials, I am convinced that Firefox works better than Chromium.

For example, using Chromium and viewing a Youtube video, it stalled and stalled again.

I opened the same video 15 seconds later with Firefox and it played though.

Thanks

---

### Post by Curtis6767 on 2012-04-12
With a live CDd or USB, I think updates are lost at the end of each session.

But I'm a noob so maybe someone more knowledgeable can supply the correct answer.

---

### Post by snowpine on 2012-04-12
I install all updates (and I recommend 15gb minimum for Ubuntu).

If you want a light, minimal install, see here: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Boyntonstu on 2012-04-12
> **snowpine said:**
> I install all updates (and I recommend 15gb minimum for Ubuntu).

If you want a light, minimal install, see here: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)


16 GB is what I will use.

How would you partition it, remembering that my plan is to store very little on the USB.

(The USB installation of 11.10 is persistent)

246.7  MB of updating is almost done.

After the updated install, I plan to use a LIVE CD to clone one USB to another USB.

                                 dd if=/dev/sda of=/dev/sdb

---

### Post by snowpine on 2012-04-12
> **Boyntonstu said:**
> How would you partition it, remembering that my plan is to store very little on the USB.

I use a single ext4 root / partition on my USB installs.

---

### Post by Boyntonstu on 2012-04-12
> **snowpine said:**
> I use a single ext4 root / partition on my USB installs.

IICRC The install kept bugging me to create a Swap partition.

I assume from your statement that Swap is not required.

Please educate me.

---

### Post by snowpine on 2012-04-12
> **Boyntonstu said:**
> IICRC The install kept bugging me to create a Swap partition.

I assume from your statement that Swap is not required.

Please educate me.

I do not use a swap partition on small disks because I would rather use the space for programs/data/documents.

If your computers are low-ram or you plan to use the hibernate feature, you may wish to create a swap partition.

---

### Post by Boyntonstu on 2012-04-12
> **snowpine said:**
> I do not use a swap partition on small disks because I would rather use the space for programs/data/documents.

If your computers are low-ram or you plan to use the hibernate feature, you may wish to create a swap partition.


Thanks,

BTW The update could not find grub and it paused.

I rebooted, and it fixed everything for me.

I am LOVING Ubuntu 11.10!

On my 8 GB flash after a complete install and 247 Mb of updates, System Monitor shows memory 379.9 MiB (13.7%) of 2.7 GB and 1 GB of swap.


In System Monitor File Systems it shows:

/dev/sbd5   ext4 6.4 GiB  total  2.2 Gib free 1.9 GiB available  4.2 Gib used  69%

Why the differences?

I am a little confused.

Thanks for your help.

---

### Post by Paqman on 2012-04-13
> **Boyntonstu said:**
> 
For example, I do not use presentation, games, social networking,  or need any languages in addition to US English.

Suggestions?

There's nothing stopping you from uninstalling any stuff that's in the default install that you don't want. For example, you could remove all the Gnome games. Doing so is unlikely to save much space, and they aren't often updated, but it's your machine.

For trimming language support you can install [localepurge]("apt:localepurge"). You could also use [bleachbit]("apt:bleachbit"), which contains a similar function in addition to a lot of other bits and pieces.

---

### Post by souravc83 on 2012-04-13
Firefox and Chrome also add up a lot to the space requirements.
You can try using a minimalist browser such as Midori. 
That might help you save space.
Also there are lots of more lightweight minimalust distros out there, which you might try.
Crunchbag or maybe Slitaz. Slitaz, for example, requires only 45 Mb. 
Don't know how complete the OS is, but I plan to test that out sometime.

---

