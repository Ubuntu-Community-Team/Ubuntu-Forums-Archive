---
title: "Why does my Broadcom Wireless Card stop working after every major update?"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by schabert on 2013-02-19
I have a Dell Precision M6700 with a proprietary Broadcom wireless card. Almost every time that I have installed a new version of the Linux kernel (I am running Ubuntu 12.04) my wireless card either stops working or the network manager thinks forever about connecting but never does. These problems are trivially fixed by booting with an older, stable, version of the Linux kernel but I can't help but wonder if there is a good reason for this behavior. Why can't the developers simply test out their code on machines with Broadcom wireless cards since there are evidently problems with this class of wireless cards with almost every new release? If it is an issue of physically having machines to beta test on I would be happy to volunteer mine since I can always recover pretty easily. One other possibility: could my problems be related to the fact that I'm dual booting Windows and Ubuntu?

---

### Post by kc1di on 2013-02-19
Hello schabert and Welcome to Ubuntu
If I understand you correctly you have seen this behavior when updating kernels.  that makes sense since when the kernel is update the modules being loaded to it would have to be rebuilt. Now that being said Ubuntu is pretty good about doing just that if your using the normal update channel.  I've never had a problem with my broadcom driver when I've upgrade the kernel by the regular ubuntu update manager. 

so I'm assuming that perhaps your installing a newer kernel outside the regular updates.

---

### Post by schabert on 2013-02-19
Thank you for the prompt reply. I'm not sure what you mean by "outside the regular updates." I always use the update manager to install updates and wasn't aware that there was any other method. Actually, now I'm pretty sure that the recurring problems I've been having are related to my dual Windows-Ubuntu configuration. After visiting my Windows partition, switching the WiFi hardware switch on and off a few times, and returning to Ubuntu everything worked fine. Does this make sense?

---

### Post by ptn107 on 2013-02-19
Check to make sure the package 'dkms' is installed.  This will rebuild the kernel modules for each kernel if it is updated.

---

### Post by kc1di on 2013-02-19
> **schabert said:**
> Thank you for the prompt reply. I'm not sure what you mean by "outside the regular updates." I always use the update manager to install updates and wasn't aware that there was any other method. Actually, now I'm pretty sure that the recurring problems I've been having are related to my dual Windows-Ubuntu configuration. After visiting my Windows partition, switching the WiFi hardware switch on and off a few times, and returning to Ubuntu everything worked fine. Does this make sense?

yes,  it sounds like windows is shutting down the hardware on reboot or shutdown, I've seen that happen before.

in Ubuntu you can check to see if there is a hardware or software block on your wireless card by issuing the following command in a terminal:

```
rfkill list all
```
it will give you a list similar to this and if anything is blocked it will say so. 

```
: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
also ptn107's suggestion is a good one ;) 


good luck :)

---

### Post by Kevin McCready on 2013-03-15
For some reason my system is also blocking my wifi
The output of 
#rfkill list all#
is
#0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

#

---

### Post by Kevin McCready on 2013-03-15
The answer was to shutdown the computer, reboot then go into the BIOS and set the DEFAULT for all settings.

---

