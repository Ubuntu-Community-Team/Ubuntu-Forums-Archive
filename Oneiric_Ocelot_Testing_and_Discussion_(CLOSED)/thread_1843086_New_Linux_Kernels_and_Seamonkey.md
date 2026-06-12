---
title: "New Linux Kernels and Seamonkey"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alexvy13 on 2011-09-12
Why do the new linux kernels 3.0.0-11 depend on seamonkey? i dont want seamonkey.

---

### Post by xebian on 2011-09-12
> **alexvy13 said:**
> Why do the new linux kernels 3.0.0-11 depend on seamonkey? i dont want seamonkey.

Never.  What are you smoking?

---

### Post by sammiev on 2011-09-12
Still FF here. So not sure what you are talking about. Please add a little info to your post. ):P

---

### Post by alexvy13 on 2011-09-12
I clicked update and it tried to install language packs for firefox (which i dont have installed) and seamonkey applications. It said i had to install seamonkey to install the kernels. I fixed it up in synaptic though. Weird.

---

### Post by pressureman on 2011-09-12
I noticed this too. It seems that xul-ext-calendar-timezones really really wants to install seamonkey :|

---

### Post by zenarcher on 2011-09-13
I noticed the same thing, as well.

zenarcher

---

### Post by pressureman on 2011-09-13
I don't know why apt-get seems to be interpreting "recommends seamonkey" as "depends on seamonkey", but I just downloaded the .deb of xul-ext-calendar-timezones manually, and then installed it with dpkg.

No seamonkey invasion :)

---

### Post by zenarcher on 2011-09-13
It did seem strange to me, but I allowed Seamonkey to be installed.

zenarcher

---

### Post by effenberg0x0 on 2011-09-14
Is it something only on Ubuntu Kernel? I compiled mine from kernel.org on monday and there's no mention to seamonkey anywhere during recent updates. It's not a recommended / dependency package anywhere during updates, including when apt installed the latest Ubuntu Kernel release.

Regards,
Effenberg

---

### Post by dino99 on 2011-09-14
seamonkey dependants: some xul-ext-*

so look at which xul-ext-* is installed on your system.

---

### Post by Seq on 2011-09-14
> **pressureman said:**
> I don't know why apt-get seems to be interpreting "recommends seamonkey" as "depends on seamonkey", but I just downloaded the .deb of xul-ext-calendar-timezones manually, and then installed it with dpkg.

No seamonkey invasion :)

That is what a recommend is. There are three types of dependancies:

[LIST]
[*]Depend: Required installed with
[*]Recommend: Optional, installed with
[*]Suggests: Optional, not installed with
[/LIST]

If you don't like this behavior, you can always set APT::Install-Recommends to "false". Be aware that this may cause problems (I'm not sure if auto-installed recommends will be suggested for removal or not).

---

### Post by pressureman on 2011-09-14
Yep, I'm aware of depends/recommends/suggests in apt-get. I think the real question is, if the default behaviour of apt-get is to install "recommends" packages, perhaps the package metadata is wrong, and seamonkey should be a "suggests" instead.

---

### Post by pressureman on 2011-09-14
> **effenberg0x0 said:**
> Is it something only on Ubuntu Kernel? I compiled mine from kernel.org on monday and there's no mention to seamonkey anywhere during recent updates. It's not a recommended / dependency package anywhere during updates, including when apt installed the latest Ubuntu Kernel release.

No, it's got nothing to do with kernels. I'd say it was just coincidental that the OP was new kernel packages available at the same time as the upgrades to Lightning.

---

### Post by Seq on 2011-09-14
> **pressureman said:**
> Yep, I'm aware of depends/recommends/suggests in apt-get. I think the real question is, if the default behaviour of apt-get is to install "recommends" packages, perhaps the package metadata is wrong, and seamonkey should be a "suggests" instead.

Well, I'd assume it actually does depend on thunderbird or seamonkey, otherwise being quite useless. If that is the case, it should probably be an actual depend on (thunderbird | seamonkey), causing it to need one, but it shouldn't care which.

---

### Post by pressureman on 2011-09-14
I *do* have Thunderbird installed.... so the "WTF" is that it wanted to install Seamonkey as well.

---

