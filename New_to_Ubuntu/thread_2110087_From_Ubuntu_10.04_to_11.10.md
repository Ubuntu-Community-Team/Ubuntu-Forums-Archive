---
title: "From Ubuntu 10.04 to 11.10"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by daniell59 on 2013-01-29
I will soon be doing a clean install. I already burned my photos to DVDs. Anything that I need to know after the installation is complete? Also, I would like comments on how I plan to do it.
I have two hard drives. I will disconnect the one that has windows installed on it. When I want to change operating systems, I will go into the BIOS.

---

### Post by sudodus on 2013-01-29
There is something you need to know now at once!

The end of life is the same date for 11.10 as of 10.04 LTS (April 2013), so it is not a good candidate for upgrading. I recommend that you make a new install of or upgrade to 12.04 LTS. End of life of vanilla Ubuntu is April 2017, end of life of light-weight Xubuntu is April 2015.

---

### Post by kansasnoob on 2013-01-29
11.10 reaches EOL in just a couple of months ......... go for 12.04 which is supported until April 2017 :D

If the new Unity DE blows your mind you can even get close to classic via:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by kansasnoob on 2013-01-29
> **sudodus said:**
> There is something you need to know now at once!

The end of life is the same date for 11.10 as of 10.04 LTS (April 2013), so it is not a good candidate for upgrading. I recommend that you make a new install of or upgrade to 12.04 LTS. End of life of vanilla Ubuntu is April 2017, end of life of light-weight Xubuntu is April 2015.

Oopsie ....... we stepped on each other :lolflag:

---

### Post by furything on 2013-01-29
Agree with sudodus and kansasnoob

Why don't you just do dist upgrades right up to 12.04? Ensures correct drivers

Why stop at 11.10? What is your reason for this particular version?

I use both 12.10 and 12.04 on different pcs with multiple desktops (gnome, unity ,kde). Personally I prefer kde but know I am in the minority.

If a fresh install then always boot from live cd and play around. That you know if your hard ware is supported e.g. ethernet ports (wired/wireless) graphics and sound. Or if you are going to encounter and issues.

---

### Post by kansasnoob on 2013-01-29
> **furything said:**
> Agree with sudodus and kansasnoob

Why don't you just do dist upgrades right up to 12.04? Ensures correct drivers

Why stop at 11.10? What is your reason for this particular version?

I use both 12.10 and 12.04 on different pcs with multiple desktops (gnome, unity ,kde). Personally I prefer kde but know I am in the minority.

If a fresh install then always boot from live cd and play around. That you know if your hard ware is supported e.g. ethernet ports (wired/wireless) graphics and sound. Or if you are going to encounter and issues.

But, if you decide to do an upgrade via update-mangler wait a couple of weeks until the delayed 12.04.2 drops:

[http://www.phoronix.com/scan.php?page=news_item&px=MTI3MjY](http://www.phoronix.com/scan.php?page=news_item&px=MTI3MjY)

I've been doing SRU testing and IMHO it's worth the wait :D

---

### Post by daniell59 on 2013-01-29
Thanks guys. I have burned discs for both 12.04 and 12.10. I ran both on my computer, and they both work fine. I must say however that 10.04 is working perfectly. I always thought that a clean install is the best way to go.

---

### Post by sudodus on 2013-01-29
> **daniell59 said:**
> I will soon be doing a clean install. I already burned my photos to DVDs. Anything that I need to know after the installation is complete? Also, I would like comments on how I plan to do it.
I have two hard drives. I will disconnect the one that has windows installed on it. When I want to change operating systems, I will go into the BIOS.

It is a good idea to use two drives. I recommend that you download several iso files, version 12.04 (and 12.10 if you want to try it), flavours [vanilla or standard] Ubuntu, Lubuntu, Xubuntu, Kubuntu. Try them live before installation, and select what you prefer on that particular computer!

Then you can do as you write: Install without the Windows drive.

Check if Windows is booted via BIOS or UEFI. If BIOS, it will be straight-forward.

You need not go into the BIOS menus to change the boot order. Instead connect the Windows drive, keep the booting from the Ubuntu drive, and run this command
```
sudo update-grub
```After reboot, you should be able to boot Ubuntu as well as Windows, selecting at the first text menu, the grub menu.

If UEFI, it is more complicated. Search for new threads in the Ubuntu Forums about dual booting of Ubuntu and Windows (7 or 8) where these methods are explained, for example this thread

[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

### Post by sudodus on 2013-01-29
> **daniell59 said:**
> Thanks guys. I have burned discs for both 12.04 and 12.10. I ran both on my computer, and they both work fine. I must say however that 10.04 is working perfectly. I always thought that a clean install is the best way to go.
Maybe you need a lighter desktop environment than vanilla Ubuntu's Unity. You can try *kansasnoob*'s tweaks, or Xubuntu with XFCE or the ultra-light-weight Lubuntu with LXDE.

---

### Post by daniell59 on 2013-01-29
> **sudodus said:**
> It is a good idea to use two drives. I recommend that you download several iso files, version 12.04 (and 12.10 if you want to try it), flavours [vanilla or standard] Ubuntu, Lubuntu, Xubuntu, Kubuntu. Try them live before installation, and select what you prefer on that particular computer!

Then you can do as you write: Install without the Windows drive.

Check if Windows is booted via BIOS or UEFI. If BIOS, it will be straight-forward.

You need not go into the BIOS menus to change the boot order. Instead connect the Windows drive, keep the booting from the Ubuntu drive, and run this command
```
sudo update-grub
```After reboot, you should be able to boot Ubuntu as well as Windows, selecting at the first text menu, the grub menu.

If UEFI, it is more complicated. Search for new threads in the Ubuntu Forums about dual booting of Ubuntu and Windows (7 or 8) where these methods are explained, for example this thread

[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

This is a homebuilt computer. It is about four years old. It definitely has BIOS. As I previously stated, I ran both 11.04 and 11.10 from the CD and DVD. No problems.

---

### Post by furything on 2013-01-29
Agreed
> But, if you decide to do an upgrade via update-mangler wait a couple of weeks until the delayed 12.04.2 dropsWait for the rest of us to do updates break our systems and then post how we fixed it. (it happens thankfully not too often)

> Then you can do as you write: Install without the Windows drive.!I always do this so my windows mbr remains untouched and I can from BIOS select boot option and go straight to windows. Windows always wants to be sda if you want to use it's inbuilt backup so booting this way ensures it works when it runs.

Otherwise I let my linux disk boot up by default and can select linux or windows from there. I prefer linux but have to keep the household happy with windows :(

---

### Post by sudodus on 2013-01-29
> **daniell59 said:**
> This is a homebuilt computer. It is about four years old. It definitely has BIOS. As I previously stated, I ran both 11.04 and 11.10 from the CD and DVD. No problems.
I guess you mean 12.04 and 12.10? That's great!

Anyway, you can easily change the desktop environment, or add one for some special task if necessary (for example to play high definition video).

---

### Post by daniell59 on 2013-01-29
> **sudodus said:**
> I guess you mean 12.04 and 12.10? That's great!

Anyway, you can easily change the desktop environment, or add one for some special task if necessary (for example to play high definition video).

Thank you for the correction.

---

