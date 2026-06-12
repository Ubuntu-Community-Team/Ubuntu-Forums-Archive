---
title: "Xubuntu install issues"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by LoudShirts on 2008-11-28
In a nutshell:

I'm home for the holidays, and I promised my folks that while here, I'd give their ancient PC a little extra life with Xubuntu.  Then while Dad is playing Mah-johng on the newer system, mom can still check her e-mail.  But I've run into problems.

When I say "ancient," I mean "ancient."  The old system is a Compaq Presario 7AP170.  It's got a whopping 128M of ram, a 40G HD and a blistering 900MHz Athlon.  Yeah...I know.  Still, should more than the minimum specs needed to run a trim install like X.  

I have a CD-R burned with the Alternate CD ISO of Xubuntu 8.10, and have tried several times to install it using the text-based interface.  But, annoyingly, it gets as far as the "Detect and Mount CD-ROM" step before swearing up and down that my "installation CD-ROM couldn't be mounted."  Huh.  Well, the bloody disc sure recognized the drive just fine when it booted into the install screen.

I've looked around for a fix for this, but I can't find any that don't require a previous Windoze install (main HD is blank) or that don't assume I know a LOT more than I do.  I've been using Hardy at home for almost six months, and am acclimating fine, but I'm a long, LONG way from compiling my own code.  So...I need some directions from Boston to Miami, please...And if we could refrain from starting in Orlando, that would be much appreciated.   

Thanks in advance for your assistance.

---

### Post by cwsnyder on 2008-11-28
1) Did you check the install CD after you burned it to see if there were any errors, or have you used this same disk to install on another computer, so that we can eliminate this as the source of the problem?

2) Do you have an external or alternate optical drive available to eliminate THAT as the source of the problem?

---

### Post by LoudShirts on 2008-11-28
> **cwsnyder said:**
> 1) Did you check the install CD after you burned it to see if there were any errors, or have you used this same disk to install on another computer, so that we can eliminate this as the source of the problem?

A check of the disc on the Vista system indicates validity.

> 2) Do you have an external or alternate optical drive available to eliminate THAT as the source of the problem?

There is a secondary CD-ROM drive on the system, but it isn't working.  Not sure why.  Won't open up.

---

### Post by wrtpeeps on 2008-11-28
> **LoudShirts said:**
> In a nutshell:

I'm home for the holidays, and I promised my folks that while here, I'd give their ancient PC a little extra life with Xubuntu.  Then while Dad is playing Mah-johng on the newer system, mom can still check her e-mail.  But I've run into problems.

When I say "ancient," I mean "ancient."  The old system is a Compaq Presario 7AP170.  It's got a whopping 128M of ram, a 40G HD and a blistering 900MHz Athlon.  Yeah...I know.  Still, should more than the minimum specs needed to run a trim install like X.  

I have a CD-R burned with the Alternate CD ISO of Xubuntu 8.10, and have tried several times to install it using the text-based interface.  But, annoyingly, it gets as far as the "Detect and Mount CD-ROM" step before swearing up and down that my "installation CD-ROM couldn't be mounted."  Huh.  Well, the bloody disc sure recognized the drive just fine when it booted into the install screen.

I've looked around for a fix for this, but I can't find any that don't require a previous Windoze install (main HD is blank) or that don't assume I know a LOT more than I do.  I've been using Hardy at home for almost six months, and am acclimating fine, but I'm a long, LONG way from compiling my own code.  So...I need some directions from Boston to Miami, please...And if we could refrain from starting in Orlando, that would be much appreciated.   

Thanks in advance for your assistance.

X might struggle with only 128mb of Ram actually.

---

### Post by LoudShirts on 2008-11-28
> **wrtpeeps said:**
> X might struggle with only 128mb of Ram actually.

That's a drag.  I opted for Xubuntu over a full Hardy or Intrepid install based on the lighter architecture, and [this thread](http://ubuntuforums.org/showthread.php?t=643148) seeming to indicate it would be fine...So I hope I'm not way off-base.  

I promised I'd get this thing running before I have to leave for home on Sunday, so I'm still holding out hope for a workaround.  :(

---

### Post by Bartender on 2008-11-28
> **LoudShirts said:**
> A check of the disc on the Vista system indicates validity.  There is a secondary CD-ROM drive on the system, but it isn't working.  Not sure why.  Won't open up.

Not sure how you'd check an alt-install CD on a Vista box.  

I'd open the thing up and see if the 2nd optical drive is plugged in.  Check the cable on the 1st one.  I was screwing around with my testbed PC a while back and managed to pull the data cable to the optical drive partway out.  Windows 2000 was able to use the drive but Ubuntu was not.  Shoved the cable back on and everything was fine.
Optical drives are easy to move around as long as you're familiar with the little jumpers on the back of the drive - I'd borrow another one from some other PC and try that too.

---

### Post by LoudShirts on 2008-11-28
> **Bartender said:**
> Not sure how you'd check an alt-install CD on a Vista box.

I just put it in the drive, booted the machine, and selected the "check CD for defects" option at the install screen.  It scanned the burn, and came back with a valid result.   

> I'd open the thing up and see if the 2nd optical drive is plugged in. 

I checked the power and data cable connections, and they seemed fine.  Tried installing again...Same result.  

A search of some older threads seems to indicate that maybe the drive itself is at fault...like it can't read the CD-R properly.  If that's the case, I can't help but wonder why it boots into the install screen from that drive at all...?

---

### Post by halitech on 2008-11-28
128 meg of ram for Xubuntu is way on the light side, works best with at least 256 but requires at least 192. Does it have a wired internet connection? if it does, you could do a net install of Debian and install XFCE which will run much better then Xubuntu

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by gn2 on 2008-11-28
Here's a download link for [Debian Xfce]("http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-xfce-CD-1.iso")

Another distro to consider is [Zenwalk]("http://www.zenwalk.org/")

---

### Post by ugm6hr on 2008-11-28
While I agree 128MB is probably a little low for Xubuntu, it doesn't explain the problem with installation you're having.

Will the AlternateCD allow you to install a command line system?

If all you are looking for is something to get online, Slitaz is worth investigating - and the LiveCD should work fine with 128MB.

---

### Post by halitech on 2008-11-28
just thought of this, try adding this to the grub boot line

```
ide=nodma
```
and see if that helps

---

### Post by LoudShirts on 2008-11-29
Thanks for the assistance, all.  

Wound up going to my local computer-nerd store up the road from my folks' house.  You know the place...Run by a solitary geek in a storefront, mounds of parts laying around.  Bought a used-but-newer CD-ROM drive for a five-spot and dropped it into the system.  Once I had a newer drive, everything installed like magic!  In fact, I'm on that system now, 128M of memory and all!

The assistance has been much appreciated, and Mom is thrilled.   :)

---

