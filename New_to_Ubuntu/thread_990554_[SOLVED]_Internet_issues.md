---
title: "[SOLVED] Internet issues"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by otamotacon on 2008-11-22
My friends computer crashed a few weeks age. So I did the neighborly thing and formatted it with Ubuntu. everything went smoothly except for getting his internet to work. Its a gateway and connects wireless to a router.

I think the problem is his wireless card, it is a Broadcom 43xx wireless card. 

He seem to be pretty enthusiastic about switching to Linux so i would really like to get it to work for him. 

any advice is greatly appreciated.

---

### Post by stalkingwolf on 2008-11-23
What version of Ubuntu did you use?  I just installed 8.04 on an everex
with a broadcom 43xx wireless card and it worked fine. A first I will admit.

Also , I had to do the install and updates with the HDD installed on my desktop, a problem with the DVDrom.  FWIW I also used the live DVD.

---

### Post by otamotacon on 2008-11-24
I used 7.10 because I was what I happend to have around, but I guess now I'm going to reformat with the latest version and see if that works.

---

### Post by otamotacon on 2008-11-25
I didn't reformat, i downloaded the Debian packages and did the installation off-line. works perfectly and i successfully converted another one.

---

### Post by otamotacon on 2008-11-26
He upgraded to 8.04 and it stopped working.

I think that he needs b43-fwcutter with 8.04 instead of b43xx. not real sure.

---

### Post by andrew.46 on 2008-11-27
Hi,

I can only really speak for Intrepid Ibex and Broadcom. Which broadcom do you have? Mine is reported as follows:

```
andrew@skamandros:~$ lspci | grep -i broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
```

Andrew

---

### Post by otamotacon on 2008-12-01
It wouldn't work under 8.04 or 8.10
I had to reformat and put 7.10 back on it, then install bcm43xx ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)) off line

I tried getting the Debian packages for 8.10 here: [http://packages.debian.org/etch/b43-fwcutter](http://packages.debian.org/etch/b43-fwcutter) 
but i couldn't get them to properly install or they just weren't doing for the driver.

I just thought it was weird that it would work under version 7 but not 8.
I formatted his brothers computer also and his wired connection hooked up on installation without a problem. Either way, problem solved.

---

