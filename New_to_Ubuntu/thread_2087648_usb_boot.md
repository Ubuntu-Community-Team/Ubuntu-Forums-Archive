---
title: "usb boot?"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by Yezinki on 2012-11-24
My machine's slim slot loading optical drive is malfunctioning.

It's BIOS doesn't have a usb option, only Internal optical, HDD, Floppy & Network.

Could you expert members teach how I could use Plop so that can install using usb optical drive?

Hoping to hear from you,

Thanks.

---

### Post by mlentink on 2012-11-24
I don't know plop, but a quick search turned up:
[http://www.plop.at/en/ploplinux/usb.html](http://www.plop.at/en/ploplinux/usb.html)
[http://www.youtube.com/watch?v=N51B0gi-g0U](http://www.youtube.com/watch?v=N51B0gi-g0U)
[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

It seems you will need to open the can which contains the canopener.

---

### Post by Yezinki on 2012-11-24
Thanks mlentink for posting the links. I formatted my machine's HDD & wanted to perform a clean install of Ubuntu not realizing that optical drive might malfunction.

The drive is empty so how do I proceed using this link [http://www.plop.at/en/ploplinux/usb.html](http://www.plop.at/en/ploplinux/usb.html) ?

---

### Post by mlentink on 2012-11-24
If I read the HowToGeek link (the third) correctly, you will first need to load the PloP bootloader, for which you will need an an optical drive. That's what I meant by having to open a can that contains the can-opener. Sorry, but I think you will have to replace you optical drive.

---

### Post by NikTh on 2012-11-24
Hi , 
is this machine has a linux inside ? (already installed). If you have (eg: Ubuntu) and you use grub , then we can add an entry to grub's menu with plop boot manager , see here how : [http://askubuntu.com/questions/220364/boot-off-usb-key-without-bios-support/220386#220386](http://askubuntu.com/questions/220364/boot-off-usb-key-without-bios-support/220386#220386)

But above is the console mode (bit difficult) the GUI mode is easiest. 

Thanks

---

### Post by Yezinki on 2012-11-24
Hi thanks NikTh	for your reply.

There is Grub inside, how do I locate it, add Plop entry & GUI mode?

---

### Post by NikTh on 2012-11-24
> **Yezinki said:**
> 

There is Grub inside, how do I locate it, add Plop entry & GUI mode?

Can you boot and login normally to that Operating System ? What OS it is ? (Ubuntu ? ) 

Login and open a terminal and give the results of 
```
lsb_release -rcd 
uname -a 
cat /boot/grub/grub.cfg
```Click on **"New Reply"** and put the results inside [CODE] tags to be easier to read. [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by Yezinki on 2012-11-24
Thanks again, I can boot in it's Ubuntu. Will Plop always remain in or can be removed later after reinstalling, using usb DVD combo drive?

---

### Post by NikTh on 2012-11-24
> **Yezinki said:**
> Will Plop always remain in or can be removed later after reinstalling, using usb DVD combo drive?

If you re-install the OS , then everything will be lost .. grub bootloader will be replaced and configuration files as well, so you have to follow again the procedure if you want the plop boot-loader in grub menu. 

I guess what you want to achieve here is to boot from usb (because CD/DVD not working and PC has not support for USB-Boot) and install Ubuntu.
Thanks

---

### Post by Yezinki on 2012-11-24
> **NikTh said:**
> If you re-install the OS , then everything will be lost .. grub bootloader will be replaced and configuration files as well, so you have to follow again the procedure if you want the plop boot-loader in grub menu. 

**I guess what you want to achieve here is to boot from usb (because CD/DVD not working and PC has not support for USB-Boot)** and install Ubuntu.
Thanks

So true, exactly NikTh.

---

### Post by Yezinki on 2012-11-24
```
vaio@VGC-LS1:~$ lsb_release -rcd 
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
vaio@VGC-LS1:~$ uname -a 
Linux VGC-LS1 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux
vaio@VGC-LS1:~$ cat /boot/grub/grub.cfg

```

---

### Post by Yezinki on 2012-11-24
```
vaio@VGC-LS1:~$ lsb_release -rcd 
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
vaio@VGC-LS1:~$ uname -a 
Linux VGC-LS1 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 i686 i386 GNU/Linux
vaio@VGC-LS1:~$ cat /boot/grub/grub.cfg

```

---

### Post by Yezinki on 2012-11-24
When I was running W7 Pro on this machine at times this optical drive use to stall while using a burn app giving an I/O error donno what that means?

Thanks.

---

### Post by NikTh on 2012-11-24
> **Yezinki said:**
> When I was running W7 Pro on this machine at times this optical drive use to stall while using a burn app giving an I/O error donno what that means?

Well , in general and I/O error is an Input/Output error when a program or an O.S not communicate well with a device . (in your case the CD-rom device). 

What possibly could be wrong ? (for CD/DVD)


[LIST=1]
[*] Device is damaged , so you need to replace the device
[*]CD/DVD  disk is corrupted or dirty so you have to re-burn it
[*]The software driver is not good , so you have to update it or replace it or use another software.
[/LIST]
 
I/O error is a communication error that can be caused in various ways.

Thanks

---

### Post by Yezinki on 2012-11-24
Thanks for explaining the causes of I/O error.

I have observed that it doesn't run +R media properly, tried installing Ubuntu burnt on a new Verbatim DVD+R did bad vs when installed on a cheap 50 cent DVR-R?

Could you care to explain how I could boot install using Sony usb DVD combo vs Internal Matshita DVD-RAM drive?

Regards!

---

### Post by Yezinki on 2012-11-24
Thanks NikTh any ways. I shall try to install configure Plop, though might take a while at my age but shall search.

Regards.

---

### Post by NikTh on 2012-11-25
> **Yezinki said:**
> 

Could you care to explain how I could boot install using Sony usb DVD combo vs Internal Matshita DVD-RAM drive?

I saw that you marked the thread as solved , so I guess you achieved your goal  ( ? )

If you want to install from an external USb-DVD , then you have to configure BIOS to boot first from this device. 

1) Plug in the device 
2) Power on the PC 
3) hold down the key to go in to BIOS config page 
4) Change boot priority (set first the USB-DVD device) 
5) Put the CD/DVD disk inside 
6) Hit F10 to save the BIOS configuration and boot . 

Thanks

---

### Post by Yezinki on 2012-11-25
Hi NikTh I marked it as solved thinking that is big issue & who would want to assist........

I know that but my machine's BIOS has NO usb option, just Internal Optical, HDD, Floppy & Network, so what do I do?

Thanks.

---

### Post by NikTh on 2012-11-25
Well, some BIOS recognize such devices (external USB-DVD) , even if not have USB general support.

Check first as I told you (steps above)  if BIOS recognize the device in boot order. If not , then the only thing you can do is to attach a new internal CD/DVD device 
or
try to configure plop boot-loader. 

Thanks

---

### Post by Yezinki on 2012-11-25
Thanks again shall do that.

---

