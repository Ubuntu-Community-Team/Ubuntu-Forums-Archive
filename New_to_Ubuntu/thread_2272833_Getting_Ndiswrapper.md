---
title: "Getting Ndiswrapper"
date: 2015-04-08
forum: New to Ubuntu
---

### Post by ScoJoMo on 2015-04-08
Hello all, 
Total noob here.  So, I installed Ubuntu on to a system with 2 HDDs the other day, and I'm going absolutely INSANE trying to get this program that everyone keeps mentioning, called Ndiswrapper.  Here's my problem: I have to download this thing somewhere, I'm assuming.  I have to download it from another computer, then transfer it to a USB drive, then try to install it on Ubuntu.  Now, my questions are....
1. Where is the best place to get the program from?
2. After I download said program, how on Earth do I install it from my USB drive onto Ubuntu?
I've seen about 50 different methods that people have posted out there with all this code that I have no idea what it means, but I try to type it into my terminal, and nothing works.  This has been absolute INSANITY the past few days!  Do I need to just start from scratch and read what all this meaningless code means?
Now, if I actually AM successful in installing Ndiswrapper.... The next fun little project will be getting my Netgear WDNA 3100v2 USB wireless adapter to work.

Thanks for reading, and I hope that SOMEONE out there can just give step by step instructions.

---

### Post by wildmanne39 on 2015-04-09
Here are directions for installing ndiswrapper without an internet connection.
[http://askubuntu.com/questions/606948/netgear-wnda3100v2-802-11-not-instaling](http://askubuntu.com/questions/606948/netgear-wnda3100v2-802-11-not-instaling)

---

### Post by ScoJoMo on 2015-04-09
Thank you for the reply Wild Man!  I will try this when I get home tonight!

---

### Post by kurt18947 on 2015-04-09
> **ScoJoMo said:**
> Hello all, 
...............................................................
The next fun little project will be getting my Netgear WDNA 3100v2 USB wireless adapter to work.

Thanks for reading, and I hope that SOMEONE out there can just give step by step instructions.

As you may be aware, Netgear's WDNA 3100 v2 is notorious in linux land. Here is how I would approach this:


1) Get thee to an office supply, electronics emporium or other preferred shopping destination and buy something like this:

[http://www.netgear.com/home/products/networking/wifi-adapters/WNA1100.aspx](http://www.netgear.com/home/products/networking/wifi-adapters/WNA1100.aspx) (uses an Atheros 9271 chipset. Note: speed is limited to 150 mb./sec)

[http://www.trendnet.com/products/proddetail.asp?prod=200_TEW-649UB](http://www.trendnet.com/products/proddetail.asp?prod=200_TEW-649UB)  v1.0r (uses a Realtek 8192**su** chipset)

or other adapter that uses the same chipset.


2) Alternatively purchase an adapter that uses a Realtek 8192**cu** chipset. They're pretty common on Ebay as well as at retail bearing various manufacturer's names. This will work out-of-the-box but not well in my experience. Then go to this site using an account with SUDO privileges e.g. your original account:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I open a terminal and just copy/paste each line, one at a time. If possible use an ethernet cable rather than wifi. I've done this on a few machines using ubuntu versions through 15.04 and it has worked as expected. I mention these devices as I have them and they work. There may be other better choices but I have no experience with them. Searching this forum should return other options known to work.

I must issue a disclaimer. Some manufacturers- D link seems a frequent offender - will change chipset without changing model designations, instead appending a version designator. X adapter ver. 1.0 will use a plug 'n' play chipset, X adapter ver. 2.0 is not recognized. It's usually not possible to determine the version without opening the packaging so buying where you can easily return unpleasant surprises has its benefit.

How to determine which chip set is used in a particular device? Googling something like "netgear wna1100 chipset" should return helpful links. Usually a site called 'wikidevi.com' is at the top of the list. 

3) Use the Netgear WNDA 3100 v2 with Windows only. 

I'm not sure the status of Ndiswrapper - if it is being actively maintained or not.  The last I knew it only worked somewhat reliably with Windows XP drivers, not Windows 7 or 8 drivers. I don't know that new hardware is going to come with Windows XP support. Another issue is that if the linux OS in question is 64 bit, you must use Windows XP 64 bit drivers. Those may be difficult to find. The path of least resistance seems to be to buy devices that are supported natively. I follow the same path when buying printers, scanners and the like. It makes life easier for me and rewards  companies that support Linux O.S.s

Of course if you want the experience and knowledge that comes from attempting to get a WNDA3100 v2 working, disregard the above. Have fun either way.

---

### Post by ScoJoMo on 2015-04-10
OK, so I started up my system last night and my wi-fi magically started working.  I'm thinking that is using the PCI card that I have in there that i haven't used in a long time.  How?  I have no idea.  Thank you all for the info though!  Now I have to backup a little and learn how this whole thing works....  Which won't be easy, I know.  Thanks again!

---

### Post by Bucky Ball on 2015-04-10
If the wifi is 'automagically' working with the internal card rather than the 3100, all good and I'd stick with it! As mentioned, the 3100 is tricky in Ubuntu, requires the largely superceded ndiswrapper (which can be problematic in itself), and is best avoided. 

Glad it sorted itself and good luck. ;)

PS: If you want to see what you're using, open a terminal and:

```
sudo lshw -C network
```

Look under 'Network Controller' and that will give the card in action and at the bottom the driver being used. One of these days the 3100 will also work 'out of the box' with any luck.

---

### Post by kurt18947 on 2015-04-10
I'm glad you're set. One of the truisms of hardware and linux is that newer is not necessarily better. I am somewhat surprised that WNDA3100 v.2 is not yet supported, it's been around for quite some time. If you run what Bucky Ball suggests you'll find out how your PCI card is seen and what module(s) drive it. Linux comes with far more 'built-in' drivers than Windows. Good thing too because as you've seen some manufacturers won't lift a finger to support other than Windows and maybe Apple.

---

