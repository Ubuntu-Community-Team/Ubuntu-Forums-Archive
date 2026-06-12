---
title: "Surface Pro 1 freezes when wifi is used"
date: 2015-08-19
forum: New to Ubuntu
---

### Post by rasmus9 on 2015-08-19
Hi there!

I really got sick and tired of Windos 8.1 & 10 and decided to try out Ubuntu, i've always had a quite good feeling about this OS.

But every time i use the wifi (searching for updates, trying to use the internet browser etc.) the tablet completely freezes, and have to be manually restarted - this was the same issue under the installation of the OS (Ubuntu 14.04) if i connected it to wifi. It works fine when i disable wifi and hook it up through my phone via USB. I've tried updating the driver for the wifi chip (Marvell 88W8797 as far as i am informed) through the terminal (found a guide), which did not seem to work. I updated the kernel to 4.1.6-040106-generic, which didnt help either.
Ubuntu is new to me, so it is hard to figure out a solution to this problem, and most of the threads online is about unstable wifi, and they seem quite confusing to me at this stage.

Are anybody here able to help with this particular problem? 

Best regards
Rasmus

---

### Post by oldrocker99 on 2015-08-19
There is a program called **ndiswrapper**, which will load a Windows wireless driver into the kernel. Here's what you need to know:[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

You obviously need to download the Marvell driver, then extract it and point ndiswrapper at the **.inf** file. Reboot and you should be up and running.

Good luck! And welcome to the Linux community! You'll be very glad you started using the very best OS there is.

---

### Post by rasmus9 on 2015-09-02
Thanks for the support, but i could not make it work, and i have to give up. I cant handle dealing with alle these small issues all the time, when i have to use the tablet for my studies, it is too much trouble and setback all the time. There is no doubt that linux is a way better OS than Windows, and i really liked using it. But it is just not meant for touchscreens, whereas windows is optimized for this particular tablet.

I will try it out with dualboot on my laptop, the next time i format it, and try to get more familiar with it. 
Thanks for now!

\\Rasmus

---

### Post by Geoffrey_Arndt on 2015-09-02
A surface pro . . . . pretty much designed for windows only (why not?)

A simple usb wireless adapter that is 100% compatible with Ubuntu would be a fast solution.    

For about 10 usd . . . ($10) via Amazon, you can get a "Panda Ultra Wifi b/g/n 150" - do a search on that . . . these are "plug and play" in Ubuntu for all current versions above 11.10.

................................................

If needing full touch screen capability . . . perhaps a pre-configured PC from System76 or a similar vendor would be a longer term solution.

---

### Post by ashraf4 on 2015-12-05
I know I am 4 months late but I just found a solution that worked for me which I think might work for you too. Since your kernel version is 4.1.6, I'm pretty sure that is your problem. Try downgrading to 3.16.0. That's what I did and that fixed my problem. I am currently running Ubuntu 15.10 on my Surface Pro 1 and I still haven't run into any problems.

---

