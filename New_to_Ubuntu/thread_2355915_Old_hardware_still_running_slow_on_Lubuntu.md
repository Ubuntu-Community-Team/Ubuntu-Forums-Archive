---
title: "Old hardware still running slow on Lubuntu"
date: 2017-03-18
forum: New to Ubuntu
---

### Post by kiicki on 2017-03-18
I decided to use an old computer as my media server and for Kodi instead of getting something like a Raspberry Pi 3 as I thought this would still be better in terms of specs and I already had the computer so it would also be cheaper. It runs Windows 10 just fine and after fiddling with Ubuntu, Lubuntu and Mix in various version from 14.04 - 16.04 at least for Ubuntu/Lubuntu. Nothing has quite worked out and even if "sudo apt update && sudo apt upgrade" has helped with the screen tearing on this old computer, it runs a bit laggy and it stutters. I can feel it on the mouse movement, moving folders around and simply watching movies aren't that great either.

I thought Lubuntu would at least be way less resource demanding than Windows 10 and Windows 10 worked out fine. I suspect drivers issue even though I have been told that the Open source driver should be running good and that I should not have any problems. My understand is that "fglrx-updates" aka "AMD Catalyst" was last supported in 14.05, and even though I can see it showing up in "additional drivers" I get error issues after selecting it. I got some help from some people where I had to type in some command so they could see what I was running and they sad that I was still using the open source one even though I selected and rebooted using "fglrx-updates"

We even tried to downgrade kernel to a working one (If that was even what we were trying to do) and nothing was working. I do understand the bad specs I have, what I don't understand is why something like Windows 10 works so much better than Lubuntu. It should at least perform better than a Raspberry Pi as many people prefer that for an easy Kodi setup where my PC kinda stutters watching movies. Not usable IMO.

Specs:

- Custom PC

- CPU AMD Athlon II X2 B24

- GPU AMD Radeon HD 5450

- RAM 16GB

I guess what I'm getting is: lag, stuttering, some minor screen tear, folders kinda lags behind when moving folder around, scrolling through Chrome and Firefox, Youtube sometimes hangs up. Another word I could use is that it's not as snappy

---

### Post by mikewhatever on 2017-03-18
It is quite well known that most consumer grade hardware is made for and tested on Windows, while Linux distros are rarely in the picture. Because of this, hardware support is often better in Windows, with graphics drivers being a particularly sore point. Given the above, I don't think it's hard to understand why Windows may work better. (...and yes, software runs on hardware :~))
RP3 is a much newer device with a very different architecture. Comparing it to a decade old PC is hardly practical, and, needless to say, there are many thing that old PC can do, and RP3 can't.
The term "resource demanding" is often misunderstood. Lubuntu uses less RAM, but it doesn't add better graphics drivers or support for modern codecs or hardware acceleration. In other words, it can't make an old PC new. With 16 GB of RAM available, I doubt there is any advantage in Lubuntu selection.
In fact, I'd recommend an Android 6 box with 2GB of RAM, 16GB storage for youtube and Kodi. It will play them all with zero noise, and consume about ten times less power.

---

### Post by poorguy on 2017-03-18
Hey kiicki,

With those specs Lubuntu should fly.

I'm running LM 18 Xfce on an HP Desktop with the same Processor and Graphics Card and only 4.0 GB DDR2 Memory using the open-source graphic driver and have no problems at all with video streaming / lag / stuttering etc.

Don't really know what would cause video streaming problems you have unless your internet speed isn't very good. Are you wireless or hard wire as a hard wire connection will be superior to a wireless connection.

---

### Post by kiicki on 2017-03-18
I guess there's no reason for me to force Linux into this old machine. Windows runs way better but I kinda wanted to try Linux and Kodi has some graphics issues with some cards on the Windows version, where 9/10 times Kodi will crash when it starts up with the PC and sometimes during using Kodi. I have another system that has a GTX 560M where Kodi will crash no matter what when I try to open it in windows version where I have integrated graphics also in one of the systems (intel HD 3000) that actually works flawlessly. Problem is that the 1st system which is in the post only has the GPU that has issues on the Windows version but works great on Linux for Kodi, but again the whole OS seems laggy using Linux with it.

---

### Post by HermanAB on 2017-03-18
Try a faster browser, eg 'surf' or 'luakit'.

However, the trouble is likely due to a bad video driver, more than anything else.

---

### Post by kiicki on 2017-03-18
Yeah because the issue is not just the web browser. It was just an example. it's also slow straight from the desktop using VLC to watching movies, drag around folders etc.
It's really not usable but on Windows, Kodi likes to crash with this GPU. Which kinda leaves me with Ubuntu on Windows as I have heard that is a thing now. Not sure if it would work but could I run Kodi from that? On Windows with the Ubuntu on Windows?

---

### Post by mörgæs on 2017-03-19
AMD is putting great effort into improving their open source drivers. I suggest that you try to see how far they have come by testing 17.04 (beta).

---

### Post by mikewhatever on 2017-03-19
> **mörgæs said:**
> AMD is putting great effort into improving their open source drivers. I suggest that you try to see how far they have come by testing 17.04 (beta).

Agreed, though that effort is rather moderate (not too great), and might take some years to bear fruits. Also, their attention is focused primarily on new hardware. Chances are slim that cards from 2010, such as HD5450, will see any benefit.

---

### Post by sp40140 on 2017-03-19
Points made above about the drivers are valid.
I would like to add one more thing. The software you use to play videos. from my experience, VLC is no good on old systems for some reason. (others have mentioned the way cache is managed now). Regardless, all of my computers are at least 9 years old. And I use SMPlayer which gives me visibly huge performance boost from vlc.
Cheers,

---

### Post by mastablasta on 2017-03-20
> **mörgæs said:**
> AMD is putting great effort into improving their open source drivers. I suggest that you try to see how far they have come by testing 17.04 (beta).

So this is option one - 17.04 (beta). 17.04 will be released end of April. it will have latest kernel which means latest drivers. 

option 2 - 14.04 - but you need to install the 14.04.0 or 14.04.1 version. 14.04.2 up to 14.04.5 have kernel and xserver that won't allow you to install the AMD close soruce drivers. 14.04 is supported until 2019 and the AMD drivers should work just fine on it. downgrading just the kernel won't do it. i have a HD 6xxx series chip with similar issue, though it works fine on 14.04 with AMD drivers. these first 14.04 version will also keep kernel on same version addign security patches only.
you will find older versions here: [http://old-releases.ubuntu.com/releases/14.04.0/](http://old-releases.ubuntu.com/releases/14.04.0/)

option 3 - 16.04 - then use a PPA to upgrade the drivers to latest version. i believe oibaf's PPA is the popular one: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)


option 4 - stay on windows 10 and optimize it.

> **mikewhatever said:**
> Agreed, though that effort is rather moderate (not too great), and might take some years to bear fruits. Also, their attention is focused primarily on new hardware. Chances are slim that cards from 2010, such as HD5450, will see any benefit.

my HD 3650 worked just fine on Linux. it died though...

---

### Post by gordintoronto on 2017-03-20
I have a Phenom II X2 550, which is about 10% faster than your CPU. My GPU is an Nvidia Geforce 9400 GT, which was rebadged as the 210. I have the suggested Nvidia driver installed. I run Mint Cinnamon 18 (which is a heavy DE), and have zero complaints about performance. I use VLC to play videos. My video benchmark is a video called Mobius on Vimeo. (I downloaded the 1080P version) It plays perfectly in VLC.

In short, you might consider spending $20 on eBay buying a video card similar to mine.

But first, give Xubuntu 17.04 a shot.

I know, it seems silly to spend money on an old computer. Last year, I installed a Samsung 750 EVO SSD on my system, and it flies! I expect to be able to continue using this computer at least until Ubuntu 16.04 and derivatives reach end of life.

---

