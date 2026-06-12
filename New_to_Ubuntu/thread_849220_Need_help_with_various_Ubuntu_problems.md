---
title: "Need help with various Ubuntu problems"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by SpinDizzyMR on 2008-07-04
I've had it for about a week, and I've done practically nothing at all on it.

All my time on Ubuntu is spent fixing problems. 

Even installing it was a big problem, after trying the 8.10 CD and the 8.10 alternate, then trying a dozen odd commands on the cd to get it to install, my friend said he could never get the 8.10 cd to work either, recommended using the 7.10 cd and upgrading.

So I downloading and used that instead in the end, and after finally making it burn with no errors at slowest speed it worked a treat, great.  Though the latest 8.10 linux kernal doesn't work, have to use the second latest 8.10 linux kernal.  Don't know if I'm missing much.  But I tried everything I could find to fix the ATA2 problem that stops it booting.

These forums themselves helped me fix about 20 odd problems, would never have even bothered getting as far as I have without them.  Got  multiverse/packs installed, got flash working, got gstreamer uninstalled and vlc player installed and working (though its not working properly, video playback flickers for anything, though dont know what to do about it yet).  ATI drivers working, wine working etc... all thanks to you guys.

Though everytime I fix something, something else breaks, about the 3rd time now I can't get Ubuntu to boot at all through error messages. (2nd time was when computer froze installing a new program which broke something called dkts or whatever its called, and 1st time, can't remember, fixed it anyway thx to these forums)

ANYWAY I'LL GET TO THE POINT. :D 

Current problems.

Before booting broke, the internet connection would disconnect and stop working after about 20 minutes, it's a usb modem and I think one of the boot error messages is to do with it.

Before booting broke, the sound had stopped working, used to work on every other boot, now it appears to not be working at all again, SoundBlaster Audigy is the card I use.

Desktop wallpaper and desktop right click command menu would sometimes not load at all on boot.

Firefox sometimes unresponsive.

Error messages currently shown that are stopping computer from booting;

modprobe error wifi ubuntu/wireless

usb dev desc read/64 error 110 c-2

Before boot broke on restart attempt I would get a recurring error involving the line

rt2x00usb_vendor_request

The error which actually appears to break the boot process though is:

vm.mmp_min_addr unknown key.

I don't know why I punish myself when I could go back to Vista and it works no problem.  I probably enjoy this. O_o

---

### Post by Canis familiaris on 2008-07-04
Did you try updating 8.04 to 8.04.1. It has numerous bug fixes. If you are already using Hardy you could update to 8.04.1 using the update manager

EDIT: LOL! You are using Intrepid! I'm really stupid not to read your post properly. ANyway 8.10 is an ALPHA 1 release and not for productive machines.

---

### Post by Archmage on 2008-07-04
8.10 should only be done by experts they know that they can expect a lot of problems. Normal user like 99.99999% should get the 8.04(.1).

---

### Post by hyper_ch on 2008-07-04
I agree with archmage:

Ubuntu 8.10 Intrepid Ibex is an Alpha 1 release... do not use it in a productive environment.

---

### Post by Canis familiaris on 2008-07-04
> **Anurag_panda said:**
> Did you try updating 8.04 to 8.04.1. It has numerous bug fixes. If you are already using Hardy you could update to 8.04.1 using the update manager.

EDIT: LOL! You are using Intrepid! I'm stupid not to read your post properly. ANyway 8.10 is an ALPHA 1 release and not for productive machines.

---

### Post by Paddy Landau on 2008-07-04
> **Archmage said:**
> 8.10 should only be done by experts they know that they can expect a lot of problems. Normal user like 99.99999% should get the 8.04(.1).
LOL...

99.99999% of the current world's population is about 670 people. It must be a problematic version!

I'll stick with 8.04.1.

---

### Post by t0p on 2008-07-04
> **SpinDizzyMR said:**
>  

Even installing it was a big problem, after trying the 8.10 CD and the 8.10 alternate, then trying a dozen odd commands on the cd to get it to install, my friend said he could never get the 8.10 cd to work either, recommended using the 7.10 cd and upgrading.

Is this a typo? Did you mean 8.04?

Because if it's not a typo - if you are running version 8.10 - that could explain a lot. The current version of Ubuntu is 8.04, Hardy Heron.  8.10, Intrepid Ibex, is an alpha or testing release. Intrepid is in no way meant to work properly yet.

> **SpinDizzyMR said:**
> 
I don't know why I punish myself when I could go back to Vista and it works no problem.

Well, you certainly could do that.  Though I've got to ask: if Vista works "no problem", why did you decide to try Ubuntu?

The last Microsoft Windows distro I used was XP (I've still got it on a partition, though I haven't booted it since I installed Gutsy).  XP certainly didn't work "no problem" for me. And the problems I had weren't all to do with the way the OS did or didn't work - I have a major problem with Microsoft, and Ubuntu's philosophy fixes *that* problem nicely.

Maybe you own hardware that belongs to the small group that won't work with Ubuntu. Or maybe your problems stem from using 8.10 instead of 8.04. But if none of those are applicable, chances are your issues are fixable and you'll soon be wondering why you ever had doubts.

And if you do decide to junk Ubuntu and rejoin the Vista crowd... well, part of the freedom of Free software is the freedom to kick it into touch whenever you want. You can always come back at a later date, when you decide again that Microsoft ain't for you.

Good luck!!

---

### Post by Sef on 2008-07-04
>  Originally Posted by SpinDizzyMR  View Post
I don't know why I punish myself when I could go back to Vista and it works no problem.

You should use what you prefer.

---

### Post by SpinDizzyMR on 2008-07-04
> **Anurag_panda said:**
> Did you try updating 8.04 to 8.04.1. It has numerous bug fixes. If you are already using Hardy you could update to 8.04.1 using the update manager

EDIT: LOL! You are using Intrepid! I'm really stupid not to read your post properly. ANyway 8.10 is an ALPHA 1 release and not for productive machines.

OMG I'm so sorry, it is 8.04.

I'm stupid not you, well nvm.  I'll try and be clearer instead of rambling. *Grabs camera*

The latest kernal in 8.04 has never worked for me.  It loads very slow, says cannot find devices retrying, both recovery and normal on eventually fail on ALERT! /dev/disk/by-uuid/xxx-xxxx-xxxx-xxxxxxxxx does not exist. Dropping to shell.

[[IMG]http://img225.imageshack.us/img225/810/snapshot200807047rk2.th.jpg[/IMG]](http://img225.imageshack.us/my.php?image=snapshot200807047rk2.jpg)

I use the 2-6-22-14 kernal usually, but something is failing at the moment, and here is the output on the screen.

[[IMG]http://img301.imageshack.us/img301/3083/snapshot200807045ya7.th.jpg[/IMG]](http://img301.imageshack.us/my.php?image=snapshot200807045ya7.jpg)

---

### Post by bumanie on 2008-07-04
There are at least three later kernels - may be they will work better, may be they won't, but I would download via updates if I were you. You should go to System --> Administration --> Software Sources and enable the first 4 boxes, then click on third party and enable the first canonical box. I think you may not have enabled your software sources properly and you should find a lot of updates.

---

### Post by steveneddy on 2008-07-04
> **Sef said:**
> You should use what you prefer.

Agreed.

So, what are your hardware specs?

---

### Post by nothingspecial on 2008-07-04
If I may butt in here.
I upgraded to 8.04 3 or 4 weeks ago and found it to be very buggy so I reinstalled 7.10 which works like a dream and is still supported. If you still have the 7.10 disk give it a go.

The thing is, if you`ve fixed alot of problems like you`ve said then you`re on your way to be an experienced linux user. I`ll bet you know a lot more about computers than you did when you stared this venture and by the time you sort your self a system you are happy with you`ll practically be an expert.

Soon you`ll be able to install Ubuntu on any computer you like with confidence, knowing that even if something dosen`t work, you`ll be able to fix it (with a little help here).

I spent weeks trying to get sound working on a laptop, I thought I`d tried everything but the answer was here all along. When I eventually found it the sound of those drums at the login screen was amazing.

I reckon it`d be kind of a waste to give up on something you`ve invested this much time in, (I wouldn`t blame you though). I say give gutsy ago, from what I understand it`ll be alot easier than installing windows.

---

### Post by hyper_ch on 2008-07-04
> **SpinDizzyMR said:**
> The latest kernal in 8.04 has never worked for me.  It loads very slow, says cannot find devices retrying, both recovery and normal on eventually fail on ALERT! /dev/disk/by-uuid/xxx-xxxx-xxxx-xxxxxxxxx does not exist. Dropping to shell.

did you alter your partitions?

---

### Post by nowshining on 2008-07-04
if u want - u can try installing an un-patched kernell from kernel.org - the latest 2.6.25.x altho it seems to get frequent updates - withing days, week, etc..

I suggest installing the 2.6.24.7 kernel - leave all at default - it's quite easy to make, install a kernel. :), that way u won't get any of ubuntu's patches which may be the source of ur problems.

---

### Post by Threbus5 on 2008-07-04
I can sympathize with you.
Version 6.0 was the most recent Ubuntu version that worked 100% for me. Since then either the hardware was too new or services unsupported.

I agree with several of the postings, that is, learning about Linux is good and worthwhile. But, without a usable system that behaves in a consistent manner, a computer provides only a learning platform.

It seems more reasonable to learn and work, than to just learn.
So, perhaps it would be helpful to have a stable installation for your work tasking and an experimental installation to maintain fault isolation skills?

However, sometimes a previously reliable OS performs poorly on new hardware. That is my present situation.
Good luck on making the best OS decision for your circumstances.

---

### Post by SpinDizzyMR on 2008-07-04
Right I missed some things out.  (Such nice people here btw, love reading and posting on this forum)

Anyway I better give out some physical specs. 

Was a custom build, from just before Christmas roughly I think.

Amd Athlon Dual Core 5000+
Asus MVP Motherboard.
Ati Radeon 3850
2 gig DDR 2 ram.
SATA 250 gig hard drive. 

Vista is on 190 gig to itself, Ubuntu is running on a 60 gig partition on the same hard drive for the moment with 4 gig swap space (maybe a lot for swap space but I like to make sure :p)

Sharing with Vista might somehow cause problems you think?

But anyway, I cannot boot into any hard drive saved ubuntu at the moment, and live cd wont give me admin rights. 

I dont know how to fix either of these problems with these currently two broken ubuntu kernals in order to load them and get an update so I'll either have to hope someone gives me some code to disable or fix the damage or I'll reinstall 7.10 from live cd I think?

It's just I'm really against a reinstall at the moment since I've been doing a ton with the terminal and was starting to get somewhere. :(

Yes it has been a learning experience, although Vista is really stable and works great for games, I find Ubuntu to actually be more desirable to myself as a work based OS.  I also can't stand the controls on Vista either.  I find it a bit too condescending at times. 

As a friend once put it.  "Vista is like a shiny new sports car with the hood welded shut" With a smiley face and a support number in the instruction manual"

If Ubuntu could run all the AAA game titles and the software wasn't all a conflict risk and it could switch processes and minimize seamlessly it'd be worth all the trouble. :)

The way I see it, Linux and such are catching up with windows anyway.

---

### Post by hyper_ch on 2008-07-04
well, in your /etc/fstab you try to identify the partitions with their UUID and when you alter partitions then the UUID changes... that's why I asked... obviously the UUIDs have changed and hence it can't find them anymore...

(1) boot up the desktop cd

(2) mount the "/" root partition

(3) edit the /etc/fstab file

(4) alter the /dev/disk/by-uuid=kkkkkkkkkkk to /dev/sdXY (replace of course YX with the according partition devices)

---

### Post by SpinDizzyMR on 2008-07-04
Ahahahah, weird, I couldnt seem to be able to mount the drive and edit it from the live CD (prob lack the coding know how) 

I already got the main 4 boxes ticked for software updates, wasn't sure about for 4th canonical box, so I ticked 7.10 drivers or something. 

Anyway.

I booted the older 8.04 kernel i use in recovery mode then deleted the UUID string from SDA2 (my linux partition, sda1 is vista, sda3 is swap file).  and then went back to recovery console and said continue boot.

...and low behold it boots up fine with sound working and everything O_o 

Even firefox currently running for 30 min without a single freeze or greyout yet O_o.  (usually always snags on youtube) wont count my chickens though.

It must have fixed something for it to boot though, maybe deleting the UUID string made it have to reallocate a new correct UUID or something?

Now all I gotta do is fix flickering in vlc player and get that other later 8.04 kernel working maybe? :p

Hmm actually, vlc isn't flickering in fullscreen mode, I can probably live with that. *grins*

Although no sound on vlc player, though sound on everything else, still quite happy atm that im back where I was.

---

