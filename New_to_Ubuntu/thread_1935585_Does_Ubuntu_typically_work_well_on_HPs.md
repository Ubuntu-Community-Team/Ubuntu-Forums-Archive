---
title: "Does Ubuntu typically work well on HPs?"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2012-03-04
I'm getting a lappy for college, and from the ratings, this one looks great for some gaming and general needs.

[http://www.bestbuy.com/site/HP+-+15.6%22+Pavilion+Laptop+-+6GB+Memory+-+640GB+Hard+Drive+-+Dark+Umber/4815065.p?id=1218533331581&skuId=4815065#tabbed-customerreviews](http://www.bestbuy.com/site/HP+-+15.6%22+Pavilion+Laptop+-+6GB+Memory+-+640GB+Hard+Drive+-+Dark+Umber/4815065.p?id=1218533331581&skuId=4815065#tabbed-customerreviews)

I'm planning on dual booting with Ubuntu on whichever machine I decide to get, and I'm also looking at a few Toshibas.

Is Ubuntu known for installing / working well with HP laptops? How about Toshiba? I guess it would vary from model to model, but I'm sure some brands just work better than others with Linux, right?

---

### Post by Henkdroid on 2012-03-04
HP often partitions the HDDs of their laptops into 4 partitions, this can make installing Ubuntu overly complex. I don't know about Toshiba.

---

### Post by papibe on 2012-03-04
I've had good experiences installing Ubuntu on Toshiba laptop.

Just a thought.
Regards.

---

### Post by Sonsum on 2012-03-04
> **Henkdroid said:**
> HP often partitions the HDDs of their laptops into 4 partitions, this can make installing Ubuntu overly complex. I don't know about Toshiba.

This is very true. Unless you use Wubi, you will probably have to delete a partition to get another OS on there.

I have an HP G62 and I had to delete the system tools partition (I don't think it's really that necessary, but I am no expert) to install Ubuntu.

Besides that though, everything has been flawless (especially once Precise comes out and the better power management from the i-series processors is integrated by default).

---

### Post by iowa_wildcat on 2012-03-04
I am a total newbie to Linux and installed Ubuntu 10.10 as the sole OS on my Toshiba A-305.  The Vista on my Toshiba was so corrupted by trojans that it would not load.  Ubuntu installed easily and correctly on the first try and has worked flawlessly for the last three months.  I installed it on a couple of friends old PCs and they love it also.  Now if we could just get our old Compaq printers to work with Ubuntu......

---

### Post by wildmanne39 on 2012-03-04
Hi, I have used two different hp's with ubuntu over the years and the only issues were setting up the wireless and graphics cards which is not to hard with the help of the forum.
Thanks

---

### Post by daslinkard on 2012-03-04
If it were me and I was looking at dual-booting, whether HP, Dell, Toshiba, etc., I would first create the Recovery Media CD's.  This is important due to the fact the recovery media is no longer provided by the manufacturer in the box.  You'll probably need 4-6 DVD's to complete the process.

Get those made and then proceed to creating 1 single partition for Windows as mentioned above the 4 partitions can make it a bit tricky.  Run your install on Ubuntu and build the partition size you want for Linux.  

If you run into an issue you will be able to start all over again (remember those restore disc's) but I would recommend installing Windows first, then Ubuntu.  Or you could be like many others who solely dive into the awesome world of just Linux!

As for the computer choices to install Ubuntu...I have installed on Toshiba, HP DV6, Dell desktops, HP mini's, Asus, etc. and I have not had any issues.  Just take your time, do not rush the process, and I think you'll be fine!

---

### Post by ubuntu27 on 2012-03-04
I have an HP Pavilion dv6000 laptop.

I had no trouble installing any distribution of Linux on it.

Henkdroid mentions that HP laptops comes with 4 partitions. I don't remember well, but I do recall having to delete some partitions to install Ubuntu.
That was back when I dualbooted. Now I only have Linux on my laptop (no more Windows!).


Oh. My laptop has a some heating issue. I've read on the Internet that HP laptops is known for having serious heating issues. So, you might want to stay away from HP laptop perhaps. (Unless they fixed it in their recent models)

---

### Post by mcduck on 2012-03-05
> **ubuntu27 said:**
> 
Oh. My laptop has a some heating issue. I've read on the Internet that HP laptops is known for having serious heating issues. So, you might want to stay away from HP laptop perhaps. (Unless they fixed it in their recent models)
I wouldn't make such general statements, and definitely based on information "read on the Internet".

Any laptop running a Sandy Bridge CPU, with integrated graphics card on the CPU, currently has some issues with not powerign off the GPU correctly. Regardles of the manufacturer. And that'a a problem that can be solved. And as most new laptops have nVidia Optimus or AMD Fusion, you'll have the same issue regardles of which manufacturer you choose. :D

Also keep in mind that high heat is not same as heating issue (which wold mean that the amount of heat would be too much for the system to handle, resulting in crashes or throttling the CPU/GPU speed to reduce heat). Any computer hardware is supposed to be able to handle full load and thus also any normal amount heat the hardware itself is capable of generating. Yes, it might get noisy and hot to touch, but that's still not same as overheating.

(I'm currently running a HP laptop, with a Sandy Bridge CPU, but on this model HP has on purpose disabled the use of the integrated GPU completely as swithcing the GPU ion the fly causes troubles with workstation apps even on Windows, so I'm not having any problems with high load or fan noise/ high temperatures. You can of course do the same on any laptop, but it's a compromise when it comes to battery life)

---

