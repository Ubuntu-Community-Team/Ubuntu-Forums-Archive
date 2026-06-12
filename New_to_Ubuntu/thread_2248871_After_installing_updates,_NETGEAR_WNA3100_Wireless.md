---
title: "After installing updates, NETGEAR WNA3100 Wireless adapter no longer works"
date: 2014-10-17
forum: New to Ubuntu
---

### Post by TriforceOfKirby on 2014-10-17
So I installed Ubuntu along side Windows Vista a couple days ago, I followed this forum: [http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251) and installed ndiswrapper to get my wireless adapter to work on Ubuntu, but after installing updates and rebooting, the wireless adapter can't connect to the internet, the light on it turns on, but it just won't connect anymore. I think it installed the wrong update to the driver, is there a way to revert it?

---

### Post by Vladlenin5000 on 2014-10-17
Hi, welcome.

Have you repeated the procedure already?

---

### Post by TriforceOfKirby on 2014-10-17
Yes I tried to repeat the procedure, after i get to the command:
```
sudo ndiswrapper -i ~/bcmn43xx64.inf
```
It says it is already installed; however, it is still not working. It was working before I accepted to install updates, I could browse the web and such, but after it prompted me to reboot after installing updates, it no longer works.

---

### Post by Vladlenin5000 on 2014-10-18
Well, perhaps it's for the best... ndiswrapper is horrible anyway and I bet it was performing below standards before. 
There are dozens of cheap dongles with native support.

---

### Post by TriforceOfKirby on 2014-10-18
Ok so I reinstalled Ubuntu and ndiswrapper and wireless is working again, I haven't allowed any updates yet as I think it may cause it to not work again. Although it's still probably best to get a better wireless adapter with native support, do you have any recommendations?

---

### Post by Vladlenin5000 on 2014-10-18
First thing you should be aware of is that brand/model are irrelevant. Vendor tend to aggregate under the same model 2, 3 or more different hardware with similar characteristics/performance. The way they differentiate them is by revision numbers. R1 of model X are natively supported whereas the same model X but R2 or R3 aren't.

Almost all Intel based are natively supported; most Realtek ones are also natively supported but avoid brand new chipsets if you don't want to compile drivers; many Atheros also have good support; avoid most Broadcom or Ralink/Mediatek ones.
I usually recommend Realtek 8191SU but that's just because I happen to have several. There are many other good options.

---

### Post by mörgæs on 2014-10-18
> **Brandon_Schumann said:**
> Ok so I reinstalled Ubuntu and ndiswrapper and wireless is working again, I haven't allowed any updates yet as I think it may cause it to not work again. Although it's still probably best to get a better wireless adapter with native support, do you have any recommendations?


You should apply all updates as soon as possible and fix problems later, if any appear. 

If Ndiswrapper works why search for new hardware?

---

### Post by verymadpip on 2014-10-19
> **mörgæs said:**
> 
If Ndiswrapper works why search for new hardware?

Hi there.
You may find you'll only have to repeat the procedure after kernel updates.
IIRC that was how it worked with my Netgear WPN111 adapter.
I didn't mind spending the 5 minutes on Ndiswrapper as it meant I could spend the £20 on something else.
 However, each to their own.

---

### Post by TriforceOfKirby on 2014-10-20
Ok thank you, I think I'll just invest in another wireless adapter, even though it works with ndiswrapper, the performance is pretty bad, download speed is about a quarter of what it is on Windows. I planned on playing graphics intensive, online multiplayer games on Ubuntu, so higher performance is a must. Alternatively, I might be able to swap wireless adapters with a relative that uses windows 8. Also, how hard is it to compile drivers? I've done alot of coding with C++ in the past, so that may be an option.

---

### Post by JeQhdMD on 2014-10-20
TP-Link 722n . . . excellent performance plus plug and play.    Has external antennae which improves range.    If you prefer a smaller nano type usb dongle (like a wireless mouse dongle), then I suggest the Panda Ultra Wifi adapter.   These are available on Amazon and in the $15-25 range.

---

### Post by snowmobiler on 2014-10-21
The Panda 300Mbps wireless adapter (amazon -$20), gets great reviews for plug and play with Ubuntu. Has the high gain antenna. I am using Netgear WNA1100 (N150) and they seem to work well.

---

### Post by TriforceOfKirby on 2014-10-22
Ok I got the [COLOR=#000000]TP-Link 722n, works really well, thanks.[/COLOR]

---

