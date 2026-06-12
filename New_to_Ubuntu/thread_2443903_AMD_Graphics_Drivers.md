---
title: "AMD Graphics Drivers"
date: 2020-05-21
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-05-21
Hi all, just looking to see if anyone can weigh in on a driver question.

My CPU is an AMD E2-1800 APU with Radeon HD graphics - 1.7GHz dual core

The video driver I have loaded is simply called 'radeon'

My question is basically, is this a generic driver that comes with ubuntu (18.04 LTS) or is it a proprietary AMD driver? I realize it says 'Radeon' in the cpu string, but see below... 

The reason I ask is that the laptop is from around 2012, and I believe AMD only support their hardware for 3 years (that could be wildly inaccurate / oversimplified) which would mean they stopped supporting my hardware long before my version of Ubuntu was released. I do have issues with some video stuff like playing mp4's and BBC Iplayer (a streaming service) and am wondering if maybe there is another video driver I could try? Like a generic driver that comes with Ubuntu perhaps?

Any info is well received!

---

### Post by kurt18947 on 2020-05-21
As far as I know, AMD has discontinued their proprietary Linux drivers. My understanding is that there are two AMD drivers, both available in the repositories. Older cards use the Radeon driver, newer cards use AMDGPU. I had an AMD Ryzen 3 2200G that used AMDGPU. It was a real problem with Ubuntu 18.04 and the 4.xx kernel. When 18.04.4 came out using the 5.3 series kernel it was somewhat better. 20.04 is better yet, it is pretty stable. I think there are updated graphics related  packages in 20.04 in addition to the newer kernel.

---

### Post by CatKiller on 2020-05-21
> **jcdenton1995 said:**
> The video driver I have loaded is simply called 'radeon'

My question is basically, is this a generic driver that comes with ubuntu (18.04 LTS) or is it a proprietary AMD driver?

It's an open-source driver contributed to by AMD, but also contributed to by everyone else. They *used to* have a proprietary driver, but it was pretty awful and they discontinued it and put all their resources into the open source driver.

Newer cards - with a newer architecture - have a newer driver called amdgpu, which is also open source. AMD have a version of that (amdgpu-pro) which is exactly the same open source amdgpu driver but with proprietary shaders from their Windows driver.

> I do have issues with some video stuff like playing mp4's and BBC Iplayer (a streaming service) and am wondering if maybe there is another video driver I could try?

Nothing to do with the graphics driver. What you're seeing is the lack of hardware-accelerated video decoding: your CPU really isn't strong enough to do it in software. For local playback, **mpv** is able to use hardware decoding for whichever encodings you have hardware support for. The web browsers disable hardware acceleration on Linux, but there's [a PPA for chromium](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html) that enables it.

---

### Post by jcdenton1995 on 2020-05-22
Thanks for the detailed reply

I'm still a little confused as GNOME settings shows that my 'graphics' is AMD PALM, and I couldn't work out weather this was another name for the driver, or a code name given to the integrated graphics hardware?

what further confused me was an article I found online about a company that produces smart phones - called Palm - [poaching AMD's top guy who was in charge of developing it's Linux drivers]("https://www.phoronix.com/scan.php?page=article&item=amd_matthew_tippett&num=1") which made me wonder what the significance of this was, is 'AMD PALM' a 3rd party graphics driver released by Palm for mobile CPU's or something? It doesn't show up under that name or anything similar if I run lsmod so unsure what it means...

---

### Post by jcdenton1995 on 2020-05-22
Thanks for the info, I don't think I'll be upgrading to 20.04 for a while as I'm still getting to grips with things, but when I do it will probably be on a machine with a proper graphics card, so I'll bear this in mind!

---

### Post by mastablasta on 2020-05-22
> **jcdenton1995 said:**
> Thanks for the detailed reply

I'm still a little confused as GNOME settings shows that my 'graphics' is AMD PALM, and I couldn't work out weather this was another name for the driver, or a code name given to the integrated graphics hardware?

what further confused me was an article I found online about a company that produces smart phones - called Palm - [poaching AMD's top guy who was in charge of developing it's Linux drivers]("https://www.phoronix.com/scan.php?page=article&item=amd_matthew_tippett&num=1") which made me wonder what the significance of this was, is 'AMD PALM' a 3rd party graphics driver released by Palm for mobile CPU's or something? It doesn't show up under that name or anything similar if I run lsmod so unsure what it means...

palm probably means something else.

various system info applications will dispaly thigns differently. for example you can also try inxi (in command line): [https://www.tecmint.com/inxi-command-to-find-linux-system-information/](https://www.tecmint.com/inxi-command-to-find-linux-system-information/)
or lspci 
or lshw

and similar. but the bottom line is that APU is really not that great to begin with. and no matter what drivers you have they can't perform miracles. you have the opensource radon drivers by the way. i have a similar chip and 5 years ago radeon was worse than proprietary one. but they (AMD) improved the opensource and i don't have much issues.

with APU - make sure you have enough RAM available. you need ram for the OS and then a large portion of same RAM will also be taken by the graphics chip. these low end notebooks usually don't have enough ram. i have 2 Gb, it is horrible on Win7 but tolerable on Linux. i think i might upgrade it to 8 GB or at least to 6 GB. 

on windows system takes over 1 GB ram and GPU takes 512MB ram. On linux system takes 400 MB and GPU also takes 512 MB, so that leaves 1GB for applications. 

when ram runs out hard disk is used, and they are a lot slower. even if you have a sata SSD drive in it.

---

### Post by CatKiller on 2020-05-22
> **jcdenton1995 said:**
> I'm still a little confused as GNOME settings shows that my 'graphics' is AMD PALM, and I couldn't work out weather this was another name for the driver, or a code name given to the integrated graphics hardware?

The products in the Ati Radeon HD 5000 series (codename **Evergreen**) were given codenames of types of tree: Cedar, Redwood, Juniper, Cypress, and Palm. Later products were codenamed various types of island.

---

### Post by jcdenton1995 on 2020-05-22
Ah I see, just a confusing coincidence then - Palm the code name and Palm the smartphone company.

Thanks!

---

### Post by jcdenton1995 on 2020-05-22
My laptop isn't too bad to be fair as it does have 8gb of RAM, I am looking to get something a little more modern though as I'd like to maybe run a couple of old games or something, which was *just *possible on windows 8, but with the compatibility layers needed for Linux I imagine that the performance margin is just too slim to run them. I haven't even so much as looked at WINE or Steam proton.

---

### Post by GhX6GZMB on 2020-05-22
Been there, had those problems and still partially have them.
But I've improved the situation considerably by including the oibaf PPA:

```
[FONT=Arial]sudo add-apt-repository ppa:oibaf/graphics-drivers[/FONT]
```

There are weekly updates coming from there, even for my old Radeon X1300 chip, and most problems have diminished with each update.
Update meaning:
```
sudo apt update
sudo apt upgrade
```

---

### Post by mörgæs on 2020-05-22
I don't think that your hardware is the problem. Ubuntu is, as it's one of the heaviest distros around. 

You could try a clean install of L/Xubuntu 20.04. I don't know the PPA mentioned above but if one of the light Buntus is not enough you could try that too.

---

### Post by CatKiller on 2020-05-22
> **jcdenton1995 said:**
> I'd like to maybe run a couple of old games or something, which was *just *possible on windows 8, but with the compatibility layers needed for Linux I imagine that the performance margin is just too slim to run them. I haven't even so much as looked at WINE or Steam proton.

There are modern games that aren't demanding. There are thousands of native games on Steam before you need to look at Proton.

I'd second the idea of considering a lighter desktop environment, but also the version of Gnome that comes with 20.04 has significant performance improvements over the version that came with 18.04. Either of those might make your experience more palatable.

---

### Post by GhX6GZMB on 2020-05-24
> **mörgæs said:**
> I don't know the PPA mentioned above but if one of the light Buntus is not enough you could try that too.

You should know it. Oibaf is the main repository for open graphic drivers, and resides under launchpad.net. Very active, too.

I bless the day I found it :)

---

