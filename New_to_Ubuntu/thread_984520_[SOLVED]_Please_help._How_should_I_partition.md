---
title: "[SOLVED] Please help. How should I partition?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-16
Hi everyone. So I have decided to make the full switch to ubuntu. I have 2 Hard drives.
one Of them is a 120g(older hard drive) the other is a 500g (newer and faster). 
I am doing a fresh install of ubuntu 8.04 and I am thinking I want to use the 120 as the /home. But how should I partition the 500g drive. /boot,/swap,/root,/tmp,/usr,/var,/srv,/opt,/user/local.?

What is necessary what is not?
If there is already a thread on this please point me to it I could not find many that were relative to this.

Thanks for any help.
[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
sys.specs
P4, 3g
4gram
onboard vid card:(
the rest i believe irrelevant.

---

### Post by philinux on 2008-11-16
Only partitions really necessary now are 

/
/home
/swap

You could just use the older disk as a data backup disk.

---

### Post by ugm6hr on 2008-11-16
I'd use the 500GB for /home.  You don't need more than 10-20GB for the rest, so 120GB should be fine.

I don't bother with other partitions, just /, /home and swap.

---

### Post by starcannon on 2008-11-16
Adendum: Do like [[COLOR=#D40000]**ugm6hr**[/COLOR]]("http://ubuntuforums.org/member.php?u=103883") says, just don't waste to much on root / for most of us 20gb root partition is way overkill.

Root also known as / should go on the first drive also known as the master drive, it is not necessary, but since your going Ubuntu exclusive its best. 
Swap can go where ever, might as well stash it on the faster of the 2 drives.
and /home can go on either.

My favorite scheme is:
10 to 20gb for root /
2gb for swap
the rest to /home

I would probably put / and /home on the 120gb drive, and swap on the 500gb drive, and then just put a storage partition on the rest of the 500 as well (do that after your done installing Ubuntu, we'll tackle that later, its best to stick with one project at a time)

---

### Post by nakama85 on 2008-11-16
> **starcannon said:**
> Adendum: Do like [[COLOR=#D40000]**ugm6hr**[/COLOR]]("http://ubuntuforums.org/member.php?u=103883") says, just don't waste to much on root / for most of us 20gb root partition is way overkill.

Root also known as / should go on the first drive also known as the master drive, it is not necessary, but since your going Ubuntu exclusive its best. 
Swap can go where ever, might as well stash it on the faster of the 2 drives.
and /home can go on either.

My favorite scheme is:
10 to 20gb for root /
2gb for swap
the rest to /home

I would probably put / and /home on the 120gb drive, and swap on the 500gb drive, and then just put a storage partition on the rest of the 500 as well (do that after your done installing Ubuntu, we'll tackle that later, its best to stick with one project at a time)

with this being said. I think I may want to use the 120 g exclusively as backup sense the 500gsata is the first drive i will use it as the main. what do you think of this setup.
/boot ? - should i have this?
/ -20g
/swap -2or4g
/home -the remainder of the drive

what good programs are there for automated backup to another drive?

---

### Post by binbash on 2008-11-16
> **ugm6hr said:**
> I'd use the 500GB for /home.  You don't need more than 10-20GB for the rest, so 120GB should be fine.

I don't bother with other partitions, just /, /home and swap.


^^^^^^^^^^

Listen this advice : )

---

### Post by philinux on 2008-11-16
No need for a boot partition. I use 12 gig for root and am only currently using 3.3 after installing extra apps.

---

### Post by nakama85 on 2008-11-16
> **philinux said:**
> No need for a boot partition. I use 12 gig for root and am only currently using 3.3 after installing extra apps.

so do you know any good software for backup?

---

### Post by binbash on 2008-11-16
clonezilla

---

### Post by starcannon on 2008-11-16
> **nakama85 said:**
> with this being said. I think I may want to use the 120 g exclusively as backup sense the 500gsata is the first drive i will use it as the main. what do you think of this setup.
/boot ? - should i have this?
/ -20g
/swap -2or4g
/home -the remainder of the drive

what good programs are there for automated backup to another drive?
Yeah putting the entire OS on the 500gb drive would be fine, and makes good sense since it is the first drive. 

There is no need for a separate /boot partition (I used to do this when I was into compiling my own kernels but generally its unnecessary). 

2gb is plenty of swap unless your on a laptop or want to hibernate, in which case make sure you have >= the ram in your machine for swap.

If you want to run more than 3gb of ram without having to install a special kernel you will need the 64bit OS, though it still requires a bit of tuning. For your best first time out experience I would still recommend the 32bit version of Ubunt; best to keep the learning curve as minimal as possible, you can always install 64bit later quite easily since you are putting /home on its own partition (wish that was default way of doing things on the installer).

As far as backup software goes, I've heard a lot of good things about sbackup, myself I just tarball it to where ever I have space and call it good.

GL and keep it fun

---

### Post by nakama85 on 2008-11-16
> **starcannon said:**
> If you want to run more than 3gb of ram without having to install a special kernel you will need the 64bit OS, though it still requires a bit of tuning.

I only have a 32bit system. Is there any way to get ubuntu to recognize the rest of my ram or did i waste my money? lol

thanks

---

### Post by philinux on 2008-11-16
It's more than 4 gig ram that needs 64 bit so you did not waste your money. Your onboard ram will also use some of it too. so no worries.

---

### Post by nakama85 on 2008-11-16
So here is what i did

/ - 20g
/swap - 2g
/home - remaining

thanks for the advice everyone. I will also give the previously mentioned backup programs a shot.

Thanks again for all the help!!!!!:)
:guitar:

---

