---
title: "Language pack without wifi"
date: 2019-12-31
forum: New to Ubuntu
---

### Post by thoven2 on 2019-12-31
Hello,

I forgot my system password, but I also disabled wifi from BIOS.  So, basically, I can't use wifi.

How do I install language pack, specifically Korean, from flash drive?

Thanks in advance!!

---

### Post by Skaperen on 2019-12-31
you posted here ok, from somewhere.  can whatever this is (your phone?) download the .deb file and put it on media (USB memory stick or SD card?) that your PC can read?

---

### Post by Impavidus on 2020-01-01
What system password did you forget? The bios password? There are usually ways to reset it.

It is possible to use Ubuntu on a computer without networking, but it's a bit harder to install software and updates. Of course, you don't really need those security upgrades without networking, as hackers can't get in anyway.

---

### Post by thoven2 on 2020-01-01
Bios password...  I think the way to do it is to get into the motherboard and reset a switch.  So, I use Xubuntu 18.04, and I am a newbie with absolutely no knowledge what Linux is all about.  From the following website ([https://pkgs.org/download/language-pack-ko](https://pkgs.org/download/language-pack-ko)), which one is compatible? And is there a way to get the download package from launchpad ([https://launchpad.net/~xubuntu-dev)?](https://launchpad.net/~xubuntu-dev)?)

I found another link: [https://pkgs.org/download/korean](https://pkgs.org/download/korean)

---

### Post by Impavidus on 2020-01-02
If you use Xubuntu 18.04, use the one for Ubuntu 18.04. Ubuntu, Xubuntu and the other flavours all use the same repositories with the same packages, the only difference is the list of packages that get installed by default.

Another option is to get networking via your phone, assuming your phone can connect to your wifi (or the cellular network, but that may get expensive) and you can plug it into a usb port of your computer. Then you can simply use the package manager to download and install any package you like.

---

### Post by thoven2 on 2020-01-02
I downloaded language-pack-co.deb (from [https://ubuntu.pkgs.org/18.04/ubuntu-main-amd64/language-pack-ko_18.04+20180423_all.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-amd64/language-pack-ko_18.04+20180423_all.deb.html)), but it still won't install.  The size is 2kb, so I think the installer still requires wifi to download actual file.
So, you mean, install linux package manager on my phone and use it to install on my laptop?  I will try one more method before I smash this laptop.  Thanks for your help in advance.

---

### Post by Impavidus on 2020-01-02
language-pack-ko depends on language-pak-ko-base, which contains most of the data. When you download and transfer packages manually, you have to handle dependencies yourself. That's why having internet access is easier.

By using your phone I mean tethering it. Connect your phone to your wifi, connect it to your computer by usb and enable sharing the network on your phone. The computer should recognise your phone as a usb modem and connect to internet. Then use the package manager on your computer to install whatever you like.

---

### Post by leroy1379 on 2020-03-16
> **thoven2 said:**
> I downloaded language-pack-co.deb (from [https://ubuntu.pkgs.org/18.04/ubuntu-main-amd64/language-pack-ko_18.04+20180423_all.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-amd64/language-pack-ko_18.04+20180423_all.deb.html) [MCDVOICE]("https://www.mcdvoice.page/")), but it still won't install.  The size is 2kb, so I think the installer still requires wifi to download actual file.
So, you mean, install linux package manager on my phone and use it to install on my laptop?  I will try one more method before I smash this laptop.  Thanks for your help in advance.
yup thats great i will try this for sure ..

Thanks

---

