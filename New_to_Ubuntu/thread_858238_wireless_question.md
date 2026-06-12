---
title: "wireless question"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by widespread on 2008-07-13
My dell inspiron 8600 has a broadcom BCM4309 wireless card in it.  I know this card is incompatible and I need to configure Xubuntu to work with it. My question is, after looking around the forums, it seems there are a lot of guides/tutorials dealing with broadcom cards, so I was having trouble deciding which one to follow.  Does anyone else have the BCM4309 card working? If so, what guide did you follow?  Thanks for your time.

---

### Post by TSS on 2008-07-13
I have a Broadcom card as well.

Check out this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

From what I can tell, looking at the testimonials, it looks like someone else has gotten a Broadcom 4309 working using that guide.

S/he said:
> 
Dell Latitude X300; lspci = "Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)"; Chipset = 14e4:4324 (rev 02); Ubuntu 7.10; uname -mr = "2.6.22-14-generic i686"; Used step 2b; using non-compiled ndiswrapper gave me some functionality, but I had to start all networking from command line; compiling ndiswrapper gave me full gui functionality! Thanks!


Be sure to take note of that as you follow the guide!  Post here if you have any questions.

EDIT:  On second thought, it looks like the bcm43xx driver is supposed to support that card ([http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)).  What happens when you type:
```
sudo modprobe bcm43xx
```

---

### Post by Bachstelze on 2008-07-13
There are two possible approaches with Broadcom WiFi chipsets:

1) Use the bcm43xx driver that is shipped with Ubuntu. The problem is that this driver needs a firmware that, on the other hand, can not be shipped with Ubuntu. It is, however, very simple to install if you can get your laptop wired temporarily, it's just a matter of

```
sudo apt-get install bcm43xx-fwcutter
```


2) Use ndiswrapper, which is an utility through which Ubuntu (and Linux in general) can make use of Windows drivers. It is a bit more complicated, but nothing really nasty either. Search for it on the forums or the Wiki for details.

I personnally would favour the first one, as it uses a native Linux driver. It seems to cause problems with the newest chipsets (4311+) but since yours is a 4309, it should be fine.

---

### Post by jualin on 2008-07-13
I have a BCM4306 and it worked perfectly after following the guides. I tried the Ndiswrapper approach because the native linux driver didn't work.

---

