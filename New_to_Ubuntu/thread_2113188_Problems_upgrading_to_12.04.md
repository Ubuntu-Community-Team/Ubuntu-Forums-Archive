---
title: "Problems upgrading to 12.04"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by MrLeek on 2013-02-06
I've left it until now to upgrade from 11.10 since my printer refused to work after that upgrade......nothing goes smoothly does it! 

It looks like I had the error as reported in Bug #970260 when the upgrade hangs on the memtest process. From the bug report it seemed that killing that process would do the trick. So I tried to open up a new terminal by clicking the dash, but that just made the taskbar disappear. Keyboard shortcut to open a terminal didn't work - I could type into the terminal window contained within the upgrade window but that obviously did nothing. The only result left was to REISUB(?) and reboot.

When I try to reboot normally I end up with a black screen plus mouse pointer which doesn't move. The recovery mode presents options that probably will cause more harm if I just try stuff. So, especially as its getting late I'm going to stop now, post here for help and resume tomorrow!

I'm far from certain what is possible to resolve this - im guessing that trying to continue the install is just going to be difficult at best! I suppose if all else fails I could boot via a Live dvd, mount the drive in question and copy the home drive. Not 100% on how to do that so either some pointers or some google searches will need to be done. Or is there some other way to resolve this?

Annoying thing is...I've got a pair of machines I'm upgrading to use Edbuntu ( sister plus kids). They've played with a live DVD and love it, but I've had a gfx card glitch to sort (was going to post about that). Got other problems to solve now!! :mad:

---

### Post by DuckHook on 2013-02-06
<sigh> ...don't know how many times on these forums that people don't backup before upgrading which leads to fingernail-gnawing suspense as they try to belated backup on a broken system. Not scolding you: just making a sad observation.

Okay, you can backup at this point (hopefully) by following the instructions [here]("http://ubuntuforums.org/showthread.php?p=12494352#post12494352"). I'm pointing you to a recent thread because I've already given same instructions twice these last two days, so makes no sense to repeat.

Let's make your data safe first. Straighten out install afterwards.

---

### Post by MrLeek on 2013-02-07
I know - stupid schoolboy error not backing up the data first. The instructions that you posted are very clear, and that's what I had in mind when I realised things were not going to plan. Save data first then go from there....

As an aside, is having the home directory on a different drive a smart idea? From my understanding it makes upgrading much easier - I.e. fresh install - but is it as simple as that?

Thanks for the post

---

### Post by MrLeek on 2013-02-07
Hmmm.....that's two different live DVDs that throw a "(initramfs) Unable to find a medium containing a live file system" problem

I think I installed ubuntu the first time using a USB stick - ill try that.

---

### Post by MrLeek on 2013-02-08
> **MrLeek said:**
> Hmmm.....that's two different live DVDs that throw a "(initramfs) Unable to find a medium containing a live file system" problem

I think I installed ubuntu the first time using a USB stick - ill try that.

Ok, strange. Live flash drive works fine, but insisted on only trying to install ubuntu (which I stopped early to avoid any risk of data damage). Might have been possible to get to a live cd version, but wasn't worth the risk.

Solution was to create a live flask stick using Puppy Linux, boot into that and copy the data that way. Primary data recovered and safe. I want to investigate having the Home directory on a different  partition to allow for easier upgrade and perhaps trying other linux versions. Bit of homework to do I think..

Moral of the tale: protect your data! From there upgrading is far less scary! ;)

---

### Post by DuckHook on 2013-02-08
> **MrLeek said:**
> ...is having the home directory on a different drive a smart idea? From my understanding it makes upgrading much easier - I.e. fresh install - but is it as simple as that?

I always define a separate /home partition because it makes sense for my type of use. I run 12.04 LTS as my base system and have no intention of upgrading it until end-of-life in 2017. I do run newer versions out of curiosity, but do so in virtual machines inside of my base 12.04 install. Because I don't upgrade every 6 months, I don't have to worry about the problems of inheriting inappropriate config files on version upgrades, which is the main drawback to separate /home partitions. On the contrary, my biggest risk is that some update, new app or configuration change breaks my system. If it were bad enough, I would need to reinstall 12.04 and that is where a separate /home partition shines. I can just reinstall the OS, tell the install process that I have an existing /home partition, and it will just plug my old /home into the new OS lickety split, and I'm back up and running in less than 20 minutes.

However, there is an even more exacting way to define partitions that works better for people who constantly install the newest: they define a separate /data partition, but keep /home married to / (root). This way, with each fresh install, /home gets wiped out and freshly installed along with the OS, but their *data* is preserved and can be reconnected just like I do with /home (thanks to *@oldfred* for pointing this out). This is true ultra-guru-ism and a really good habit to start out with.

I trust that you were able to successfully retrieve your data. Happy Ubuntuing!

---

