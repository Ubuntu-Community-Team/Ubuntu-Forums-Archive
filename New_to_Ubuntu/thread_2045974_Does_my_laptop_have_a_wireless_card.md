---
title: "Does my laptop have a wireless card?"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by chadwell on 2012-08-22
Funny question you say.  But I received this old HP Compaq 6715B laptop with no hard drive.

I have booted Ubuntu from USB - but I'm not sure how to check if there is a wireless card or not?  

I used:lspci in terminal.

It brought up loads of stuff, including an ethernet controller.  But no mention of wireless or 801g or anything like that.

Anyway to know for sure (either software or hardware based?)

---

### Post by miegiel on 2012-08-22
> **chadwell said:**
> Funny question you say.  But I received this old HP Compaq 6715B laptop with no hard drive.

I have booted Ubuntu from USB - but I'm not sure how to check if there is a wireless card or not?  

I used:lspci in terminal.

It brought up loads of stuff, including an ethernet controller.  But no mention of wireless or 801g or anything like that.

Anyway to know for sure (either software or hardware based?)

Some old (cheap consumer type) laptops don't have wifi. However *lspci* might not show the wifi because it's disabled. Check the keyboard for any function keys to turn it on (usually a transmitting tower or dish icon). If your laptop doesn't have one, you probably don't have wifi. Alternatively you can grab a screwdriver and take a look inside. But be gentile and patient, laptops don't like to be opened up.

There are also manuals of the manufacturer that you probably can still download. But often these cover multiple models, some with hardware that others lack.

---

### Post by chadwell on 2012-08-22
I think it should have wifi - the manual states it should have.  There is a wifi button above the keyboard, below the screen.

Everytime I pressed it nothing would happen.  But in Linux, I right-clicked on the Bluetooth icon, and chose enable.  Then the light came on above the keyboard.  This shouldn't be a bluetooth icon - its definatley the wireless icon according to the manual.  But pressing it now turns the bluetooth on and off!

Se manual here:

[https://docs.google.com/viewer?a=v&q=cache:T6Zne4gxkc4J:arc.parsons.edu/wordpress/wp-content/uploads/2011/08/pc.pdf+&hl=en&gl=uk&pid=bl&srcid=ADGEESj8OIrYyetRCkK1LU3JPutfTnNlNZRihXj2dgzDTkaaRF-Knfsg8abp43J9ImHVT_i0aE7Y4aUHqK_s2BKIC0Z_d7ZopgnvEKkPGD1b6vGVLUZThmLHN4Rp-ka_4BGhmNLSg4Op&sig=AHIEtbSWp7sWmzs0lQs8ZRL1H3ZQmt5wNQ](https://docs.google.com/viewer?a=v&q=cache:T6Zne4gxkc4J:arc.parsons.edu/wordpress/wp-content/uploads/2011/08/pc.pdf+&hl=en&gl=uk&pid=bl&srcid=ADGEESj8OIrYyetRCkK1LU3JPutfTnNlNZRihXj2dgzDTkaaRF-Knfsg8abp43J9ImHVT_i0aE7Y4aUHqK_s2BKIC0Z_d7ZopgnvEKkPGD1b6vGVLUZThmLHN4Rp-ka_4BGhmNLSg4Op&sig=AHIEtbSWp7sWmzs0lQs8ZRL1H3ZQmt5wNQ)

---

### Post by howefield on 2012-08-22
Would appear it has..

[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3368540&exit=product_series_oid&jumpid=reg_r1002_usen_s-001_title_r0001&lang=en&cc=us](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3368540&exit=product_series_oid&jumpid=reg_r1002_usen_s-001_title_r0001&lang=en&cc=us)

---

### Post by LiamOS on 2012-08-22
Any chance you can post lspci and lsusb?

---

### Post by Paqman on 2012-08-22
> **LiamOS said:**
> lsusb

This. Sometimes even internal devices are connected via USB instead of PCI.

---

### Post by chadwell on 2012-08-22
It is appearing now, I reinstalled Ubuntu on my USB stick and it appears now in lspci.  (Broadcom Corp BCM4311).

I installed the Additional Drivers (Broadcom STA wireless driver),  I am rebooting now!

---

