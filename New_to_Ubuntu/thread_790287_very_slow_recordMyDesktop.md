---
title: "very slow recordMyDesktop"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by akimatsu123 on 2008-05-11
Hi,

I am using the program recordMyDesktop. After trying several screen capturing programs like instanbul(or whatever it is called) and xvidcap, i decided that it was the best program. 

recordMyDesktop worked fine on Gutsy. I mean sure, there is the inevitable slowdown of your computer, but only slighty, and the quality was good so i could live with it. 

but on Hardy, it slows my computer down so much, up to a state where it's barely usable. I would click something, and have to wait for 5 seconds before i get any result. now opening even the terminal takes about 15 seconds. usually it takes a second max. 

how can i fix this? i'm on an ATI driver, if that matters at all. any ideas?

thanks,

---

### Post by diablo75 on 2008-05-11
This kind of software is processor intensive so you should expect slow downs.  There is a settings panel within the program that will allow you to disable features like on-the-fly video compression, as well as decrease the capture frame rate.  Have you tried adjusting these settings?

---

### Post by saundesj on 2008-05-12
I can confirm this. ATI Radeon Mobility 7500 and recordMyDesktop worked fine in Gusty. With Hardy CPU is maxed out. Tweaking performance settings didn't help.

**UPDATE: Disabling Compiz seemed to fix the problem for me. Must just be my ancient video card :)**

---

### Post by pcmac77 on 2008-10-18
I am running 32bit Hardy with ATI Mobility Radeon X1600 with the latest driver from [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) (version 8.10 as of Oct 18, 2008), on Acer TravelMate 8210 with Intel Core Duo2 T7200, Compiz-Fusion enabled.  recordMyDesktop is running very slow, perhaps at 1 or 2 fps.  I have try setting the FPS at 5 or 10, and disabled encoding on the fly.  CPU activity doesn't get that high, maybe at around 30-40% on one core. 

Running recordMyDesktop v0.3.6

Thanks.

---

### Post by jiapei100 on 2008-11-17
Here, exactly the same configuration.

ATI X1600
driver Radeon 8.10
Compiz-Fusion disabled
Intel Core Duo2 T 7200
RecordMyDesktop 0.3.7.3

It's not as slow as 1-2 fps, but no more than 5 fps I think...

Any solution?

Regards




> **pcmac77 said:**
> I am running 32bit Hardy with ATI Mobility Radeon X1600 with the latest driver from [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) (version 8.10 as of Oct 18, 2008), on Acer TravelMate 8210 with Intel Core Duo2 T7200, Compiz-Fusion enabled.  recordMyDesktop is running very slow, perhaps at 1 or 2 fps.  I have try setting the FPS at 5 or 10, and disabled encoding on the fly.  CPU activity doesn't get that high, maybe at around 30-40% on one core. 

Running recordMyDesktop v0.3.6

Thanks.

---

