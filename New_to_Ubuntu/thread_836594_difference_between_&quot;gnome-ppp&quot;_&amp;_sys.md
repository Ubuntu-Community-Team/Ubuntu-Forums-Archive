---
title: "difference between &quot;gnome-ppp&quot; &amp; system/administration/network"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by wpshooter on 2008-06-21
What is the difference between the **gnome-ppp** that I see listed in Synaptic and the configuration layout that I see under Ubuntu/Gutsy at System/Administration/Network/modem connection, i.e. do they perform the same function(s) ?

Thanks.

---

### Post by cariboo on 2008-06-21
Gnome-ppp and all the others are just a gui front end for the ppp daemon. If pppd is loaded you can dial from the command line for example:

```
atdt2505551234
```

will dial the number, you should here it dial and ring if it is a valid number.

Jim

---

### Post by wpshooter on 2008-06-21
If I place all of the correct parameters in the System/Administration/Network/modem connection section and then ENABLE the modem therein listed, will that initiate the dialup connection of the modem to the ISP ?

Thanks.

---

### Post by editrix on 2008-06-21
> **wpshooter said:**
> If I place all of the correct parameters in the System/Administration/Network/modem connection section and then ENABLE the modem therein listed, will that initiate the dialup connection of the modem to the ISP ?

Well, you could always just try it :-)

Sorry, I don't use Gnome so I don't know. But it sounds reasonable.

---

### Post by cariboo on 2008-06-21
I always found Kppp to be easier to setup a dialup connection. But if you don't have a internet connection I guess you you can't download it to try it:)

Jim

---

### Post by wpshooter on 2008-06-21
> **editrix said:**
> Well, you could always just try it :-)

Sorry, I don't use Gnome so I don't know. But it sounds reasonable.

Well, I have been trying it for about the last 4 hours with every conceivable combination of parameters that I could come up with and and have not gotten it to work yet.

If the modem is showing up in the hardware description section of Ubuntu does that necessarily means that it has been installed (including any necessary drivers) by the O/S and it is just waiting for the proper configuration parameters before it can dialup the ISP account.

Thanks.

---

### Post by johnfarrow on 2008-06-21
One of the biggest problems in getting a laptop modem to work under Ubuntu is that you must do all your research and requests for help in Windows and then try to load thatin Ubuntu.  You are constantly trading find out how to configure your modem while you are actually in windows.
     I have stumbled around in the various help sites and finally got my modem to dial and connect but presently am unable to get on a web site or get my mail.

---

### Post by wpshooter on 2008-06-21
> **johnfarrow said:**
> One of the biggest problems in getting a laptop modem to work under Ubuntu is that you must do all your research and requests for help in Windows and then try to load thatin Ubuntu.  You are constantly trading find out how to configure your modem while you are actually in windows.
     I have stumbled around in the various help sites and finally got my modem to dial and connect but presently am unable to get on a web site or get my mail.

I am beginning to think that if you want to connect to the Internet on a Ubuntu computer on a dialup/modem connection that your are just SOL.

I have been trying to get this thing to work about all day and I am seemingly no closer to getting it to work than when I started.

I am assuming that the problem "MAY" be that Ubuntu is not SMART enough to load a driver for these modems when the O/S installation is done.

But I will be heck if I can find a Linux driver for this modem so far !!!  
Lucent ENF656-PCIG-LUPR.

Any suggestions welcomed.

---

### Post by nowshining on 2008-06-22
wpshooter - is ur modem a software one or hardware? ie: internal or external? a win-modem modem is trouble for linux ie: getting it to work.

ubuntu by default doesn't come with any dial-up frontends for wvdial, however kubuntu does.

u can also download the packages from packages.ubuntu.com for ur specific version of ubuntu or earlier.

[http://packages.ubuntu.com/search?keywords=gnome-ppp](http://packages.ubuntu.com/search?keywords=gnome-ppp)

[http://packages.ubuntu.com/search?keywords=kppp](http://packages.ubuntu.com/search?keywords=kppp)

---

### Post by editrix on 2008-06-23
> **wpshooter said:**
> If the modem is showing up in the hardware description section of Ubuntu does that necessarily means that it has been installed (including any necessary drivers) by the O/S and it is just waiting for the proper configuration parameters before it can dialup the ISP account.

Thanks.

No. It just means the system knows it's there. The problem is **not** with Linux, but with a**hole modem manufacturers who will not write drivers for Linux, or allow Linux guys to write them. It's no different from not being able to use hardware that ran on Windows 98 on XP. Laptop modems are especially problematic.

Try here: [http://linmodems.org/](http://linmodems.org/)

---

