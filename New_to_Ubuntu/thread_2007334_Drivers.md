---
title: "Drivers"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by Meelis on 2012-06-20
My Wi-Fi driver was missing from Ubuntu 12.04 disc.
But ubuntu printed out for me where to get that driver.
So why wasn't that driver on 12.04 when the existence of that driver was already discovered?

---

### Post by mlentink on 2012-06-20
I don't rightly know what you mean by "ubuntu printed out for me where to get that driver".
Most drivers are built-in. If you needed one that wasn't there's a high probability you needed a proprietary driver, which are not bundled so as not to infringe on intellectual property.

---

### Post by Meelis on 2012-06-20
Oo i see now. So my Wi-Fi driver is not free driver.
i did search in forum and yes, it's not free driver.
But the driver is downloadable later atleast.

However when i buy computer, why hardware maker won't include driver price together with final hardware price. Maybe they sell it included with Windows price and therefore it's unfair monopol (prohibited by law).
It wouldn't be prblem to pay 20$ more for the computer if i get the pleasant user experience with it's usage.

---

### Post by Mark Phelps on 2012-06-20
> **Meelis said:**
> However when i buy computer, why hardware maker won't include driver price together with final hardware price. 
They DID include the driver -- for the OS that came installed in the computer!

> Maybe they sell it included with Windows price and therefore it's unfair monopol (prohibited by law).
You are obviously NOT a lawyer or you wouldn't make such a ludicrous comment.  These are technical forums, not legal forums.

> It wouldn't be prblem to pay 20$ more for the computer if i get the pleasant user experience with it's usage.
You got with the computer what you paid for.  If you intend to install something extra -- especially something for an OS not included with the computer -- the computer seller would have now way, in advance, of knowing what else to include -- now would they?

---

### Post by wildmanne39 on 2012-06-20
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets and we will see if we can help you.
Thank you

---

### Post by mastablasta on 2012-06-21
> **Meelis said:**
> But the driver is downloadable later atleast.
.
 
 
the driver is probably free as in free beer but not free as in libre. So the code for it is likely closed and distribution for it done by the makers of hardware (i.e. others are not allowed to tinker with it, change it or distribute it but they are allowed to use it).
 
take for example ATI/nvidia windows drivers. you get them on a CD together with the graphics card/computer or you can download and install the latest ones from internet. but you can't make any changes to them and you can't distribuite them yourself.
 
if they did a good job with the drivers then for the end user (in my opinion) it doesn't matter that much.

---

### Post by Meelis on 2012-06-21
Sorry for late replay. The forum didn't load in FireFox 13.0.1

@ wildmanne39
I don't have the laptop with me. It was my fiends laptop who visited me.
It was **Fujitsu Siemens Amilo A1667G**
and manufacturer info about Wi-Fi lists:
*WLAN Gemtek WLAN IEEE802.11 b/g 13ch. Gemtek WMIB-160GW02EU20(LF). Broadcom Wireless LAN 802.11b / 802.11g. WN2302A mPCI WLAN IEEE802.11 b/g. WN2302A-F4 13ch. mPCI WLAN IEEE802.11 b/g (Atheros). *

---

### Post by Meelis on 2012-06-21
@ mastablasta
Ok i got your point.
-------------------------

When i buy new laptop, i take the model with Wi-Fi chipset that has free to distribute drivers.

---

### Post by mastablasta on 2012-06-21
well they are freely distrubuted by broadcom as well as gemtek in yourcase. but not by others. 
And usually to get the wi-fi working all you need to do is connect to internet with a wire and then download the drivers via hardware drivers (or something like that) application. There might be some linux distribution that already include them. i am not sure about that. but you could have a look at distrowatch website if there are any. they might come with a price...

I am not sure which ones are freely available. i have a PCIMCIA card from tp-link that is plug and play (i.e. driver is included in kernel, so no downloading).

---

### Post by wildmanne39 on 2012-06-21
Hi Meelis, we will be happy to help when you are able to post the information that I asked for in my last post, there is no way to tell from what you posted what you need.
Thanks

---

### Post by Meelis on 2012-06-21
> **wildmanne39 said:**
> Hi Meelis, we will be happy to help when you are able to post the information that I asked for in my last post, there is no way to tell from what you posted what you need.
Thanks

Hi

When i booted in live mode i got the text you need to download Wi-Fi driver from [http://linuxwireless.org/en/users/Drivers]("http://linuxwireless.org/en/users/Drivers")
more specific url to correct driver was given. And live boot was canseled (in that time i didn't know how to proceed).
Now i know the internet cable has to be pluged in. But it wasn't clear for me when i had the lap-top in my home (now the laptop owner is in another down far away)

I thank you for your kind effort to help me. I will test it out when i have that lap-top with me.

Meanwhile i plan testing it on my desktop that did run previous Ubuntus ideally, other than Ati driver and or the Screen casting programs very low performance compared to free program CamStudio-Recorder with lagarith lossless codec under Vista 64 home-p.

---

