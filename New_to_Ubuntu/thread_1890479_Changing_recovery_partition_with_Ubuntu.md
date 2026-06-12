---
title: "Changing recovery partition with Ubuntu?"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by justdoit2011 on 2011-12-03
I've been spending the last few days trying to recover windows on this Acer Aspire One 722 netbook I bought recently. 

Right now I'm trying something I saw suggested on another forum which requires me to dl Ubuntu (I'm using 11.04) and then use Nlite to slipstream some appropriate drivers onto a recovery disk...or something.

I have tried to download Ubuntu so that I will no longer need to have the live CD running, but each time I try to dl it tells me I do not have the 4.4gb of required space to do this.  

Someone on another forum mentioned changing the recovery partition, but I don't know how to do this on Ubuntu.

I'm not a techy person, so a somewhat layman walkthrough of the procedure to do this would be very much appreciated. 

Thank you for any help.

---

### Post by Mark Phelps on 2011-12-04
You can't "change the recovery partition" using Ubuntu. The partition (if it actually exists is in a fixed location on your drive -- where the OEM put it in the first place -- presuming that it came preinstalled with Windows on it.

Don't know what comes preinstalled on a netbook, but if you removed the recovery partition, there is basically no way to get it back.

What do you have on your netbook at present? If you're not sure, then open a terminal in Ubuntu and enter "sudo fdisk -lu" (lowercase L, not a one).  This will list out the partitions on your drive -- and let us see if there is a recovery partition there.

---

### Post by mapes12 on 2011-12-06
> I've been spending the last few days trying to recover windows on this Acer Aspire One 722 netbook I bought recently. Part of the solution may be based on what version of windoze you need to recover. If you have an installation disk and a genuine windows activation code then that should do it. There may be a recovery partition but as the previous post commented you need to run the Terminal command to see what's on the HDD.

> I have tried to download Ubuntu so that I will no longer need to have the live CD running, but each time I try to dl it tells me I do not have the 4.4gb of required space to do this. I wouldn't install Ubu until you have your windoze installation back as you want it. Boot from the UBU Live CD to recover any files you need to keep to external media then start the recovery work.

> if you removed the recovery partition, there is basically no way to get it back.In normal circumstances this is correct but it depends on how important the stuff is you want to get back and if you're prepared to pay for a solution. Here's a starter for 10:-

[http://www.runtime.org/](http://www.runtime.org/)

If you can live without windoze then why not run the machine using Ubu?

---

