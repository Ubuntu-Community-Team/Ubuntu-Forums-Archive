---
title: "Swapfile disappeared, cannot suspend or hibernate PC"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by mayoman on 2013-03-22
Have been renning xubuntu 12.04 on my old dell 4400 dimension desktop for a few months with no issues. It became intermittently very sluggish in the last few days & when I noticed "suspend" button disappeared from the logout window I discovered the swapfile had disappeared.
Manually created a new 1G swapfile per [https://help.ubuntu.com/community/SwapFaq#addswap](https://help.ubuntu.com/community/SwapFaq#addswap)
New swapfile seems to be working fine - running the free command in terminal gives something like:[INDENT][FONT=courier new]            total       used       free     shared    buffers     cached
Mem:        766340     711836      54504          0     122544     166428
-/+ buffers/cache:     422864     343476
Swap:      1048572        156    1048416[/FONT]
[/INDENT]

However it still will not suspend, now gives a "No Kernel Support" error when I try. Havent seen any major crashes & only recent software installs have been the regular ubuntu updates. Not sure where to proceed from here short of entire re-install & would appreciate any pointers.

---

### Post by mayoman on 2013-03-24
Update - The suspend/hibernate issue was not the end of the world, but of more concem was that recreating the swapfile did nothing for the general clunkiness of performance. Most importantly (for my wife anyway), it could no longer stream videos smoothly. I booted to 3.2.0-38-generic kernel this morning (from 3.2.0-39), and hey presto everything runs smoothly again! (and suspend is back!) So obviously things must have gone a bit haywire in the most recent update. Next question - how do I force re-install of the 3.2.0-39 kernel?

---

### Post by coldcritter64 on 2013-03-24
> **mayoman said:**
> Update - The suspend/hibernate issue was not the end of the world, but of more concem was that recreating the swapfile did nothing for the general clunkiness of performance. Most importantly (for my wife anyway), it could no longer stream videos smoothly. I booted to 3.2.0-38-generic kernel this morning (from 3.2.0-39), and hey presto everything runs smoothly again! (and suspend is back!) So obviously things must have gone a bit haywire in the most recent update. Next question - how do I force re-install of the 3.2.0-39 kernel?
That sounds like you ran the update-initramfs command on only one kernel when adding the swapfile.

The command "sudo update-initramfs -u" given in the instructions you linked to will only update 1 kernel, adding the switch "-k all", will update all kernels, eg
```
sudo update-initramfs -u -k all
```

I would update all the kernels then reboot into 3.2.0-39 and see if that helped, if not I'd look into bugs on launchpad etc.

Edit: re performance, what "swappiness" setting have you set the system to ?

---

### Post by mayoman on 2013-03-24
> **coldcritter64 said:**
> That sounds like you ran the update-initramfs command on only one kernel when adding the swapfile.

The command "sudo update-initramfs -u" given in the instructions you linked to will only update 1 kernel, adding the switch "-k all", will update all kernels, eg
```
sudo update-initramfs -u -k all
```

I would update all the kernels then reboot into 3.2.0-39 and see if that helped, if not I'd look into bugs on launchpad etc.

Edit: re performance, what "swappiness" setting have you set the system to ?

Did not run the sudo update-initramfs command as it said in the post above that section that it will not work in 12.04 (which I'm running). As I do not have a swap partition I just followed the "4 step process to add a swapfie" section. I did verify it worked in 3.2.0-39 & is working in 3.2.0-38 today.
I played with the swappiness as well but it did not make a difference (everything from 10 to 90). I was on the default 60 before this issue started. I have just checked and am now at 40 which was the last value I tried. I am pretty sure that more than just the swapfile got screwed up in the 3.2.0-39 kernel. Also, it should be noted the pc is borderline on video streaming at the best of times (Xp and Ubuntu are too slow, Xubuntu streams SD ok, but not HD), so it would not take much to kill streaming performance!

---

### Post by coldcritter64 on 2013-03-24
What sort of hardware specs are you talking on the Dell you have, RAM, processor etc ? If it struggles with xubuntu, sounds very limited in resources.

---

### Post by mayoman on 2013-03-24
> **coldcritter64 said:**
>  If it struggles with xubuntu, sounds very limited in resources.

Intel(R) Pentium(R) 4 CPU 1.60GHz
768MB RAM 

Yes very limited! To be honest, I installed linux purely to put off the day I need to buy a new PC. 

Bottleneck as I see it is the CPU & ancient motherboard architecture, so, as long as Xubuntu can stream SD ok I'll keep it going. Otherwise I'll have to splash the cash!

---

### Post by matt_symes on 2013-03-24
Hi

I would have installed Lubuntu on that machine with those specs.

Kind regards

---

### Post by mayoman on 2013-03-24
Yeah, for us beginners a table or form of PC spec v suitable OS would be great to point us in the right direction. When I was looking at the various options it just said Xubuntu or Lubuntu for older slower machines. I went from Xp to Ubuntu (which was no better at streaming), to Xubuntu - which was much better and left it at that. More importantly the Xp-Xubuntu transition was easy for my non-tech wife. Not sure how she would take another transition to Lubuntu :)

EDIT: Of course what I should have said was that the Xp-Xubuntu transition was easy for me (to teach my non-tech wife). "Start menu is top left instead of bottom left, use thunderbird instead of outlook for email," Tutorial done!

---

### Post by mayoman on 2013-03-28
Update: Tried uninstalling & reinsalling 3.0.0-39 kernel but no change, so staying with 3.2.0-38 for the moment.
Ran the following commands:
```
sudo apt-get remove linux-image-3.2.0-39-generic
sudo apt-get update
sudo apt-get install linux-generic linux-headers-generic linux-image-generic
```

Not sure if that is enough or if I should delete everything to do with the 39 kernel?

Or maybe I should give up & take Matts advice:)
> I would have installed Lubuntu on that machine with those specs.

---

