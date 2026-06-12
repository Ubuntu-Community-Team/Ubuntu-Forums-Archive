---
title: "Need VGA card recommendation under $60 - PCIE"
date: 2016-11-30
forum: New to Ubuntu
---

### Post by kingneutron on 2016-11-30
--Hello, I currently have an older video card that is something of a heat-beast and not that well supported anymore in Ubuntu 14.04.

(from lspci)
```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV770 [Radeon HD 4870]

```


--I do a light amount of video watching (standard 4-8GB DVDs in Linux; youtube and Netflix inside of Vmware Workstation) and do not use this PC for games.  Dual booting with Win7, but Ubuntu is my primary operating environment.

--Looking for a PCI Express VGA card with good support in 14.04, preferably ATI/AMD, with DVI and HDMI ports, in the $50-60 range. Something that runs cooler and doesn't take up (2) slots would also be nice.  If anyone has a recommendation, I'd appreciate it. TIA

---

### Post by SeijiSensei on 2016-11-30
I always prefer NVIDIA cards for Linux; they're better supported.

Here's a [bunch in your price range](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%204026%20600007303%20600007313%20600007321&IsNodeId=1&bop=And&Order=PRICE&PageSize=60).  I have an MSI card with a GTX 750 chip so I can play games in Windows.  Has worked like a charm in both Windows and Linux.

---

### Post by oldrocker99 on 2016-11-30
+1 on the GTX750. It draws all of its power from the PCI-E slot, too.

---

### Post by mörgæs on 2016-12-02
I suggest that you leave Ubuntu and 14.04, doing a fresh install of X/Lubuntu 16.04.1.
After the install this [setting]("https://help.ubuntu.com/community/RadeonDriver#Ubuntu_12.04.5_LTS_.28Linux_kernel_3.13.0.29.2C_Ubuntu_14.04_LTS_and_later") will help against overheating.

---

### Post by Autodave on 2016-12-02
Nvidia is the way to go. And, I would go with Xubuntu to lessen the load on the memory. Unity is a bigger user of memory that Xubuntu.

---

### Post by kingneutron on 2016-12-03
--Thanks for the replies so far, but (as stated) I would prefer an ATI/AMD card and have no plans to upgrade my OS to 16.04.  I use Xubuntu/Lubuntu by preference, but  fluxbox is the WM on my main PC -- I don't run Unity.  

--I did an Amazon search on GTX750 cards and they appear to be out of my price range (~$115 was the lowest I found.)  Basically I'm fine with a card that's a few years old but still well supported in Linux. I don't need 4K, my monitor is HD 1920x1080 running off a DVI cable.

--Found this link; considering upgrading to an "Asus ATI Radeon HD6450 Silence 1 GB DDR3 VGA/DVI/HDMI Low Profile PCI-Express Video Card" since it appears to be several generations newer than my current chipset AND affordable:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


--Still looking for hints... TIA

---

### Post by SeijiSensei on 2016-12-04
You're welcome to your preference, but I still believe that NVIDIA cards are better supported and will continue to be so in the years ahead.  While I mentioned that I have a GTX750-based card, all the ones I linked to in my post were in your price range.  Here they are again: [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%204026%20600007303%20600007313%20600007321&IsNodeId=1&bop=And&Order=PRICE&PageSize=60](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%204026%20600007303%20600007313%20600007321&IsNodeId=1&bop=And&Order=PRICE&PageSize=60)

---

### Post by jim Kane on 2016-12-04
you would be much better of with NVIDIA, i use a 8400GS very cheap and works ok without even installing the restricted drivers

---

### Post by Yellow Pasque on 2016-12-05
The 6450 should work fine for your use.
Other newer candidates are: 7730/7750, R7 240, R7 350
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814202237](http://www.newegg.com/Product/Product.aspx?Item=N82E16814202237)

---

### Post by kingneutron on 2016-12-05
[**[COLOR=#000000]@Temüjin[/COLOR]**]("https://ubuntuforums.org/member.php?u=327594") - that is an *excellent* suggestion and I came within an ace of ordering it, but decided to go with the 6450 instead because of price (and the R7 350 doesn't appear to be listed on the driver link that I posted earlier.)  Much thanks!!

---

