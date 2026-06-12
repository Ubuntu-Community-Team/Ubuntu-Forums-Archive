---
title: "How to make ubuntu boot by priority"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Lism on 2012-06-11
I've been wondering this for ages,

I have W7 and Ubuntu installed to dual boot and they work fine. However upon switching on the machine you have to wait for the boot manager then select Ubuntu before 10 seconds are up, so I was wondering if I can prioritize which OS to boot so I can switch on the machine and walk away and let it boot.

Thanks

---

### Post by drs305 on 2012-06-11
Absolutely. You can change the default OS, how long to wait before it automatically boots, etc.

I'd recommend you install a GUI Grub editor such as Boot Repair or Grub Customizer (links in my signature line). Boot Repair will help later if you have a problem.

You can read about how GRUB 2 works by visiting the GRUB2 community documentation link.

All are linked in my signature line.

---

### Post by Cavsfan on 2012-06-11
> **Lism said:**
> I've been wondering this for ages,

I have W7 and Ubuntu installed to dual boot and they work fine. However upon switching on the machine you have to wait for the boot manager then select Ubuntu before 10 seconds are up, so I was wondering if I can prioritize which OS to boot so I can switch on the machine and walk away and let it boot.

Thanks

There is a How to in my signature that is perfect for dual or tri-booting. And the beautiful thing is you never have to mess with it.
Even when a new kernel is installed.
I am currently tri-booting Lucid Lynx 10.04, Precise Pangolin 12.04 and Windows 7. If you look at the bottom of that first page you can see an example of my screen.

---

### Post by Cavsfan on 2012-06-11
Drs305 you beat me to it! :)

---

### Post by timcowchip on 2012-06-11
```
sudo gedit /etc/default/grub
```

GRUB_DEFAULT="0" can be changed to 2 or any number (0,1,2,3...) to boot the 0th or 1st or 2nd or 3rd entry in /boot/grub/grub.cfg.

make sure to run 

```
sudo update-grub
```

afterwards

---

### Post by Cavsfan on 2012-06-11
> **timcowchip said:**
> ```
sudo gedit /etc/default/grub
```GRUB_DEFAULT="0" can be changed to 2 or any number (0,1,2,3...) to boot the 0th or 1st or 2nd or 3rd entry in /boot/grub/grub.cfg.

make sure to run 

```
sudo update-grub
```afterwards

Yes but, every time a kernel gets installed one would have to edit the file again.
My How to makes it where you never have to edit anything ever period.

I have mine defaulting to windows 7 for the wife. I never have to edit anything.

---

### Post by PapaGary on 2012-06-11
> **Lism said:**
> I've been wondering this for ages,

I have W7 and Ubuntu installed to dual boot and they work fine. However upon switching on the machine you have to wait for the boot manager then select Ubuntu before 10 seconds are up, so I was wondering if I can prioritize which OS to boot so I can switch on the machine and walk away and let it boot.

Thanks
Uh, wait a minute. The default grub menu will boot to the latest version of Ubuntu if nothing is selected within the 10 second interval. Is yours different? If you turn it on and walk away what didl it boot to while you were gone?

---

### Post by Lism on 2012-06-11
Thanks guys, really helped a lot. I love this forum, help is always seconds away.

---

### Post by timcowchip on 2012-06-11
> **Cavsfan said:**
> Yes but, every time a kernel gets installed one would have to edit the file again.
My How to makes it where you never have to edit anything ever period.

I have mine defaulting to windows 7 for the wife. I never have to edit anything.

I believe apt runs "update-grub" when installing a new kernel, so yes it would overwrite /boot/grub/grub.cfg with the Ubuntu entry selected as first choice in the boot menu.

There are other boot-loaders like Lilo in the repository. Lilo will boot partitions by path or UUID. Its boot order should remain the same through kernel upgrades.

---

### Post by Cavsfan on 2012-06-11
> **Lism said:**
> Thanks guys, really helped a lot. I love this forum, help is always seconds away.
You are very welcome!

> **timcowchip said:**
> I believe apt runs "update-grub" when installing a new kernel, so yes it would overwrite /boot/grub/grub.cfg with the Ubuntu entry selected as first choice in the boot menu.

There are other boot-loaders like Lilo in the repository. Lilo will boot partitions by path or UUID. Its boot order should remain the same through kernel upgrades.

Exactly, when I first started using Ubuntu I got tired of changing the default line every time a new kernel got installed.
My wife likes windows 7 and since it was last that default would move up one with every new kernel.
So, a really sharp user on here **ranch hand** told me how to customize it. It's pretty straightforward.
Between **ranch hand** and **drs305** I learned a lot about grub and put the tutorial together.
At first it was overwhelming but, as a few days passed I went for it and am happy I did.
I have mine defaulted to windows 7 and 60 seconds on the timer because sometimes I am not too fast.
So, if it boots, it goes into Windows 7. My wife and son use windows 7 mostly but, my son is in the Army now.

---

