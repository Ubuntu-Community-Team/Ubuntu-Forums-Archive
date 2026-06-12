---
title: "nVidia TNT2 M64 graphics card, jerky video"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by David_Maxwell on 2014-05-09
Yikes!  Your concept of an "Absolute Beginner" is in a different league from me, and  I can't make head nor tail of the instructions posted to solve my  problems.  So perhaps you could direct me to some source where I can at  least learn your language. And, at its most basic, how do even get to a  command line prompt in Lubuntu 14.04?

I have an old HP Pavilion 7955 which had XP on it until I set about  replacing it with Lubuntu, (chosen because it purportedly runs well on  older machines.) According to the sticker on the front, it has a  Pentium-4 processor at 1.5 GHz, 256 Mb of SDRAM (but when I run the  memory test which was included in the installation download, it says  that the L1 cache is 8K, L2 cache 256K, and memory is 767M - does this  mean somebody added extra memory??) , 40GB Ultra DMA h/d, nVidia TNT2  M64 graphics card with 32 Mb SDRAM.  It was running extremely slowly,  with jerky video under XP.  In addition, the owner is inclined to surf  questionable sites.  I figured that putting Linux on might solve both  speed and safety issues.  It hasn't.  If anything the video is even more  jerky, (maybe one frame per second).  My question now is whether the  real problem is a hardware failure, or whether I need some additional  programs or drivers to make Lubuntu play nice with the video card. And  if the latter, I will need some guidance on exactly how one acquires and  installs such programs. (Just point me to sources of instruction). (I  grew up in the DOS era, and the prospect of command line interaction is  not overly daunting to me, but I need a little guidance as to the actual  commands and how things work in Linux.)

---

### Post by LastDino on 2014-05-09
If it is 256MB then that might be your actual problem. No matter how light the OS itself is, modern day programs need more than that. You could try to install non-free drivers, but I don't think that's the real issue. Just go to Nvidia site and search for your appropriate version which are made for Linux to download.

---

### Post by mörgæs on 2014-05-09
Sorry, but changing drivers won't make much difference. The graphics card is so weak (as is rest of the hardware) that one must expect a low performance.

---

### Post by sudodus on 2014-05-09
It seems there is 767M RAM available (which probably means 768 MB installed), and it is enough for Lubuntu.

Open a terminal window with the hotkey combination ***ctrl + alt + t*** or from the menu.

```
free -m
``` will show the memory. The following command will show the current version

```
lsb_release -a
```

I think the problem is the nvidia graphics card. You can try to install a proprietary driver, which might or might not solve the problem with jerky video.

But it might also be the problem that flashplugin (for web video) is not well supported for linux by the owner of flash. You may never be able to play video well.

Which version of Lubuntu are you running? There are two supported versions, 13.10 and 14.04 LTS.

With some old hardware, more suitable drivers come with Ubuntu 12.04 LTS. Lubuntu 12.04 has passed end of life, but there are several re-spins, that are worth trying, if you have no luck with the current Lubuntu versions:

- Bento, Bodhi and LXLE with support until April 2017.

See this link about what to expect from old hardware
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by newbie2244 on 2014-05-09
Important to read the original post. As I can't access your original posting I can pnly c;arify. 

 ```
 L1 cache is 8K, L2 cache 256K, and memory is 767M
``` means that you have level 1 and level2 ***cache memory*** of 8 kilobytes and 256 kilobytes, respectively.  You have available RAM of 767 megabytes. Probably your nominal RAM is 1 gigabyte, but what is actually available for use is 767 megabytes as posted by  ***sudodus***, above. 

About the video card, make sure you have the latest drivers. I can say that video cards cause problems frequently. Search for old posts  in this forum by "video card problems" or by the OEM name of your video card.  

BuT, if  XP ran reasonably well on this system, so should Lubuntu. 

Persevere and you'll get there. 

Regards,

---

