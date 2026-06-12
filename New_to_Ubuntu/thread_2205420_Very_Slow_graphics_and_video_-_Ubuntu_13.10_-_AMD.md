---
title: "Very Slow graphics and video - Ubuntu 13.10 - AMD"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by Peter_Storm on 2014-02-13
Hi there;

I'm new to Ubuntu and Linux.

My trouble is with the speed I'm getting (I know something might be very wrong: slower than Windows is not an option :S )

I'm running Ubuntu 13.10 aside Windows 7 Ultimate.

Trouble is, the graphics are Very slow, and the videos (Yotube and other Flash) are very poor, with a kind of "lag".


I would also want to know how to boost the whole set I have - it's not the best, but:

AMD Dual-Core E1-2500
8Gb RAM
AMD Radeon HD 8240

Any help, please?!


Thanks!!!

---

### Post by ubudog on 2014-02-13
Hi Peter_Storm,

Have you installed any proprietary drivers for your graphics card yet?
If not, have a look in Software & Updates, under the Additional Drivers tab.

---

### Post by Peter_Storm on 2014-02-13
Hi;I tried to, but went in to a "black screen" dead-end.I'll try it again.Thks

---

### Post by Mark Phelps on 2014-02-14
Don't use the Additional Drivers -- the repository drivers for fgkrx are having problems with the HD 8xxx series.

Instead, go to the AMD drivers site and download the drivers you need.  I did that and installed the AMD Catalyst 14.1 Beta drivers -- and they are working great (on my AMD HD 8500).

---

### Post by Peter_Storm on 2014-02-14
The change for AMD proprietary (fglrx) on Additional Drivers clearly made the trick! Videos are up and running fast.

(I tried before installing AMD Catlyst, but had problems doing so).

Thanks!!!


By the way, is there anywhere where I can find some kind of "boost" for my particular computer?

Thing is, the speed of the processor is very poor (1400), but it's Dual-Core, and it comes with 8Gb DDR3; so maybe there's a special configuration for that?
Or Ubuntu does it all optimized at installation?

[COLOR=#000000]AMD Dual-Core E1-2500[/COLOR]
[COLOR=#000000]8Gb RAM[/COLOR]
[COLOR=#000000]AMD Radeon HD 8240


Cheers!!!!
[/COLOR]

---

### Post by Mark Phelps on 2014-02-14
> so maybe there's a special configuration for that?

No, sorry -- it is what it is.

I've been running various Ubuntu versions on multi-core processors for years, and in all cases, Ubuntu has used all the cores.

---

### Post by Peter_Storm on 2014-02-14
Ok, so now I'm pleased with it;

The slowlyness was on the graphics.


Thanks!!

---

