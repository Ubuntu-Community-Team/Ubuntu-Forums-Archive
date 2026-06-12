---
title: "Ubuntu on Asus K53SD"
date: 2015-03-22
forum: New to Ubuntu
---

### Post by NaneK on 2015-03-22
Hi all,

This is my first post on this forum so I hope I do not break some rules :)

I have a question, that bothers me. A few days ago I got a new laptop for a present. It's [Asus K53SD]("http://www.asus.com/Notebooks_Ultrabooks/K53SD/") 15 inch laptop.
Specs are:
- Intel®  Pentium® Dual-Core  B960  Processor
- Windows 7 Proffessional SP1
- DDR3 4GB RAM
- Optimus graphics (GeForce® 610M 2GB and Intel HD *Graphics* 3000) 
- 2.5" SATA 500GB HDD
- Battery 6Cells 5200 mAh 56 Whrs
- wifi + bluetooth

Now I know that optimus is a pain in the eye, but it wasn't my choice, so....
I was wondering if it could run Ubuntu perfect, with no overheating and short battery life.

Now on Windows 7 I get about 4 hours on battery. I need to get also 4 hours on Ubuntu (on live USB it shows max 2 hours).
Since I know that optimus will be a problem for the battery life I went to see is it possible to turn off GeForce in BIOS, but it seems it's not possible - no switch. But even if it is possible I do not is it a smart thing to do, how much the Intel HD is capable?

I do not do gaming on laptop, but I do use a lot of programs like GIMP, for image manipulation. Also I often connect laptop to the TV via HDMI to play 1080p videos, so I need system to be capable to play full HD videos with no problems. I read something about bumblebee (or something like that), is it safe, can it make my battery lasts longer and also work as good as on Windows?

I have some experience with Linux in general, and I would like to use Ubuntu insted of Windows 7, but I wont do it if I can't get the same battery life on Ubuntu as on Windows. So can you give me some advice please.

---

### Post by grahammechanical on 2015-03-22
A lot of these question can only be answered by those that have the same hardware. That makes you an experimenter. Which is why we often recommend dual booting and still keeping Windows.

For a long time Bumblebee (an open source video driver) was the only choice for any one wanting to use Linux with Nvidia Optimus technology. And that was because Nvidia failed to provide a Linux driver. Things are a little better now but not as good as under Windows. I do not speak from personal experience but from what I have read and heard. The proprietary video drivers that come with Ubuntu 14.04 and later do make use of Optimus technology but do not provide automatic switching between the Intel and Nvidia adapters. But we can manually make the switch through the Nvidia Xserver settings manager that is installed along with the video driver. We also have something called Prime Indicator that will put an indicator on the top panel which we can use to switch between adapters.

Battery life will be an issue because you want to use to applications (Gimp and video playback) that will make use of the Nvidia adapter and it is the Nvidia adapter that will use more power. I have an older Nvidia adpater and that has a method of changing the performance level according to the load being placed on the GPU. So, I imagine your newer Nvidia adapter will also have methods of changing power levels according to need to save battery power.

The developers of the proprietary video driver being employees of Nvidia have access to Nvidia's technical secrets and this is access that the developers of Bumblebee do not have. I would advise going with the proprietary video driver. 

Regards.

---

### Post by NaneK on 2015-03-22
Thank you very much for your kind response.
If I got it right, if I install proprietary driver I could use optimus but I just need the switcher like Prime Indicator? If yes, that is OK for me.

As for battery, well most of time when I am on battery I tend not to use power hungry apps. Mostly I just surf the web and write HTML/CSS codes in GEdit. Very rearly I use GIMP or Photoshop on battery, I use them when on cable.
But I do watch videoplayback often. On battery I watch 720p videos max (beacuse internet connection isn't very fast). But when I am home, I sometimes watch Full HD videos - movies that I have on DVD or from the web. I watch that by connecting my laptop via HDMI to the my TV.

---

### Post by Vladlenin5000 on 2015-03-23
For all the usage scenarios you mentioned the Intel graphics is more than enough, actually waaaaay mooooooore than enough...

---

### Post by NaneK on 2015-03-24
> **Vladlenin5000 said:**
> For all the usage scenarios you mentioned the Intel graphics is more than enough, actually waaaaay mooooooore than enough...

Great, thank you very much for your reply :D
Yesterday I installed Ubuntu and bumblebee, and everything works great, and it appears that battery even can take it longer than on Windows. Brightness, wifi, bluetooth, fn hotkeys, everything works.

Once again thank you all, regards.
Solved

---

