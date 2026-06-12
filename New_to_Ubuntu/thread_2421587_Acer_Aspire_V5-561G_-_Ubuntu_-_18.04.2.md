---
title: "Acer Aspire V5-561G - Ubuntu - 18.04.2"
date: 2019-06-24
forum: New to Ubuntu
---

### Post by grenic on 2019-06-24
Good afternoon,

I have done the upgrade this morning from Windows to Ubuntu on my Acer Aspire V5-561G laptop.

Is it necessary to install any bios, graphics, audio or motherboard drivers? 

Is there anything else that is important for me to install?

Greg

---

### Post by VMC on 2019-06-24
I have a new Acer also. Did you go to Acer web site and check for driver upgrades. The BIO was the only one I needed. Easy to install.

Go here and enter your serial number:
[https://www.acer.com/ac/en/US/content/support](https://www.acer.com/ac/en/US/content/support)

---

### Post by grenic on 2019-06-24
> **VMC said:**
> I have a new Acer also. Did you go to Acer web site and check for driver upgrades. The BIO was the only one I needed. Easy to install.

Go here and enter your serial number:
[https://www.acer.com/ac/en/US/content/support](https://www.acer.com/ac/en/US/content/support)

After submitting serial number it only prompts me with Windows 10 & 8 Operating Systems, no Linux.

I have noticed that my microphone on my headphones is not working as it did. Looking for Acer audio driver for Ubuntu.

Do you think installing Kubuntu may be better?

---

### Post by VMC on 2019-06-24
I think those drivers need Windows to install.

---

### Post by oldfred on 2019-06-24
Is this an older system? is this similar.
       Acer V5-571P-6815 secure boot off worked Shows Diskpart 
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)

You do need to update UEFI/BIOS from Acer. Some old ones had to be downgraded to work, but newer ones all seem to be ok.

All Acer have a unique requirement of setting "trust" after install from within UEFI.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[URL="https://ubuntuforums.org/showthread.php?t=2358003"]https://ubuntuforums.org/showthread.php?t=2358003
      [/URL]
 Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator) 
    

[URL="https://ubuntuforums.org/showthread.php?t=2358003"]
[/URL]

---

### Post by oldrocker99 on 2019-06-24
It is almost certain that the drivers for the laptop are already in the kernel, like 99% of device drivers, which is why Ubuntu, or any other distribution, "just works."

A printer driver, and almost all of them have Linux drivers, and nVidia drivers, if you have onboard nVidia graphics, need to be installed from the PPA.```
sudoapt-add-repository ppa:graphics-deivers/ppa
sudo apt update
sudo apt install nvidia-410
```

If you have Intel or AMD/ATI graphics, the best drivers, being open source, are already installed.

---

### Post by grenic on 2019-06-24
Thank you for the detailed response. This Ubuntu community is great! &#128077;

> **oldrocker99 said:**
> It is almost certain that the drivers for the laptop are already in the kernel, like 99% of device drivers, which is why Ubuntu, or any other distribution, "just works."

A printer driver, and almost all of them have Linux drivers, and nVidia drivers, if you have onboard nVidia graphics, need to be installed from the PPA.```
sudoapt-add-repository ppa:graphics-deivers/ppa
sudo apt update
sudo apt install nvidia-410
```

If you have Intel or AMD/ATI graphics, the best drivers, being open source, are already installed.

---

