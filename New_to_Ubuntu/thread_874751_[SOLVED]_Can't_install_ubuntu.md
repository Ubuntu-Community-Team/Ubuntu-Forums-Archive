---
title: "[SOLVED] Can't install ubuntu"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by adudutz on 2008-07-30
I just finished downloaded ubuntu iso today, but i can't get it installed on my old PC (i'm currentlu using the new one). When it reached 94%, it always gives fatal error because of grub. I tried 5 times to do the same thing, but nothing works.

Any suggestions?

PS: I'm installing on a secondary hdd. I'm planning to remove my 1st hdd (contains Win XP) soon

---

### Post by drs305 on 2008-07-30
There are several issues with older PCs. One is the BIOS. If it's a really old computer there is a possibility you would need a separate /boot partition of no more than 512MB. 

How much memory does your machine have? 

People who have issues with older pc's sometimes have more success using the Alternate CD.

Welcome to ubuntu. :-)

---

### Post by sharks on 2008-07-30
Try alternate cd. check the cd for defects from options when u boot ubuntu.

---

### Post by adudutz on 2008-07-30
My old PC has 256MB of memory.

What should I do if i try to use alternative CD? Can anyone explain me step-by-step how to install ubuntu using alternative CD?

I'm a noob in linux OS :(

PS: I've checked for defects twice, one using md5, the other one using built-in check

---

### Post by drs305 on 2008-07-30
xubuntu is probably the flavor of the OS you should try. It's a lighter version of ubuntu that will run much better on 256MB of ram.

In answer to your question, you download the Alternate CD the same place as you downloaded the liveCD. It has a menu-driven installation process which, if you installed (mostly) ubuntu, you will understand.

[Get Xubuntu]("http://www.xubuntu.org/get")

---

### Post by halitech on 2008-07-30
256 is pushing it, the live cd installer likes to have at least 384. I would suggest using the Xubuntu alternate cd as it is lighter on requirements after running the install.

For the most part the install is self explanatory. Only thing to be careful of is when you get to the partitioning. Do the manual and set the partitions up yourself. How big of a hard drive are you using?

---

### Post by adudutz on 2008-07-30
Well, I think i'm going to try with ubuntu 1st, and later (if not working) probably i'm going to use xubuntu.

Btw, I'm underlining the problem i faced:

The installation halted at 94% regarding to a prob with GRUB. I think the installation has failed to install the GRUB to my system, so my ubuntu can't be run at all.

---

### Post by halitech on 2008-07-30
which could be still a memory issue (Live cd states at least 384meg of ram to run properly) or because of the age of your machine, you need to set up a /boot partition of under 500meg in size

---

### Post by adudutz on 2008-07-30
Well, its going to take time downloading xubuntu, since my net isn't fast, but i think i'm going to try it.

Btw, any suggestions for the ubuntu - GRUB problem??

---

### Post by halitech on 2008-07-30
you could try again and when it gets to the partitioning, do manual and create a /boot partition of 500meg

how big is the drive you are working on?

---

### Post by adudutz on 2008-07-30
my hdd:

2 @ 20GB each

hdd0 for xp + 5GB logical
hhd1 for ubuntu + 10GB logical

If I take out hdd0 and replace hdd0 with hdd1, will it affect my installation?

---

### Post by halitech on 2008-07-30
20 gig shouldn't be a problem

you can, only thing is you will need to do is install grub using something like SuperGrub to get it to allow Ubuntu to load.

for a 20 gig drive I would probably set up the partitions like this

/boot  300meg
/home  10 gig
/      whatever is left
swap  512meg

---

### Post by adudutz on 2008-07-30
> **halitech said:**
> 20 gig shouldn't be a problem

you can, only thing is you will need to do is install grub using something like SuperGrub to get it to allow Ubuntu to load.

for a 20 gig drive I would probably set up the partitions like this

/boot  300meg
/home  10 gig
/      whatever is left
swap  512meg
what does /boot, /home, /, and swap mean??

PS: actually, it is my dad's. My dad asks me to install ubuntu to his PC. He wants to preserve 10GB for his datas.

PS2: well, i think i'll tell him to get a ext3 reader instead (to read linux partitions)

---

### Post by halitech on 2008-07-30
/boot /home / and swap are the minimum partitions that any linux distro need in order to work.the /home partition will basically be his for data as most apps will be installed to / or a folder in / (also referred to as root)

---

### Post by adudutz on 2008-07-30
> **halitech said:**
> /boot /home / and swap are the minimum partitions that any linux distro need in order to work.the /home partition will basically be his for data as most apps will be installed to / or a folder in / (also referred to as root)
I think I'm going to try. Will inform you soon

---

### Post by snowpine on 2008-07-30
> **halitech said:**
> /boot /home / and swap are the minimum partitions that any linux distro need in order to work.the /home partition will basically be his for data as most apps will be installed to / or a folder in / (also referred to as root)

Halitech's suggestion is good advice, but it is not "the minimum." It is also possible to install with just a / partition (which contains /boot and /home) plus a swap partition. 

Here is a guide to setting up partitions: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by adudutz on 2008-07-30
oh, when selecting wether installing the boot loader, what should I select? My dad plans to take off the hdd that contains XP, so I think some tweak is needed there.

---

### Post by snowpine on 2008-07-30
ps I agree with the Xubuntu suggestion if speed is a priority at all, though Ubuntu should work too if you use the Alternate CD. You don't have enough ram to use the Live cd.

---

### Post by halitech on 2008-07-30
> **snowpine said:**
> Halitech's suggestion is good advice, but it is not "the minimum." It is also possible to install with just a / partition (which contains /boot and /home) plus a swap partition. 

Here is a guide to setting up partitions: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

you are right, pardon me, I'm just used to setting my systems up that way due to larger drives and old BIOSes (with no updates available that I can find) so automatically think its normal to go /, /boot, /home and swap. It is good practice though to use a seperate /home partition.

---

### Post by halitech on 2008-07-30
> **adudutz said:**
> oh, when selecting wether installing the boot loader, what should I select? My dad plans to take off the hdd that contains XP, so I think some tweak is needed there.

if he is thinking about removing it, I would remove it before you install and then when he wants to use it, connect that drive and disconnect the ubuntu drive (if he is comfortable with doing that)

---

### Post by adudutz on 2008-07-30
is there any other solution than removing and placing again??

Oh, about the /boot. It is necessary?

---

### Post by halitech on 2008-07-30
you can take the windows one out, get ubuntu installed, reinstall the windows drive and then I've heard of a way of modifying the windows boot file to include ubuntu (never done it but seen an example) and then he can just select which he wants. the other option would be to use the Grub Super disk (I think thats the right name) to install grub.

not neccessary but won't hurt if you do have it

---

### Post by adudutz on 2008-08-03
Here's what i've done:

I removed the 1st HDD, formatted the 2nd HDD, installed Ubuntu with the configuration you've given before, and it worked!

I think the problem has solved

---

