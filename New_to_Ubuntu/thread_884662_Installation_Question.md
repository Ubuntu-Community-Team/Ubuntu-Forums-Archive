---
title: "Installation Question"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by melrom on 2008-08-09
Sorry to be vague in the subject. lol.

Basically, I'm installing Ubuntu on this computer, which has 2 40 gig hard drives. I'm 95% sure there's no RAID controller though, which means the hard disks are showing up as dev/sda and dev/sdb. Is there any way to simulate these two as being RAIDed so I can install Ubuntu onto 80 gigs instead of 40?

---

### Post by phidia on 2008-08-09
The Ubuntu installation wiki has a subsection titled > [Installing on external or RAID hard disks.]("https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks") You might want to give that a look over-there is a topic there on fake RAIDs that might be what you want. 
If you have more questions or that doesn't provide what you wanted by all means add additional questions to the thread.

---

### Post by bpowell2005 on 2008-08-09
> **melrom said:**
> Sorry to be vague in the subject. lol.

Basically, I'm installing Ubuntu on this computer, which has 2 40 gig hard drives. I'm 95% sure there's no RAID controller though, which means the hard disks are showing up as dev/sda and dev/sdb. Is there any way to simulate these two as being RAIDed so I can install Ubuntu onto 80 gigs instead of 40?

How about a LVM setup? I haven't done this on Ubuntu, but my Mythbox has an LVM setup, and it's great...when I want to add more storage, I just drop a new Hard drive in, add it to the LVM, and my LVM grows accordingly.

---

### Post by hyper_ch on 2008-08-09
you can do LVm setup like bpowell2005 suggested. However there seems to be a bug when using LVM on encrypted drives and then trying to upgrade it.

---

### Post by bpowell2005 on 2008-08-09
> **hyper_ch said:**
> you can do LVm setup like bpowell2005 suggested. However there seems to be a bug when using LVM on encrypted drives and then trying to upgrade it.

Hyper_ch,

I didn't know about that bug! I never bothered to encrypt my Mythtv drives...if somebody wants to steal my episodes of Scrubs and NCIS, then hey, they must need them more than me! :)

I actually haven't played with an encrypted installation yet, but I plan to do that on my next Ubuntu install!

---

### Post by hyper_ch on 2008-08-09
it might already be fixed in Ibex...

---

