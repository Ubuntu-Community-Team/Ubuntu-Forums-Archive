---
title: "Need instructions to install video driver"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by Fennecat on 2011-11-06
My motherboard's graphics chip isn't supported very well by Ubuntu.

The manufacturer has a Linux driver on its website, but there  are no instructions, no README file, and I don't know my way around  Terminal.

[http://downloadcenter.intel.com/Deta...adType=Drivers]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15443&ProdId=2873&lang=eng&OSVersion=Linux*&DownloadType=Drivers")

Will someone please tell me how to properly extract and install the i386 driver?

---

### Post by apollothethird on 2011-11-06
> **Fennecat said:**
> My motherboard's graphics chip isn't supported very well by Ubuntu.

The manufacturer has a Linux driver on its website, but there  are no instructions, no README file, and I don't know my way around  Terminal.

[http://downloadcenter.intel.com/Deta...adType=Drivers]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15443&ProdId=2873&lang=eng&OSVersion=Linux*&DownloadType=Drivers")

Will someone please tell me how to properly extract and install the i386 driver?

Since the manufacturer has support for Linux the support might also be provided via the repository.

Try running additional drivers:

Dash Home -> More Apps -> [type in] Additional Drivers.

Follow the gui prompts.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/@ljames](www.apollo3.com/@ljames)

---

### Post by Fennecat on 2011-11-06
> **apollothethird said:**
> Try running additional drivers Got the oneiric version of this. :(

[IMG]http://www.dedoimedo.com/images/computers_new_1/ubuntu-9-4-updates-no-drivers.png[/IMG]

---

### Post by waynefoutz on 2011-11-06
The intel drivers are built into the kernel. There is nothing to download or install. What you get out of the box is about as good as it gets.

---

### Post by Fennecat on 2011-11-06
> **waynefoutz said:**
> The intel drivers are built into the kernel. There is nothing to download or install. What you get out of the box is about as good as it gets.
My board uses a SiS chipset.  The kernel drivers produce vertical tearing.

---

### Post by raja.genupula on 2011-11-06
post that output here

```
  lsmod | grep video
```

---

### Post by Fennecat on 2011-11-06
> **raja.genupula said:**
> post that output here

```
  lsmod | grep video
```
Nothing happens

---

### Post by raja.genupula on 2011-11-07
that means your drivers are not installed properly . 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://www.pendrivelinux.com/installing-proprietary-video-drivers-for-ubuntu/](http://www.pendrivelinux.com/installing-proprietary-video-drivers-for-ubuntu/)

---

### Post by hguant on 2011-11-07
Try typing in 

```
lspci
```

to the terminal, that should tell you what drivers are installed currently. Won't solve your problem but it's a start.

---

### Post by Fennecat on 2011-11-07
> **raja.genupula said:**
> that means your drivers are not installed properly .  My graphics are neither Nvidia nor ATI, the maker isn't common so I'm not surprised the repository's driver is buggy.

---

### Post by Fennecat on 2011-11-07
> **hguant said:**
> Try typing in 

```
lspci
```to the terminal, that should tell you what drivers are installed currently. Won't solve your problem but it's a start.
```
VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 04)
``` The board's manual says it has the 662.

---

### Post by raja.genupula on 2011-11-07
[http://blog.bigsmoke.us/2011/01/18/ubuntu-sis-671-driver](http://blog.bigsmoke.us/2011/01/18/ubuntu-sis-671-driver)

---

### Post by wildmanne39 on 2011-11-07
Hi, I believe the SIS driver is no longer supported because it is so old, I do not think there is anything you can do to make it work properly in newer releases.

I looked at that link and it is three years old so it will not work with a new release and I searched and it does appear that it is not supported anymore, I have one of those myself and my will not even show a screen.
Thank you

---

### Post by Fennecat on 2011-11-07
> **raja.genupula said:**
> [http://blog.bigsmoke.us/2011/01/18/ubuntu-sis-671-driver](http://blog.bigsmoke.us/2011/01/18/ubuntu-sis-671-driver)

Tried it, but '/user/bin/vim' gives me 'No such file or directory'

If someone could give me instructions on how to unzip and implement the driver from the link in my original post the way your link did (but updated for Oneiric's paths) that would be perfect!

---

### Post by Fennecat on 2011-11-07
> **wildmanne39 said:**
> I looked at that link and it is three years old so it will not work with a new release 

I have one of those myself and my will not even show a screen.
I've tried with this board with each release of Ubuntu and it's NEVER had a working driver in the repository.

Before installing hit F6 and type 'xforcevesa'. That limits you to low resolution 4:3 aspect ratios, but there's no vertical lines, tearing, or glitches.

---

