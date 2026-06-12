---
title: "Extra Ram causing problems."
date: 2008-11-23
forum: New to Ubuntu
---

### Post by kaspar_silas on 2008-11-23
Hi All,

Bit of a mystery here. I will describe the issue as completely as I can in the hope someone knows what is going on.

I am running the 32 bit desktop Ubuntu 8.10 on a Dell optiplex 755. I needed to up the RAM a bit for some work I do. So I bought 2 x 1gb modules to go to 4gb (I bought those suggested by the crucial memory site for my model).

I put the RAM modules in and rebooted. I then got the following:

-A start up message saying the hardware had disabled restart. 
-An odd message saying "no resume image doing init boot". 
-A text login screen appears, this flashs thee times.
-A pop up box appears saying the Nvidia driver is not correct switching to low graphics mode. (I actually have other options but I have to agree to switch to continue.)
-Some more flashing, a black cross and then the graphical log in screen. 

To attempt to solve this I tried fixing the swap partition (which fixed the no resume image bit). I then tried installing Nvidia. However this was a bit of a, m, failure. I tried Envy, Nvidia own installer and activating the driver in gnome and using nvidia-xconfig. All report success but on rebooting I load up back in the low graphics mode.

If I remove the RAM, the weird start up messages go away and installing nvidia drivers is no problem. 

I am away until tomorrow but I thought I would post this now so I can start on monday with some new ideas.

So anyone any thoughts? Any help is really really appreciated.

O, I just started a running a memory test but this seems unlikely to be the cause.

---

### Post by kaspar_silas on 2008-11-23
Sods law in action. No sooner had I posted it that I found

[http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/]("http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/")

---

### Post by kaspar_silas on 2008-11-24
Ah! Spoke far too soon. 

[I have now upgraded to the 64 bit Ubuntu but that doesn't help either].

It seems that according to this discussion
[http://www.nvnews.net/vbulletin/showthread.php?t=113682]("http://www.nvnews.net/vbulletin/showthread.php?t=113682")
the NVIDIA drivers don't support 4gb of RAM is this correct?

 A kernal patch (?) is given on page 2 but to be honest what this is totally baffles me.

Is there any chance someone could have a look at it and tell me if this is okay for my kernel (2.6.27-7)

Many thanks for any help

---

