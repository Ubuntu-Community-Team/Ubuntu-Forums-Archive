---
title: "external serial port modems - compatible"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by wpshooter on 2008-06-26
Which brands and models of external serial port dialup modems will work with Ubuntu/Gutsy gnome ?

Thanks.

---

### Post by phidia on 2008-06-26
I believe most external serial modems work with ubuntu and many distos. 
External serial modems are contoller type-meaning the hardware function still exsists and an OS software program isn't required to run that function.
Recently I saw, by helping someone here, that newegg had Trendnet modems for sale (approx 25USD) and they were advertising them as linux compatible. US Robotics also makes or made external controller type modems.

---

### Post by wpshooter on 2008-06-26
> **phidia said:**
> Recently I saw, by helping someone here, that newegg had Trendnet modems for sale (approx 25USD) and they were advertising them as linux compatible. US Robotics also makes or made external controller type modems.

Can you point that out to me, I really can't seem to find that ?

Thanks.

---

### Post by the.phantom on 2008-06-26
i used a "best data" 56K external modem and on the box it said linux compatible
but changed to dsl as the updates are a killer

---

### Post by phidia on 2008-06-27
> **wpshooter said:**
> Can you point that out to me, I really can't seem to find that ?

Thanks.

The Trendnet modem is [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002"). I don't think US Robotics is making an external serial modem anymore. Hope that helps.

---

### Post by wpshooter on 2008-06-27
> **phidia said:**
> The Trendnet modem is [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002"). I don't think US Robotics is making an external serial modem anymore. Hope that helps.

Thanks, but I talked to Trendnet yesterday and they said that they can NOT guarantee that their modem is compatible with Ubuntu !!!

---

### Post by wpshooter on 2008-06-27
> **the.phantom said:**
> i used a "best data" 56K external modem and on the box it said linux compatible
but changed to dsl as the updates are a killer

Phantom:

Did the best data connect consistently to the internet with Ubuntu ?

Was it a matter of basically plugging it in and then doing the dialup configuration in Ubuntu or is it like the nightmare that I have been having trying to get an internal PCI card modem to work the last several days ?

Thanks.

---

### Post by timcredible on 2008-06-27
all of them.  seriously, if it's serially-connected, 100% of modems will work.  the only issue you may run into is that some modems may not use hayes AT commands so you may have to change the commands in whatever program you're using.  you can use kermit or minicom to connect to the modem manually, in case you need to troubleshoot.  i bought a cheap serial modem a few years ago for $5US off ebay.

usb and pci modems are a different story.

---

### Post by phidia on 2008-06-27
> **wpshooter said:**
> Thanks, but I talked to Trendnet yesterday and they said that they can NOT guarantee that their modem is compatible with Ubuntu !!!
Well you probably won't find any or very few hardware manufacturers who will go on record of assuring their products will work on open source. 
They don't have anything in place to offer telephones support to linux users either.
But at that site a reviewer claimed it worked with ubuntu.

---

### Post by phidia on 2008-06-27
> **wpshooter said:**
> Phantom:

Did the best data connect consistently to the internet with Ubuntu ?

Was it a matter of basically plugging it in and then doing the dialup configuration in Ubuntu or is it like the nightmare that I have been having trying to get an internal PCI card modem to work the last several days ?

Thanks.

Some winmodems depending on the chipset involved cannot be made to work in linux, but others can-have you gone to the [linmodem site]("http://www.linmodems.org/") and downloaded the scanmodem tool to see if that internal modem is supported?

I used an internal winmodem for quite a while a few years back-once set up it was fine.

---

### Post by the.phantom on 2008-06-27
> Did the best data connect consistently to the internet with Ubuntu ?

Was it a matter of basically plugging it in and then doing the dialup configuration in Ubuntu or is it like the nightmare that I have been having trying to get an internal PCI card modem to work the last several days ?

Thanks.

just plugged it in and  used the gnome program to configure it ( been about 1 1/2 years so can't remember all the details. but it was NOT a winmodem. i was not in any confg files or anything and  was (and am still ) a lightweight on linux)

but with the size of updates now you have to ask yourself if that is the way to go ! when you see 100 meg updates a few times a week that is a lot of dialup time

---

### Post by wpshooter on 2008-06-27
> **phidia said:**
> Some winmodems depending on the chipset involved cannot be made to work in linux, but others can-have you gone to the [linmodem site]("http://www.linmodems.org/") and downloaded the scanmodem tool to see if that internal modem is supported?

I used an internal winmodem for quite a while a few years back-once set up it was fine.

Yes, I did.  I found the driver for my modem but after having installed the driver, the modem will not dialup/connect to my ISP on a CONSISTENT basis !!!

Thanks.

---

### Post by wpshooter on 2008-07-09
> **phidia said:**
> I believe most external serial modems work with ubuntu and many distos. 
External serial modems are contoller type-meaning the hardware function still exsists and an OS software program isn't required to run that function.
Recently I saw, by helping someone here, that newegg had Trendnet modems for sale (approx 25USD) and they were advertising them as linux compatible. US Robotics also makes or made external controller type modems.

O.K., I just purchased one of these, Trendnet model TFM560X and if it is compatible with Ubuntu/Hardy 8.04.1, I have not yet figured out how to get it to connect to my dialup ISP account.

Anyone have any suggestions.

Thanks.

---

