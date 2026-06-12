---
title: "Arch user moving to Ubuntu,things are different and need a little help."
date: 2019-10-21
forum: New to Ubuntu
---

### Post by freefreeno on 2019-10-21
I need advice or help on two things that I always do that are different in Ubuntu than they were in Arch. I always enable "early kms" (early kernel mode setting) in Arch simply by putting the i915 in the /etc/mkinitcpio.conf MODULES=(i915) and regenerate initramfs. In Ubuntu this does not exist but I still would like to enable it early because I know it can be done UNLESS there is reasons why not to. I have been doing this for a couple years and it worked great. Here in Ubuntu the only thing I can find or read about is the initramfs-tools but I am still unsure. The second and really more important thing is I have been using systemd boot for a couple years also and I always use initrd to load the intel-ucode before the initial ramdisk. I just add one line to the boot config file and done. Early loading of the microcode is recommended even by Ubuntu but in a stock Ubuntu build it is not being loaded early so I would like to also know how to do that to. And my last question is I see that modesetting driver is default and that is good but how or why is the system still using the modesetting driver if the xserver-xorg-video-intel is installed and if we want to continue to use the modesetting driver is it ok to remove the intel driver. One more thing is that I have dual graphics with the Radeon PRO WX3200 and it is recommended to use the pro driver but that is impossible for me because the Pro driver is for LTS and the LTS will not install unless I use the OEM Dell build becuase I have the new wifi6. So I am stuck not being able to use the PRo driver. Is there any news or PPA's on AMD maybe making those drivers available to non LTS builds??? Really these things are the only things holding me up so if anyone can help me with the early kms and the loading the loading of the intel-ucode at boot I am all ears. Also if there is reasons thet this should not be done also let me know. I like to feel comfortable in my OS and know thet I can do my own thing ya know so here I am. I also for some very odd reason have this in my fstab and it was this way twice because I thought I must have done something wrong and reinstalled.
/ was on /dev/nvme0n1p3 during installation
/ is still on /dev/nvme0n1p3 so I have no idea why this says this. I do not have any other OS installed.

---

### Post by oldrocker99 on 2019-10-21
I do have a question. Why, considering your obvious great knowledge of Arch, have you moved to Ubuntu?

After 11 years, I got fed up with packages on which I had depended being removed with no announcement:mad:, and moved to Manjaro (I don't use Arch, btw :P), where all those apps are still available, in the repositories, and in the AUR. No problems have I found in the last 6 months, with a single installation, and I'm even using the Manjaro testing repositories, which Arch, mostly properly, calls stable packages.

So why go Ubuntu?

---

### Post by #&amp;thj^% on 2019-10-21
> =oldrocker99;13899407

So why go Ubuntu?

+1 That is a very sensible and reasonable question, now my curiosity is peaked here.

---

### Post by freefreeno on 2019-10-21
(Reason 1.) I got a new PC and now for the first time have switchable graphics but it is an AMD PRO card and neither Arch or Manjaro has my driver in the aur.
(Reason 2.) I could not get Arch to boot after I install the plasma desktop. I have been installing for years but with this set up I tried like 5 times.
( Reason 3. ) I tried Manjaro and since my pro driver was not there and the only thing I saw that I liked about manjaro was the look. Performance was very poor.
 So I tried Kubuntu and right from the start the performance was twice what I was getting in Manjaro. In Manjaro I had a lot of warnings and errors and so I went to the Manjaro forum to ask questions and was met either no reply or no reply that helped any what so ever. I know it hard to believe performance was that much different but it is. The main reason is AMD will never make driver for my card for Arch and I could not get it to install. I have a new Dell Precision 7540. Yes Arch is easier to use once it is installed but I do like Kubuntu but like my post says there is some things that I can not figure out.
My question.
Is Manjaro testing really like Arch stable ????
If so where are the testing iso. I seen unstable I think but testing.

---

### Post by oldrocker99 on 2019-10-21
AMD/ATI cards, as well as Intel, have FOSS drivers only. There are parts built-in to the kernel, as well as frequent updates of the driver files.

And, my nVidia card had its proprietary drivers installed during installation; you just select "non-free" at the installation splash.

The reason I left Canonical, and unfortunately Ubuntu, which I still love, for Manjaro has the packages on which I had depended, which had disappeared from the Ubuntu repos, including pypar2, ExFalso, avidemux, and Aqualung, the most important of the four for me. I now have all of those. I do run Manjaro MATE, which is pretty lightweight, and, from my experience, Manjaro is just faster, with fewer daemons running at boot. Game performance appears faster to me, although I'm not a framerate chaser.

Arch stable **is** Manjaro testing, and I'm brave, I guess. There has been no breakage of the system. The whole deal about Manjaro is that as Arch stable programs come out, they are tested for a week or 10 days, checking stability, bugs, etc. This makes Manjaro, which is just as user-friendly as Ubuntu, and just as suitable for old hands as it is for complete n00bz, and is more likely to be stable.

It comes with most desktops. A lot of people miss Antergos, which gave the user a choice of several desktops during installation, so they only had to put out one installation disk. However, it was purely a labor of love, since they had lives which had become preventative to keep the distro alive.

Again, your reasons for leaving Arch still puzzle me somewhat.

---

### Post by uRock on 2019-10-21
@oldrocker99, you make me want to give manjaro a try. I had also never heard of Aqualung, but now I want to hear it in action.

---

### Post by oldrocker99 on 2019-10-22
Aqualung is a lightweight, GAPLESS music player, meaning you can play an live album, or one whose cuts run together, and the playback is smooth.

It was in the Ubuntu repos until 14.04, and I had to compile it (I use 4 instances to do a radio show) over and over. Even when I was used to compilation, it still took ~30 minutes. The last time, GTK2, a necessary dependency, wouldn't even compile. Also, point releases do require reinstallation, and so far, the rolling nature of Arch-based distros means that it only needs to be installed once. (I have :mad: hosed the system **myself** ](*,)](*,)](*,), so I did have to reinstall :oops:.

I knew it was in the AUR, so I installed Manjaro, enabled the AUR, selected build the program, entered my password, hit Apply, and watched as every dependency was downloaded, the source code cloned, and compilation was over in 5 minutes.

I still love Ubuntu, which introduced me to the **BEST** OS, as well as the super and I, except for dual-booting Win7 strictly for Steam games for under 2 years. In 2013, with Steam for Linux releasing Linux gaming, I deep-sixed that malware magnet, although it had the last good DE that Micro$oft released, and their attitude of fixing what wasn't broken (just like the GNOME 3 devs) resulted in 2 horrible DEs, and Win10 is so terrible that it baffles me that people are able to use it. Also, users are stuck with their "improved" DE.

Linux, as we all know, has a raft of DEs. 

I still, and will always love Ubuntu (not so much Canonical). It's been a grand ride, and I couldn't be happier with this wonderful OS. It's been like discovering Linux for the first time. I installed it on a buddy's infected laptop. He is completely ignorant of computers. He loves Manjaro MATE, and will (a) never get a virus, and (b) never have to reinstall it. And Manjaro, very unlike Arch, is as user-friendly as Ubuntu for installation and usage, and as suitable for my buddy as for old hands like me.

---

### Post by freefreeno on 2019-10-23
Simple things are making me find my way back to Arch. For instance I use hardware acceleration in the chromium browser and yes Ubuntu has one ppa to do just that but it is in my opinion and incomplete ppa. You have to have your api keys and there is not one ppa that has the widevine.so package so I can not use my hardware acceleration. This is important to me. I need a patched chromium browser and a patched chrome widevine package. In Arch I could have those two things installed and be watching videos with either my AMD or my intel card with whatever acceleration method it was using at the time. Also loading huc and guc gives benefits in this regard too. By the way I see Ubuntu installs the old libva-intel driver that is really not recommended for newer intel graphics. If you have a newer intel HD then I would advise to install the intel-media-driver non-free edition and set this variable in /etc/environment.
[COLOR=#000000][FONT=monospace]LIBVA_DRIVER_NAME=iHD
[/FONT][/COLOR][FONT=monospace]You can keep the old libva driver until you see you like the new one better but it will not be used with that variable set. Load guc and huc will load automatically and then you will have as far as I am concerned the best hardware acceleration that intel can offer at this point. I do not use the xserver-xorg-video-intel package. I use the modesetting driver and then the intel media driver catches the hardware acceleration for me. I installed the patched chromium in Kubuntu but now you can not just copy widevine over to the chromium directory and it work so I did all that for nothing. This little thing right here makes your browser use half as much cpu while streaming 4 k videos. These are types of things that make it or break for me and an OS. Most people just think you have to use your browser without hardware acceleration or they don't even miss it but I like to configure my machine one time and be done. I can not do that with Kubuntu. There is however the need for my AMD GPU Pro driver but that is a mess also. You can only install those in lts builds. My wifi6 is too new for that kernel so here I am.[/FONT]

---

### Post by #&amp;thj^% on 2019-10-23
> **freefreeno said:**
> There is however the need for my AMD GPU Pro driver but that is a mess also. You can only install those in lts builds. My wifi6 is too new for that kernel so here I am.[/FONT]
That's valid, I try to stay with new-ish hardware (Well supported) but Welcome back to Arch! ;)
Like oldrocker99, but I'm a purist Arch user>>> I like my work flow UN-interuupted, which is what I get now.  :D

---

