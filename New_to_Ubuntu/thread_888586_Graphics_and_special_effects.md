---
title: "Graphics and special effects?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Xm3buX on 2008-08-13
When ever I try to enable visual effects, a message appears and says "Desktop effects could not be enabled"

What Do I need to do to get them to work? Do I need a new graphics card? I've heard you can just download a graphics card update to make it work?

Can someone help please?

Thanks.

---

### Post by Tom--d on 2008-08-13
Post the outcome lspci

---

### Post by Xm3buX on 2008-08-13
In the terminal? Here it is:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:08.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```

---

### Post by overdrank on 2008-08-13
> **Xm3buX said:**
> In the terminal? Here it is:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:08.0 Communication controller: Intel Corporation 536EP Data Fax Modem
[COLOR="Red"]01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter[/COLOR]

```

Hi and welcome, the SIS graphics are not well supported and I do not believe the graphics are not capable of running compiz or 3d graphics. You may search the forums for issues with the graphics chipset.

---

### Post by timcredible on 2008-08-13
only ati and nvidia cards are supported for compiz (the program that does all the cool 3d desktop effects that you see on youtube).

---

### Post by overdrank on 2008-08-13
> **timcredible said:**
> only ati and nvidia cards are supported for compiz (the program that does all the cool 3d desktop effects that you see on youtube).

And do not forget intel graphics   :)

---

### Post by Xm3buX on 2008-08-13
> **timcredible said:**
> only ati and nvidia cards are supported for compiz (the program that does all the cool 3d desktop effects that you see on youtube).
How do I go about changing my graphics card?
Do I have to buy a new one and install it into my computer?
Oh, and about how much will it cost?

---

### Post by Tom--d on 2008-08-13
> **Xm3buX said:**
> How do I go about changing my graphics card?
Do I have to buy a new one and install it into my computer?
Oh, and about how much will it cost?

Depends on if your motherboard can support it.

And prices are cheap. 
You just need one which is compatible.

---

### Post by Xm3buX on 2008-08-13
> **Tom--d said:**
> Depends on if your motherboard can support it.

And prices are cheap. 
You just need one which is compatible.

Thanks, how do I find out if it's compatible?
Sorry, I'm a newb at computers](*,)

---

### Post by dhughes on 2008-08-13
> **Xm3buX said:**
> Thanks, how do I find out if it's compatible?
Sorry, I'm a newb at computers](*,)

 How old is the computer, what brand name?

 You pretty much have to find out what slots are available on the motherboard so you know what to buy. For example an old computer may have AGP (there are several types!) but a newer computer would probably have PCI-E slot.

---

### Post by Xm3buX on 2008-08-13
> **dhughes said:**
> How old is the computer, what brand name?

 You pretty much have to find out what slots are available on the motherboard so you know what to buy. For example an old computer may have AGP (there are several types!) but a newer computer would probably have PCI-E slot.
Well, on the tower of the computer, it says acer( model:AcerPower S260), but there is also a sticker on the front saying intel.

---

### Post by dhughes on 2008-08-14
> **Xm3buX said:**
> Well, on the tower of the computer, it says acer( model:AcerPower S260), but there is also a sticker on the front saying intel.

 This?

[http://www.superwarehouse.com/AcerPower_S260_4000/APS260-U-C4000/ps/624268](http://www.superwarehouse.com/AcerPower_S260_4000/APS260-U-C4000/ps/624268)

---

### Post by Xm3buX on 2008-08-14
> **dhughes said:**
> This?

[http://www.superwarehouse.com/AcerPower_S260_4000/APS260-U-C4000/ps/624268](http://www.superwarehouse.com/AcerPower_S260_4000/APS260-U-C4000/ps/624268)

Yeah, except mine doesn't have "4000" on it, but I'm pretty sure that it's that one.

---

### Post by starcannon on 2008-08-14
If thats the same computer, then you have:
1 ( 1 ) x AGP 8x
slot available.

If you were to peek inside it would be an empty slot(assuming its never been upgraded) at the top, often times brown plastic, not always though.

Any of the cards on this page should get you going with desktop effects.
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000048+1305520548&Description=agp&name=NVIDIA&Order=PRICE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000048+1305520548&Description=agp&name=NVIDIA&Order=PRICE)

GL

---

### Post by Xm3buX on 2008-08-14
> **starcannon said:**
> If thats the same computer, then you have:
1 ( 1 ) x AGP 8x
slot available.

If you were to peek inside it would be an empty slot(assuming its never been upgraded) at the top, often times brown plastic, not always though.

Any of the cards on this page should get you going with desktop effects.
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000048+1305520548&Description=agp&name=NVIDIA&Order=PRICE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000048+1305520548&Description=agp&name=NVIDIA&Order=PRICE)

GL

Thanks alot, do you have any idea where I can get that in England, or will it be on amazon or something?

Thanks.

Oh, and would it work if I bought it second hand off ebay?

---

### Post by starcannon on 2008-08-14
> **Xm3buX said:**
> Thanks alot, do you have any idea where I can get that in England, or will it be on amazon or something?

Thanks.

Oh, and would it work if I bought it second hand off ebay?

Go with a series 5xxx or greater, avoid the cards earlier than that.

Ebay results, verify that they are AGP 8x cards with the reseller, and as long as they aren't broken they should work the same as one from a retail shop.
[http://shop.ebay.co.uk/items/__nvidia-agp-8x_W0QQ_nkwZnvidiaQ20agpQ208xQQ_scZ1QQ_sopZ15](http://shop.ebay.co.uk/items/__nvidia-agp-8x_W0QQ_nkwZnvidiaQ20agpQ208xQQ_scZ1QQ_sopZ15)

Amazon results, again verify that the card you decide on is an AGP 8x and if its not broken you should be fine. 
[http://www.amazon.co.uk/s/ref=nb_ss_w_h_/203-0247005-9701505?url=search-alias%3Daps&field-keywords=agp+8x+nvidia&x=0&y=0](http://www.amazon.co.uk/s/ref=nb_ss_w_h_/203-0247005-9701505?url=search-alias%3Daps&field-keywords=agp+8x+nvidia&x=0&y=0)

---

### Post by Xm3buX on 2008-08-14
Thanks ALOT dude, really helpful :D

---

### Post by Tom--d on 2008-08-14
Try looking at [www.dabs.com](www.dabs.com)

Its really good and is in the uk :D

---

### Post by starcannon on 2008-08-14
Yeah this one doesn't look to bad for 20 quid
[http://www.dabs.com/productview.aspx?Quicklinx=3HTV&SearchType=1&SearchTerms=agp+nvidia&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=0](http://www.dabs.com/productview.aspx?Quicklinx=3HTV&SearchType=1&SearchTerms=agp+nvidia&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=0)

---

### Post by Xm3buX on 2008-08-14
> **starcannon said:**
> Yeah this one doesn't look to bad for 20 quid
[http://www.dabs.com/productview.aspx?Quicklinx=3HTV&SearchType=1&SearchTerms=agp+nvidia&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=0](http://www.dabs.com/productview.aspx?Quicklinx=3HTV&SearchType=1&SearchTerms=agp+nvidia&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=0)


And that would definitely run all the effects without a problem, and will work with my computer?

If it does, I'll be getting it soon:cool:

---

### Post by ET! on 2008-08-14
> And that would definitely run all the effects without a problem, and will work with my computer?

If it does, I'll be getting it soon:cool:

if you are not playing any games it would work fine..... you can try this card.. its definitely better than any 5 series

[http://www.dabs.com/productview.aspx?Quicklinx=4XTM&CategorySelectedId=11137&NavigationKey=11137,50810000,42740000,42220000](http://www.dabs.com/productview.aspx?Quicklinx=4XTM&CategorySelectedId=11137&NavigationKey=11137,50810000,42740000,42220000)

it has pixel shader 3 support

---

### Post by vikramaditya on 2008-08-14
Are you dual-booting with windows?  Be sure to disable your motherboard's onboard graphics before you install the new card.  Google will lead you to plenty of good tips.

---

### Post by starcannon on 2008-08-14
> **Xm3buX said:**
> And that would definitely run all the effects without a problem, and will work with my computer?

If it does, I'll be getting it soon:cool:

It should do just fine yes.

+1 to ET!, the 6xxx series is definitely better than the 5xxx series, as with most things the more you spend the more you get. If you've been living with that SiS onboard video though, even a 5xxx series is going to feel like an incredible upgrade.

---

