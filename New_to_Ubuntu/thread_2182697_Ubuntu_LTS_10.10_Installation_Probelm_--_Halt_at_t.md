---
title: "Ubuntu LTS 10.10 Installation Probelm -- Halt at the session &quot;who are you ?&quot;"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by K.F.Lee on 2013-10-22
Hi,

I am a new user. Am trying to install the Ubuntu LTS 10.10RC from CD (downloaded and burnt into CD) however it halts at the session "Who are you ?", i.e. at the session where need to fill in the user name, computer and passwords etc, i.e. the forward button is not available for me to click. 

The bottom part of the screen shows "Ready when you are ..." 

How do I procedd ? Need and appreciate an advice. Thanks !

Kim Lee

---

### Post by Impavidus on 2013-10-22
Ubuntu 10.10 is no LTS release and is unsupported. Currently supported releases are 10.04 LTS (till 4/2015, server only), 12.04 LTS (till 4/2017, the latest LTS), 12.10 (till 4/2014), 13.04 (till 1/2014) and 13.10 (till 7/2014, the latest release). I recommend you try installing 12.04 LTS or 13.10. Unsupported releases are less secure and are more difficult to fix in case of problems. If you think your hardware cannot handle the latest Ubuntu (or if you don't like the new user interface), try Xubuntu 12.04 LTS, Xubuntu 13.10 or Lubuntu 13.10 (no LTS for Lubuntu).

That being said, I think the installation process is similar. Have you given all information the installer asks for and checked your hardware and available disk space is sufficient?

Maybe you can give us some details on your hardware.

---

### Post by BBQdave on 2013-10-22
I recommend giving Ubuntu Unity 12.04LTS a go. Depending on the age of your hardware, you may want to consider Xubuntu :)

---

### Post by K.F.Lee on 2013-10-22
Thanks for the information.

The embedded target system that I am working on is using NXP LPC3250 and per my understanding the versions that Linux Kernel has been tested is 2.6.27.8 and 2.6.34

Through some search and got to know that 10.10 is using Linux Kernel 2.6.35 hence has selected and tried to install it; however have overlooked that it is not LTS, thanks for pointing out.

As a matter of fact it is very difficult to know which Ubuntu LTS is using which version of the Linux Kernel, may I know 12.04 LTS is using which Linux Kernel ? Or rather when could find the "look-up" table ?

My notebook is having Intel Core 2 Duo CPU P8600 @ 2.4 GHz, 4G RAM and harddisk space is having 60G free (never use) partition and the Ubuntu installer has further partition this 60G into 2~3 smaller partitions.

After posted the earlier thread and have tried again and noticed that when I suspended  the installation by clicking the suspend option at the top right corner at the stage that I mentioned earlier, the installation stopped and I saw an error message saying something like user id related ... would copy down the message tomorrow when back to the office.

Appreciate your advice and thanks again !

---

### Post by BBQdave on 2013-10-22
> **K.F.Lee said:**
> My notebook is having Intel Core 2 Duo CPU P8600 @ 2.4 GHz, 4G RAM and harddisk space is having 60G free...

I would go with Ubuntu Unity 12.04LTS AMD 64 - *64 bit*, current kernel is Kernel Linux 3.2.0-55.

I have had no issues with this system - installed on a Lenovo Intel Core 2 Duo notebook with 2G of RAM :)

No problems with Ubuntu Unity 12.04LTS AMD 64 on a Toshiba Satellite c655-s5503. 12.04LTS is a solid distro.

---

### Post by mastablasta on 2013-10-22
is this similar to what you are working on?: [http://phytec.com/products/system-on-modules/phycore/lpc3250/](http://phytec.com/products/system-on-modules/phycore/lpc3250/)
well you can still try latest LTS (12.04). new kernel doesn't really drop the older stuff so much. they mostly add new features (power management etc.) 

besides if you work on ARM devide you use need different kernel there anyway (the kind that is compiled for ARM CPU).

10.10 should still install (eventhough it is not supported anymore), but it could be something is not good with the download. make sure you check the md5sum of the iso: [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM
[/URL]
anyway more on kernels: [https://wiki.ubuntu.com/Kernel](https://wiki.ubuntu.com/Kernel)
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html](http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html)

even within a version the kernel gets updated regulary as bugs and security holes get patched.

---

### Post by K.F.Lee on 2013-10-22
A quick fundamental quick question : must the Linux Kernel version on the desktop be the same as the embedded target system as it is cross-compiled from the desktop to the embedded target system ? Thanks !

By the way any clue that why the installation process stopped at the "Who are you ?" session, i.e. the forward button could not be clicked ?

---

### Post by SeijiSensei on 2013-10-22
If you want to use a 2.6 kernel, I recommend installing CentOS instead of Ubuntu.  The current 6.4 version of CentOS ships with kernel version 2.6.32.  CentOS is a RedHat clone and, as such, tends to rely on older kernels with backported security upgrades.

---

### Post by grahammechanical on 2013-10-22
That problem could indicate that there is something incorrect about the user information being given. Newer version of Ubuntu give a better indication when something is wrong than those older versions. It could be that the password has capital letters. It is a long way back in memory but I think there was an issue using capital letters in passwords or something like that. "Ready when you" is the installer waiting for you to put things right and then you will get an option to move forward. I am just guessing about all of this.

Regards.

---

### Post by pqwoerituytrueiwoq on 2013-10-22
> **Impavidus said:**
> Ubuntu 10.10 is no LTS release and is unsupported. Currently supported releases are 10.04 LTS (till 4/2015, server only), 12.04 LTS (till 4/2017, the latest LTS), 12.10 (till 4/2014), 13.04 (till 1/2014) and 13.10 (till 7/2014, the latest release). I recommend you try installing 12.04 LTS or 13.10. Unsupported releases are less secure and are more difficult to fix in case of problems. If you think your hardware cannot handle the latest Ubuntu (or if you don't like the new user interface), try Xubuntu 12.04 LTS, Xubuntu 13.10 or Lubuntu 13.10 (no LTS for Lubuntu).

That being said, I think the installation process is similar. Have you given all information the installer asks for and checked your hardware and available disk space is sufficient?

Maybe you can give us some details on your hardware.

I would sugest xubuntu 12.10 over 12.04, xubuntu 12.04 seemed incomplete to me, 12.10 will be supported until 14.04 LTS is released and direct upgrade will be possible

---

### Post by K.F.Lee on 2013-10-23
Have found the root cause, it is due to my earlier used ID consists of charater "." and as mentioned by Grahammechnical "Ready when you are ..." means the installer waiting for the user to put things right prior open the option to move forward. 

By the way have downloaded and installed 12.04 LTS.

Back to my earlier fundamental quick question : must the Linux Kernel version on  the desktop be the same as the embedded target system as it is  cross-compiled from the desktop to the embedded target system ? Thanks !

---

### Post by 3rdalbum on 2013-10-23
No, the running kernel doesn't matter. Kernels and kernel modules are not compiled against the running kernel, they are compiled against the source code of a kernel. Big difference. You might need to download the kernel headers or kernel source code for the kernel version you want to target.

Of course, for just general programs you don't need to worry about the kernel at all.

---

