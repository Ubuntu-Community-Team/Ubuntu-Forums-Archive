---
title: "Wacom bamboo connect ctl470 help"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by atrahasis on 2011-12-07
Hi, I'm running Ubuntu 10.10 and I just purchased a WACOM Bamboo Connect - Pen (CTL470) and it doesn't seem to be registering.

It lights up when I plug it in and when I run lsusb, it says it's in the "Bus 004 Device 002: ID 056a:00dd Wacom Co., Ltd"

I searched on-line and I tried several suggestions. I ran several codes, rebooted, I tried one of the suggestions at [http://askubuntu.com/questions/80637/wacom-bamboo-connect-ctl470-no-tablet-detected](http://askubuntu.com/questions/80637/wacom-bamboo-connect-ctl470-no-tablet-detected)

And i still doesn't work. I'm not too computer savvy with codes and terminal but any kind of help would be appreciated.

Also, can the tabet replace the mouse completely?

---

### Post by Favux on 2011-12-08
Hi atrahasis,

Welcome to the Ubuntu forums!

The third generation BambooPT's like yours were just released this October.  Despite this support for them is already available.  Unfortunately the support is only for Natty, the 2.6.38 kernel, and later, i.e. Oneiric.  So they aren't working in Maverick.

You would want to compile input-wacom-0.12.0 and xf86-input-wacom-0.12.0 as part I. and II. in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") shows you.
> Also, can the tabet replace the mouse completely? 
Sure, with just the stylus pretty much.  You might want to add EasyStroke to the mix since you won't have a scroll wheel.  Although the stylus + touch models are probably a better choice.

---

### Post by atrahasis on 2011-12-08
Thanks for the reply.

Is there a way to do this? I downloaded those packages  only to get stuck afterwards. This was 30 minutes ago. I just bought this earlier today and never used  one before.

I really  don't know what to do. The instructions are alien to me. I'm about to install Ubuntu Studios or upgrade to 11.04 (which I don't want to). What would be the best thing for me to do?

Should I just stick to pen and paper?

---

### Post by atrahasis on 2011-12-08
If I upgrade from 10.10 to 11.04 will it fix the problem also, when you say "NATTY", does that include the Ubuntu Studios version and would the studio version be supported?

---

### Post by Favux on 2011-12-08
I don't blame you for wanting to stick with Maverick.  That's my current favorite release too.

There would be a Studio version of Natty and the compile should work on that too.

If you can return the tablet and get your money back is the old first generation BambooPT Pen (CTL460; Product ID = 0xd4)  available?  I think the spec.s are similar and you could check.  Or are there Bamboo Ones available?  They're basically the same thing, but also check their spec.s.

Whatever you decide you'll still need to compile a wacom.ko to get them working in Maverick.  It's not that hard.  The instructions are step by step and you just copy and paste them into a terminal.  Just skim through them a couple of times until you get the idea.  The fact that it is all new makes it seem like more than it really is.

Updgrading to Natty will allow you to compile a working driver for your current Bamboo Pen tablet.

---

### Post by atrahasis on 2011-12-08
I was looking over Ubuntu Studios and it mentioned that it comes with wacom-tools so that  it works with a variety of brands. I mounted the .iso on a usb stick and it doesn't load. I have a CD and it doesn't fit apparently and I can't use a DVD because my computer is DVD read only. If I upgrade to Natty, will I be able to customize my desktop how  I want?

---

