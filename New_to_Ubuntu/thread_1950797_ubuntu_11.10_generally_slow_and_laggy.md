---
title: "ubuntu 11.10 generally slow and laggy"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by dkrises on 2012-04-01
Hi guys,

I have installed Ubuntu 11.10 alongside winxp recently. After overcoming wifi setup and internet problems, i am finding the system slow and laggy which freezes at times. I don't know whether it is my hardware which is -

AMD Athlon 64 3500
1GB RAM
ATI Radeon Xpress 200M

However, winxp is running fine with this hardware.

I have seen some videos of Ubuntu is action, and they seem to be  whizzing through apps. Whenever i try to load apps such as firefox, app centre, ubuntu one, thunderbird etc., it takes 30s to 1min to load. When i load several apps at once, it freezes at times.

I have checked system monitor with firefox running and it was at 50% of RAM and 40% of swap.

Could anyone help please in improving my speed and performance with Ubuntu? It would be much appreciated.

Thanks.

dk

---

### Post by 2F4U on 2012-04-01
I would say the problem is RAM, or lack of RAM. You have 1 GB but if I am not wrong your graphics card doesn't have it own RAM, so that goes off the 1 GB. The heavy swap usage is an indication of that. Since swap resides on the hard disk, it is by magnitudes slower than RAM and this is the reason why your system is slow.
My suggestion is that you either increase RAM or use something lighter than Ubuntu, for example Xubuntu or Lubuntu.

---

### Post by jerrrys on 2012-04-01
Have you tried gnome-classic (no effects)?

sudo apt-get install gnome-session-fallback

reboot and log into classic

---

### Post by wildmanne39 on 2012-04-01
Hi, for 11.10 you are light on memory and cpu power for a great experience in my opinion.

You can try this:
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

Classic with no effects as already suggested will work better for your system also you could change to a lighter distribution like lubuntu or xubuntu.
Thanks

---

### Post by dkrises on 2012-04-01
Thanks for the replies. Actually I have 1GB system RAM and the ATI Radeon Mobility Xpress 200M has 128MB of dedicated memory. In the system monitor it shows as 1GB system memory and 256MB swap memory. I may have quoted my swap memory usage higher than actual ... sorry. Will increasing my swap memory size improve my performance?

I thought my specs were enough   ... too bad. Anyway, I might try gnome classic. Will there be less features than the ubuntu unity interface? Would I be able to revert to the original version?

---

### Post by wildmanne39 on 2012-04-01
Hi, the difference is there is no 3d effects or desktop effects.

You can install it with this command:
```
sudo apt-get install gnome-session-fallback
```
Then just log out and into gnome fall back I believe that is what it is called in 11.10, using this method you can decide which desktop you want at the login screen.
Thanks

---

### Post by mal1958 on 2012-04-01
in addition to the gnome fallback, I would suggest that you check the drivers for your vid card.  Having the right drivers can make all the difference in the world at times.

EDIT:  I just had a thought here..  Please tell us that you are using Ubuntu in it's own separate partition, and not running it under windows or with Wubi.

---

### Post by dkrises on 2012-04-02
> **mal1958 said:**
> in addition to the gnome fallback, I would suggest that you check the drivers for your vid card.  Having the right drivers can make all the difference in the world at times.

EDIT:  I just had a thought here..  Please tell us that you are using Ubuntu in it's own separate partition, and not running it under windows or with Wubi.
I am running ubuntu with Wubi as i wanted to use it alongside Windows XP. Is that having an impact on performance? 
 
I was also wondering whether it was a graphics card driver issue. I think I installed the jockey drivers ... are there any better drivers for my graphics card?

---

### Post by techvish81 on 2012-04-02
wubi install will never tell what ubuntu can offer,  either dualboot with xp or a full harddisk install is needed to get real experience of ubuntu,   i bet it would be way better than as a wubi install.

---

### Post by wildmanne39 on 2012-04-02
Hi, did you try what is in post 4 in the link I gave you?

Also you can adjust your swap, if it is only using 50 percent ram and you are using 40 percent swap I think it should be adjusted so it will use more ram and less swap that will make it quicker.
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it)
Thanks

---

### Post by dkrises on 2012-04-03
Hi,
 
I have tried Complz Config to change settings as suggested . There was a noticeable difference and things loaded up faster. In addition, I loaded the Ubuntu 2D interface which also helped. There is still some lag when loading up apps from the launcher. Firefox takes up to 10s to load which is still slower than in WinXP. 
 
I could try the swap memory adjustment. I am starting to think whether I am actually limited by my hardware as you guys mentioned. I am also thinking that rather than do all these tweaks and changes, whether it would have been worth installing it on a separate partition (which seems a bit of hassle for me).
 
Thanks for all your suggestions so far.

---

### Post by wildmanne39 on 2012-04-03
Hi, all suggestions made so far makes it faster but yes you are still limited by your hardware, your system would be much quicker with lubuntu.

Decreasing your swapiness should make it even quicker and might be acceptable to you .
Thanks

---

### Post by dkrises on 2012-04-10
Hi guys,
 
I think I may have found the reason for the slow and laggy performance of ubuntu on my system. When I first installed ubuntu through Wubi, I downloaded the executable and run it. It detected that my machine was a 64 bit machine and so automatically downloaded and installed the 64 bit version of ubuntu. I read in a post somewhere that the 64 bit version requires higher RAM, preferably 3-4GB RAM whereas I had just 1GB. I then downloaded the 32 bit LiveCD iso file and installed it from there and there was marked improvement in performance. The full ubuntu unity interface  worked faster and smoother and was more stable than before. 
 
I am aware that the performance may drop slightly under Wubi in comparison to installing it in a separate partition. But as I am using it for testing purposes at the moment without affecting my Windows install, I can live with this performance. 
 
I have just one last question though. Will the Wubi installation affect the fragmentation of my HDD in the long run? Is this a major issue? I guess this would be a separate question in a different thread.
 
Anyway, I'll see how I get along with ubuntu and whether i can get my misus to use it as well ! :-)
 
dk

---

### Post by I2k4 on 2012-04-10
Agree with others that if you're running on top of Windows via WUBI you're overtaxing your hardware.  I suggest testing 11.10 and possibly 10.10 via Live USB (Ubuntu 11.10 and related versions raised the ante on hardware / resource requirements, much as Windows Vista raised them above XP.) If something runs well on the thumb drive it will run even better on a dual installation, but running Linux on top of Windows is a recipe for molasses on a weak machine. 

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Following the above foolproof directions for Live USB, you should add Persistence at Step 2 - use all the thumb drive space above 1.5GB for that.  It's only a tester on an inferior drive, but even so the test install should run as well or better than XP.  Eventually these Live USBs go wonky, in my experience, but they last long enough to get a good feel for the system you are learning about.

---

