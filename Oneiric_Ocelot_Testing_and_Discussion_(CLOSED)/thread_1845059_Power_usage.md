---
title: "Power usage"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bro on 2011-09-16
I read the most horrible stories about power usage in ubuntu 11.04 being even worse in 11.10. Does anyone know if there will be a fix for this 11.10? Since I work on a laptop I wonder if I should enter the 11.x arena at all. That is to say, I did, and I switched to Mint 11, but I'm considering an 'upgrade' to mint 10 (based on 10.10)

---

### Post by basilwatson on 2011-09-16
> **bro said:**
> I read the most horrible stories about power usage in ubuntu 11.04 being even worse in 11.10. Does anyone know if there will be a fix for this 11.10? Since I work on a laptop I wonder if I should enter the 11.x arena at all. That is to say, I did, and I switched to Mint 11, but I'm considering an 'upgrade' to mint 10 (based on 10.10)

my netbook isnt so bad , but my desktop cpus are running at 60 % after an upgrade tp 11.10 

see the zeitgeist thread 

its got lots of promise , but I cant when I cant open VLC player , because of the CPU ,,,its annoying 

others aren't having so much of a problem , but they, as far as I can tell experiencing a higher rate of power usage 

Personally I should of waited .....but I couldn't 

Stephen

---

### Post by dino99 on 2011-09-16
its not an Ubuntu or Mint question, its totally unrelated. Its a kernel config as pcie is activate by default

change the boot line parameter into /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"

then: sudo update-grub

[http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/](http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/)

[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption](http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption)

---

### Post by bro on 2011-09-16
Thanks, my system was already running in 'powersafe' mode. I doubt if this is the power usage that all the fuzz is about, though. I don't know what the problem is, but this is seems not so much as a 'problem' or a 'regression' this is just a system setting.

---

### Post by 3rdalbum on 2011-09-16
What you should understand is that the "power regression" thing has been blown out of context.

The context is that only certain computers are affected, and even if you have an affected computer you might not even notice a difference (depending on your use pattern).

I'm sure that power regressions have happened in the past for certain computers, but it's only recently that Phoronix Test Suite has had benchmarks for power use, and they're really beating the drum whenever they find a higher-than-normal power use.

Also, Intel recommends you keep your system in "OnDemand" mode rather than "Powersave", to help the CPU get to sleep quicker and save power. Powersave is actually a misnomer.

---

### Post by bro on 2011-09-16
Ah thanks. Though the drum beating says 'up to 50%', which would be shocking if was even half true. 

My laptop was in 'powersave' mode already, I didn't put it there with the above commands. Or must have done so in the bios. Thanks anyway and I'll see what happens with Oneiric.

---

