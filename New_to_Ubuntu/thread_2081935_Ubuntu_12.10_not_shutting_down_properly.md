---
title: "Ubuntu 12.10 not shutting down properly"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by blade4 on 2012-11-08
Hi all , I recently installed quantal ( amd x64 version ) using wubi on my MSI GT70 . Everything seemed ok except when I shut down my system , I noticed my external mouse was still lit up even though all lights on my laptop had gone out . Somehow , the laptop is still on . Any suggestions ?

---

### Post by alkh3myst on 2012-11-08
'Lo Blade4! There are always problems with Wubi. I think Ubuntu should stop offering it. The Windows filesystem always tends to degrade a Wubi install, until it becomes so unstable it's worthless. If you're experimenting with Ubuntu, a much better option is to run it from a flash drive. This will let you examine Ubuntu from a stable source. I would simply uninstall Wubi, and either run Quantal from a flash drive, or if you're satisfied with Ubuntu as a long-term solution, install it dual-boot. Earlier problems with Windows bootloader fighting GRUB, the Ubuntu bootloader, seem to be over. Dual-booting is a happy experience again.

:popcorn:

---

### Post by Impavidus on 2012-11-08
I have also noticed the light of a mouse remaining on indefinitely after shutdown. Apparently the OS shuts down normally, but the USB ports remain powered (just as the network card, those control LEDs next to the network cable stay lit. I have heard this can be usefull to boot a computer remotely). The trick is to pull the plug from the wall outlet or use the switch in the power module at the back of your pc.

---

### Post by blade4 on 2012-11-08
>               **Re: Ubuntu 12.10 not shutting down properly**
         'Lo Blade4! There are always problems with Wubi. I think Ubuntu should  stop offering it. The Windows filesystem always tends to degrade a Wubi  install, until it becomes so unstable it's worthless. If you're  experimenting with Ubuntu, a much better option is to run it from a  flash drive. This will let you examine Ubuntu from a stable source. I  would simply uninstall Wubi, and either run Quantal from a flash drive,  or if you're satisfied with Ubuntu as a long-term solution, install it  dual-boot. Earlier problems with Windows bootloader fighting GRUB, the  Ubuntu bootloader, seem to be over. Dual-booting is a happy experience  again.Thanks for the advice alkh3myst[]("http://ubuntuforums.org/member.php?u=488715") . I tried using ubuntu from a flash disk but the problem still remains . 

> The trick is to pull the plug from the wall outlet or use the switch in the power module at the back of your pc.     Is that safe Impavidus ?

---

### Post by Impavidus on 2012-11-09
Not all computers seem to show the described behaviour, it's only my old one. It may be some hardware issue. It is probably even a feature.

Disconnecting from power mains is save **as long as you do it after shutdown is complete** (screen turns off, control LEDs turn off, usually an audible click). It should cause all remaining lights to go off after a few seconds. It's even saver in case of lightning strikes (which can no longer harm your computer) and it saves energy (power modules consume energy whenever they're connected to the wall outlet, even if they don't deliver any power to the computer). I always disconnect my computer after shutdown.

---

### Post by varunendra on 2012-11-09
> **blade4 said:**
> Is that safe Impavidus ?Safe, if the system has actually been shut down and halted. However, that may be a workaround for desktops, while yours is a laptop - meaning you have to pull out the battery also everytime. Not a good idea if you shutdown frequently (some of us, like me, shutdown or restart only 2-4 times a month, some go even farther !).

Does it shutdown properly in windows? I'm asking because some modern laptops have this behaviour as a 'special feature' to allow charging handhelds even if the laptop is powered off.

If yours is not such a model, what if you manually try-
```
sudo shutdown -P now
```

PS:
12.10 is a fresh interim release, so bugs are to be expected. Given some time to mature, most of them should be automatically fixed with updates.

---

### Post by Impavidus on 2012-11-09
Actually it's my desktop that keeps UBS ports and network card powered after shutdown, wich can be solved by disconnecting power. My laptop does not keep the USB ports powered, but the control LEDs next to the network cable stay lit. They go out when I pull the plug from the wall outlet, even when a battery is present. When running on battery power all lights go off immediately at shutdown.

And yes, I'm sure it must be a feature to allow charging handheld devices from the USB port.

---

### Post by blade4 on 2012-11-09
Hey Varun , thanks for the advice . The lappy was indeed showing the same symptoms in Windows shut down too . I looked into my bios and found an entry named "icharger" was enabled . I've disabled it now and my mouse doesn't light up after shutdown anymore . :D 

Thanks again .

---

### Post by varunendra on 2012-11-09
> **blade4 said:**
> I looked into my bios and found an entry named "icharger" was enabled . I've disabled it now and my mouse doesn't light up after shutdown anymore ..
Great! So it was 'Charging' your mouse all the time!! :lolflag:

---

