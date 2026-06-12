---
title: "The miserable state of graphics cards &amp; OpenGL performance"
date: 2012-12-29
forum: Recurring Discussions
---

### Post by PC_load_letter on 2012-12-29
I am furious to say the least. I am building an Ubuntu desktop PC to use for high performance computing, i.e. modeling, running Physics & Engineering simulations...etc. I got everything figured out in a couple of hours, processor, ram, mobo...EXCEPT the graphics card, and I hate to say that the picture is not bright for the linux user, here is how it goes:

**DISCLAIMER:** if you find any of what I say here inaccurate, I will be delighted to hear the correction.

- It's a linux box, so I'll opt for Nvidia, as AMD linux driver support is not up to par, not yet, and it seems like it never will (didn't they downsize the linux driver team during the last economic recession? + they don't have any plans yet to support Wayland). 
Anyway, so I googled for the latest and greatest Nvidia card and I expected top OpenGL performance, not so fast :D 

- So it was probably a 'brilliant' idea from a marketing intern. Nvidia now has two distinct lines of products, the GeForce gaming line and the Quadro professional line. And even if two cards from these different lines have the same exact GPU chip, the OpenGL (double precision) performance of the GeForce line have been intentionally crippled (to the stone age) to the point that a 3-4 yrs. old GeForce card will have noticeably better OpenGL performance. 
Nvidia puts it like this, well, the Quadro drivers are a result of long and expensive R&D to fine-tune the performance. The equivalent Quadro card is like 2-3 times as expensive! And no you can't install the Quadro driver on the GeForce, if you do, the GPU detects it and starts infinite looping with itself until the machine freezes. 

- The point of this rant is that I am not seeing too many people unhappy about this, so I'll just bite the bullet I guess. It feels really bad that the choice I have is like a $600 Quadro card or a $50-100 3-4 yrs. old Geforce, I mean come on!

- Another issue that gave me some grief is that nowhere I could find any usable OpenGL benchmarks. After some searching, I found the SPECviewperf, and I don't see it that popular. The benchmarks I see at Phoronics are all games.

Your thoughts?

---

### Post by PC_load_letter on 2012-12-29
In a more ironic development, I was reading consumer reviews @ newegg.com and found [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133353&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo").

In the last review, Nvidia commented that one needs to install the performance drivers to get the performance boost expected in the Quadro series. Well, went to Nvidia's web page and I found 3 or 4 performance drivers for the Quadro 2000 card, guess what, non of them is available for Linux 32 or 64 bit. So, it's pretty much settled for me I guess.

I just hope that this situation will change given the growing number of professional Linux users out there.

---

### Post by Sef on 2012-12-30
Moved to recurring discussions as nothing is new about graphic cards and Linux.

---

### Post by bird1500 on 2012-12-30
I'd say open such a thread on phoronix, I heard Nvidia only supports Linux well because it has corporate clients doing HPC, and now that you're saying the high performance drivers aren't available for Linux I'm completely puzzled. The phoronix folks are more benchmark oriented so they might have good ideas, and rants of course, who doesn't like rants - they're 99% of all the fun in the internet.

---

### Post by JDShu on 2012-12-30
I'll respond to OP's random points with more random points.

Regarding AMD, the layoffs involved the linux kernel and by extension, probably the AMD CPU work. The GPU team AFAIK has been unaffected.

There seems to be some noise about NVidia open sourcing their Tegra work.

GPU programming is very hard. Older cards often have better drivers because they've been in development for longer.

Phoronix has a bunch of benchmarks you can look at. You can also take a look at the related OpenBenchmark site. Finally you can run the phoronix test suite yourself. It is what the open source developers use.

---

