---
title: "Lubuntu booting vevry second time only"
date: 2021-02-02
forum: New to Ubuntu
---

### Post by nadgob73 on 2021-02-02
Hi, yesterday I have installed Lubuntu (latest LTS version) on Toshiba Satellite C660-11G (Intel pentium T4500, 2GB RAM). After I shut if off, I went to power it on again but only the fan started to spin, the screen was blank, as if I would start the system without the RAM. So after 30 seconds I shut down the system by holding the power button. And when I pressed that button again, It booted up normaly. So I tried to shut it off and on for a few more times and got the same result. I also noticed that when I restart a system instead of manualy powering it on, it would boot just fine every time.

Please ask me for additional information and mind that I am a Windows user.

---

### Post by CelticWarrior on 2021-02-02
Welcome.

By the "latest LTS" you mean 20.04, right? Because if you actually installed the previous 18.04 then my next question is 32-bit or 64-bit...

---

### Post by guiverc on 2021-02-02
I agree with @CelticWarrior, please be specific with details, as people can interpret *latest* and *LTS* differently. 

Further,  *latest* if you go to a non-Ubuntu, non-Lubuntu site because you asked google where to download Lubuntu, you can download a prior release or potentially something-else entirely).  Sticking to legitimate sites is key, but a quick scan in *firefox private* mode searching for "download latest lubuntu lts" gives 3 *unrelated* sites before giving a legitimate url.  Me, I know to go to [ubuntu.com]("https://ubuntu.com/download/flavours") for official sites, and not to ask google.

To me your issue sounds more hardware related.   I'd forget what you have installed, and assuming it's your only installed system, test using *live* media, or boot and go into the boxes uEFI/BIOS setup only; as if you can't enter that each time, you have hardware/firmware issues that are unrelated to the OS (ie. the issue is before the OS has even started loading).

---

### Post by nadgob73 on 2021-02-03
Yes, it is 20.04 form [https://lubuntu.me/](https://lubuntu.me/)

---

### Post by chrischang2021 on 2021-02-03
[COLOR=#000000]Intel pentium T4500, 2GB RAM --- it sound that the very old laptop , I have installed old version to run Ubuntu (the type of CPU - I forget , RAM 2G ,Ubuntu 14X.XXX)
---I suggest you to re-install version of older and try it again. [/COLOR][COLOR=#000000]If you can run normal hardware should be ok.

[/COLOR][COLOR=#000000]for My experience remove RAM and clean gold pin then reinstall it.[/COLOR]:p[COLOR=#000000]

[/COLOR]

---

### Post by Impavidus on 2021-02-03
> **chrischang2021 said:**
> [COLOR=#000000]... installed old version ...[/COLOR][COLOR=#000000]
[/COLOR]

Don't install unsupported versions. If the computer cannot run a supported version of even the lightest Linux distro, hand it in for recycling. Even if it can run an outdated operating system, it won't be able to run modern applications, so it will be useless anyway. Or, for very light applications, a Raspberry Pi could do it for a tiny fraction of the power consumption.

---

### Post by nadgob73 on 2021-02-03
yes, I can enter boot maneger or BIOS every second time only.

---

### Post by nadgob73 on 2021-02-03
I realised That I made a grammar mistake in the title

---

### Post by guiverc on 2021-02-03
One of boxes I use in testing is 

- lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)

and that runs anything up to the current *hirsute* daily (ie. what will become 21.04)

and I used boxes as old as from 2003 (x86 or i386), in testing Lubuntu & Xubuntu 18.10, 19.04 *alpha* with 1GB RAM until the i386 ISOs stopped being produced. The last i386/x86 image though will likely be 18.04.5 which was released August-2020 (where I tested other *flavors* too).

Your box will run the software I'm pretty sure, but as I mentioned before, it reads like hardware issues to me, and not software.

---

### Post by chrischang2021 on 2021-02-03
So the problem still there. Right ?

---

### Post by nadgob73 on 2021-02-03
Yes. It only boots every second time, but I guess I can live with that since it's not my primary computer or laptop.

---

### Post by nadgob73 on 2021-02-03
I've cleaned the RAM stick and put it into different slot. That did not make any difference.

---

### Post by guiverc on 2021-02-03
The *live* I mentioned was for testing purposes.

If it's a *config* issue with your install, you won't have the issue at all when using the *live* media, however if it's hardware related, the issue will occur regardless of what *live* media is used.

Using *live* media also lets you try different kernels, eg. Lubuntu 20.04 LTS & 20.04.1 LTS media used the 5.4 GA kernel, where as Lubuntu 20.04.2 LTS media uses a later 5.8 kernel (or 20.10 kernel). If you expand to also testing different OSes or releases, you can try different kernels & thus gain more detail as to is it related to a specific kernel (ie. driver issue as drivers are kernel modules).

Lubuntu 18.04 LTS & 18.04.1 LTS media used the 4.15 kernel, 18.04.2 used 4.18 (or 18.10), 18.04.3 used the 5.0 or 19.04 kernel, 18.04.4 used the 5.3 or 19.10 kernel etc.. Because they have different kernels, they'll have different kernel modules allowing you to test different versions of drivers (some may be the same software, just re-compiled; but it's still clues).

This is what I like about *live* testing, it allows a great deal of detail to be gained, without installing anything on the actual box; just downloads of the ISO & writing to media for testing. As I do that often, it's fast & easy, though it may involve more work for someone unaccustomed to doing it.

---

### Post by nadgob73 on 2021-03-03
Some days ago I visited a family-friend which diagnosed the laptop and said it was a hardware issue and that I should just live with it.

---

