---
title: "SOLVED   Ubuntu 12 (32 bit) boots to scrambled screen when attempting to install"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by jim36 on 2014-01-30
Good day folks, and others,

Newbie to Ubuntu but not to Linux.  Trying to boot the DVD to an older PC (plenty of power and ram).

Once the 'install' goes to X the display scrambles (top half of the monitor) and that's that.

This also occurred with Mint 16.

Thoughts anyone?

Thanks of course,

Jim

---

### Post by jim36 on 2014-01-30
Additional information:

PCLinux installs just peachy.

Go figure.

---

### Post by squakie on 2014-01-30
There is another image to try - it is called the alternate install cd and you download it from Ubuntu.  It installs Ubuntu as normal, but the installation process itself uses "terminal" graphics and is text based, so it gets around some of those initial problems.  Once installed, if you boot and still have problems post back and we can work on it from there.

---

### Post by jim36 on 2014-01-30
Thanks for the reply Squakie, I appreciate it.

Btw, the machine has an S3 based (Savage) video built in to the motherboard.  That's what I'm using right now.

I'll d/l and give the alternate a try.

Thanks again,

Jim

---

### Post by jim36 on 2014-01-30
Well, that ISO (default) worked for install but once it rebooted it went into hysterics again with the top half of the monitor making SOME sense and the bottom half a wild and crazy.

SO, without doing anything I shut down and installed my GeForce 5200 and rebooted.  Viola!  No driver, nothing,  just works peachy.

NOW I shall retry a cold install with Mint and see where THAT goes.

Thank you again.

Jim

---

### Post by squakie on 2014-01-30
If it's S3, your options are limited.  Those graphics adapters have been rather notorious. If it says something like S3 Virge or something with the word "Chrome" it in, it is limited and most likely won't run with the "heavier" desktop managers.  I'm not even sure if x really has much support for it or not. There at least used to be an OpenChrome project to try support them but I don't know if that even still exists.  It's been MANY years ago now, but I had a Gateway laptop that had a S3 gpu, and it would not support 3D.  I think what you are running into is an under-powered basically non-supported video issues, with not a lot of options.  You may want to try xubuntu or lubuntu - they use different desktop managers and are a little "lighter" than "regular" Ubuntu.  I don't know if they'll be any better.  Try the install disk(s) and just do the "Try" without installing option and see if you get a better screen or not.   That's *IF* you want to try to get it working with the S3 (I personally wouldn't waste my time with it given the limited results).  If you have a working solution now with a different video adapter that is your best bet.

EDIT:  just noticed where you said the S3 was Savage - you really won't have any luck with that at all.

---

