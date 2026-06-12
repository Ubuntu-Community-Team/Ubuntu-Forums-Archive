---
title: "Ubuntu/Vista Dual-boot...Will I have wireless Internet problems?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Aaron Forni on 2008-06-20
Hey everyone,

I have been shopping for a laptop and have recently decided on purchasing this one:

[http://www.bestbuy.com/site/olspage.jsp?skuId=8782089&productCategoryId=abcat0502003&type=product&tab=1&id=1204924952362#productdetail](http://www.bestbuy.com/site/olspage.jsp?skuId=8782089&productCategoryId=abcat0502003&type=product&tab=1&id=1204924952362#productdetail)

As much as I would love to just get rid of Vista, I think I should keep it as I am paying for it and may need it sometimes (rarely).  I would like to create a partition for Ubuntu and reduce the size of the Windows one.  I would use Ubuntu for probably 90% of my computing.

My question:

Will this set-up affect the wireless Internet capabilities of my computer when I am in Ubuntu?  I have heard that the Vista drivers can create problems for wireless in Ubuntu.

Any responses and/or suggestions for optimizing this sort of set-up would be much appreciated.  Thanks!!!   

Aaron

---

### Post by p_quarles on 2008-06-20
When one operating system is loaded, the other one won't affect it in any way shape or form (except for taking up disk space). That won't be a problem.

What is a question, though, is how much work it will take to get that wireless to work with Linux. The advertisement doesn't specify a manufacturer. It's probably a good bet that it's a Broadcom, which (from what I hear) can be a bit of a pain to get working with Linux. 

If you know you want to use Linux on the laptop, I'd suggest getting something you know will work, which means something with an Intel wireless card.

---

### Post by sdennie on 2008-06-20
It's hard to say because I couldn't find any page that actually specifies what type of wifi card is in the machine.  It may work with some work or it may not work at all.  If you want really painless wireless, I would recommend getting an intel machine with intel 3945 or 4965 wireless.

---

### Post by cod3rbro on 2008-06-20
It will be fine if you install the right driver for that wireless,
When one operating system is off, it will not affect other that on one drive.

---

### Post by mivo on 2008-06-20
> **Aaron Forni said:**
> As much as I would love to just get rid of Vista, I think I should keep it as I am paying for it and may need it sometimes (rarely).

Well, you already paid for it, so if you don't have use for it, just reclaim the space it occupies. When I bought a new computer, I considered whether I feel I might ever need a Vista license, and after concluding that it is unlikely, I went with an OS-less machine and just put Ubuntu on it. Makes no difference to you right now, but for the next time you buy a computer it may be a way to save some money. :)

---

### Post by ScaredNoob on 2008-06-20
If it is a broadcom wireless chip, you could be in for spending some time to get wireless at 54 mbs (my top with a bcm4306 stays at 1 mbs, but it does work).  If you are feeling saucy, try blacklisting your (probable) broadcom card from letting the kernel use it; and then install ndiswrapper, using manufacturer supplied drivers (keep in mind version 1.0 might be best).  Or, you could fork over to ebay another 30 bucks and buy an Atheros (or other linux friendly) mini-pci wireless card, with your fingers crossed that the blasted (inevitable) broadcom card isn't soldered in the slot.  Later craigslist out your broadcom to some poor Dell user that, 5 years ago, didn't check a simple box for a 10 dollar "internal wireless" card and has been duped into snapping 50 dollar "expresscard's" twice a year and is fed up.  You could recoup about 15 bucks for the sale.  Keep in mind, tho, that the default mac address associated with your minipci wireless card is probably on file somewhere linked to the credit/debit card you will probably use at BestBuy.  Make haste.

---

### Post by cariboo on 2008-06-20
Actually ndiswrapper is a really easy way to get ypur wifi card to work, it is a wrapper for the Windows driver, so no searching for a free linux driver that'll work, Just use the .inf file and your ready to go. There is a company called Linuxant that will sell you a working driverloader for most Broadcom chipsets.

Jim

---

### Post by BlackDragonBE on 2008-06-20
I you want to be sure it works out of the box, start up a LiveCD, if everything works in the Live System everything works when fully installed too.
However, if it doesn't you can still make it work, you'll just need some time to configure it.

---

### Post by mivo on 2008-06-20
Wireless frequently requires restricted drivers, so while the Live CD is a good way to test a lot of other stuff, wireless is not always one of them. Still, on my laptop I got Broadcom wireless working within minutes after deciding on a method, so it's definitely do-able. :)

---

