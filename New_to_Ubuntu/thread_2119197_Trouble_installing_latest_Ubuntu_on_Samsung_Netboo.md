---
title: "Trouble installing latest Ubuntu on Samsung Netbook"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by tylercheribini on 2013-02-23
Hi

I am attempting to install the latest ubuntu on a Samsung NP-NC110 netbook. This came pre installed with Windows 7 Home Edition. I have already formatted drive completely(samsung recovery partition included) and did a fresh install of Windows 7 Ultimate with no problems. However I want the option of at least a dual boot with Ubuntu. I followed all the correct procedure(swap space etc etc) as documented on the ubuntu site, numerous times to no avail. it seems to install o.s but when it goes to reboot for last time before first boot of o.s it freezes at a black screen generally. i have googled this and seems to be a specifice problem with my model of netbook as others have had the exact same problem. Some have speculated on other forums that the device is essentially "booby trapped" to install only windows o.s's. others have also mentioned missing bootloader file(grub?) preventing ubuntu from loading. As stated I carefully followed the intructions during install stage. I tried every possible combination of various drives, swap spaces etc but no sucess

I would really appreciate any advice

Thanks

---

### Post by JRV on 2013-02-23
Most netbooks use the Intel Atom processor which is not compatible with the PAE kernel.

Your best bet is to install 12.04 LTS (Precise)
from the netboot image here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

---

### Post by mapes12 on 2013-02-23
When the machine reboots do you get the grub boot loader to give you the option of which os to launch? If no then boot from a live USB/CD connected to internet and install Boot Repair. Run it to see if it fixes your grub config. BTW, I have never had a problem with Atom based processors.

---

### Post by tylercheribini on 2013-02-24
> **JRV said:**
> Most netbooks use the Intel Atom processor which is not compatible with the PAE kernel.

Your best bet is to install 12.04 LTS (Precise)
from the netboot image here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

cheers,will try that and let u know how i get on thx

---

### Post by tylercheribini on 2013-02-24
> **mapes12 said:**
> When the machine reboots do you get the grub boot loader to give you the option of which os to launch? If no then boot from a live USB/CD connected to internet and install Boot Repair. Run it to see if it fixes your grub config. BTW, I have never had a problem with Atom based processors.

yes i do get that option screen. On first reboot after install it went through a few more stages sucessfully before the ubuntu logo appearing on a purple screen. Then a DOS style screen appeared with a lot of text, too much to take everything down. i recorded where i think the problems were though.

"mountall:swapon/host/ubuntu/disk/swap.disk[6615]terminated wuth status 255
mountall:problemactivatingswap/host/ubuntu/disk/swap.disk

<alot more similar lines after this apparantly showing sucessful stages of installation so i didnt take them down>

<last few lines as follows>
"starting regular background program processing dameon
starting deferred execution scheduler
stopping save kernel messages
starting CPU interrupts balancing daemon

<it then hangs indefinitely and i press the power button to power off>

Please note i get this same screen regardless of using windows installer for ubuntu or using usb boot to install and following correct partition instructions from ubuntu site. have also tried both versions of ubunut from website

Thanks in advance

---

### Post by tylercheribini on 2013-02-24
> **JRV said:**
> Most netbooks use the Intel Atom processor which is not compatible with the PAE kernel.

Your best bet is to install 12.04 LTS (Precise)
from the netboot image here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

hi sorry, im a bit of a noob to this kind of thing, which files exactly do i download and what do i do?thx.

---

### Post by Maskedrose on 2013-02-24
If this is helps at all, I installed Ubuntu 12.04 LTS flawlessly with the Windows Installer. 

All I did was download it from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

-------------------
**Windows installer**

 				With Wubi, our officially supported Windows installer for Ubuntu  Desktop, you can install and uninstall Ubuntu easily and safely.
---------------------




It also kept Windows 7 on my drive so I can boot from that if I want (but ugh why would I? I actually stopped using my netbook because I much prefer my Ubuntu desktop PC)




Have an ethernet handy as you will not have a wireless driver installed by default. It'll do it automatically when you go to drivers in your system settings as long as you have your wired connection. 



HP Mini w/ Intel Atom btw. 



Let me know how this goes.

---

### Post by tylercheribini on 2013-02-24
> **Maskedrose said:**
> If this is helps at all, I installed Ubuntu 12.04 LTS flawlessly with the Windows Installer. 

All I did was download it from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

-------------------
**Windows installer**

 				With Wubi, our officially supported Windows installer for Ubuntu  Desktop, you can install and uninstall Ubuntu easily and safely.
---------------------




It also kept Windows 7 on my drive so I can boot from that if I want (but ugh why would I? I actually stopped using my netbook because I much prefer my Ubuntu desktop PC)




Have an ethernet handy as you will not have a wireless driver installed by default. It'll do it automatically when you go to drivers in your system settings as long as you have your wired connection. 



HP Mini w/ Intel Atom btw. 



Let me know how this goes.

Cheers, i tried the wubi installer aswell but it did not work. same problem as using iso

---

### Post by Maskedrose on 2013-02-24
:( Sorry to hear that. 

If you have an extra harddisk lying around maybe install ubuntu onto that and see if the netbook will boot.

---

### Post by JRV on 2013-02-25
> **tylercheribini said:**
> hi sorry, im a bit of a noob to this kind of thing, which files exactly do i download and what do i do?thx.

Download mini.iso, boot from it, and you have a command line based installer.  Then just follow the instructions.

---

### Post by tylercheribini on 2013-02-25
> **JRV said:**
> Download mini.iso, boot from it, and you have a command line based installer.  Then just follow the instructions.

sound.thanks man,ill give it a go.:p

---

### Post by Hylas de Niall on 2013-02-25
> **JRV said:**
> Most netbooks use the Intel Atom processor which is not compatible with the PAE kernel.

Your best bet is to install 12.04 LTS (Precise)
from the netboot image here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

I've never had any problems with pae kernels on either of my netbooks (msi u100 wind and Toshiba nb250) both of which are powered by Atom processors.

---

