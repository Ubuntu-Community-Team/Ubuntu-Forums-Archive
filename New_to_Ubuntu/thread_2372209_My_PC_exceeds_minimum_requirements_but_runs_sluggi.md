---
title: "My PC exceeds minimum requirements but runs sluggish"
date: 2017-09-22
forum: New to Ubuntu
---

### Post by gary0318 on 2017-09-22
Hi. Here is my computer description:

INTEL XEON 5030 2.67GHZ
1GB DDR2 MEMORY ECC
320GB SATA HD 

But, When I install Ubuntu Desktop 17.04, It runs very sluggish. Any a advice on what might be wrong? Or, if I need to beef up the system?

Thanks,
Gary

---

### Post by oldos2er on 2017-09-22
More RAM would help. What video card?

---

### Post by Rex Bouwense on 2017-09-22
+1.  What we have found is although it is possible to install Ubuntu (or Kubuntu for that matter) with 1Gb of RAM, for a good user experience more RAM is generally needed.

---

### Post by Bucky Ball on 2017-09-22
Try Lubuntu. You might get a better experience, but as above. More RAM, please! Ubuntu won't enjoy 1Gb. :|

---

### Post by kansasnoob on 2017-09-22
I've recently found that even 2GB of RAM is insufficient for happy browsing. I first blamed browsers but after weeks of testing with different browsers (and even Windows) I concluded it's more likely the demands of some web pages due to more resource hungry content. So 3GB of RAM seems to be the new *true* minimum for happy browsing :(

You could try running System Monitor in the background but once things really slow down you may find it really, really hard to even navigate from one app to another (think slow as in dial-up days). Alternatively you can use the command "free -m" to display how much RAM and SWAP are in use and available:

```
lance@lance-amd:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2881       2125        755         43         89        717
-/+ buffers/cache:       1319       1561
Swap:         3812          4       3808

```

The above is from a machine with a 2.5 GHz dual-core CPU and 3GB of RAM. As you can see it's already trying to SWAP and SWAP is much, much slower to respond than actual physical RAM. 

The good news (for me at least) is that both Kingston and Crucial seem to do a pretty good job of showing the proper RAM for older hardware and I was able to find 4GB upgrades (2X2GB sticks) on Ebay for three machines ranging from $5 to $13.50 per set. Things I've learned from experience when shopping for RAM for older hardware are (1) to avoid "one-sided" RAM and (2) avoid the newer low profile (half-height) RAM.

---

### Post by Autodave on 2017-09-22
+1 w/Bucky Ball. Lubuntu is much lighter than Ubuntu. Or, Xubuntu is even lighter and not as bland as Lubuntu.  Iran an Asus EEEPC one one gig ram and Xubuntu and a much slower processor than yours is.

---

### Post by HermanAB on 2017-09-22
1GB RAM is less than most embedded systems have nowadays.

You should change your desktop system to Blackbox or IceWM.  With 1GB, you can forget about Gnome or KDE.

---

### Post by kansasnoob on 2017-09-22
Bohdi would likely run OK on that hardware to a degree:

[http://www.bodhilinux.com/w/system-requirements/](http://www.bodhilinux.com/w/system-requirements/)

> Minimum:

    500mhz processor
    256MB of RAM
    4GB of drive space

Recommended:

    1.0ghz processor
    512MB of RAM
    10GB of drive space


It is based on Ubuntu (LTS) so it wouldn't be totally foreign to you, but I still suspect you'd be frustrated with browsing efficiency.

---

### Post by Bucky Ball on 2017-09-22
> **Autodave said:**
> Lubuntu is much lighter than Ubuntu. Or, Xubuntu is even lighter and not as bland as Lubuntu.

Think it's the other way around with Lubuntu being the lightest, but yes, definitely, Xubuntu less bland and more customisable. ;)

---

### Post by Autodave on 2017-09-23
Yes....and I know that. What I meant to say and what it looks like in the post are 2 different things. Call it old age. :-)

Lubuntu is lighter than Xubuntu. Xubuntu is lighter than Ubuntu.

---

### Post by Rex Bouwense on 2017-09-23
With machines that have less than 4 GBs of RAM we have reduced the swappiness from the default 60 to 10 with some success.

---

### Post by kansasnoob on 2017-09-23
> **Rex Bouwense said:**
> With machines that have less than 4 GBs of RAM we have reduced the swappiness from the default 60 to 10 with some success.

I hadn't thought of that but it's an excellent idea.

---

### Post by poorguy on 2017-09-24
I would go with** antix Linux** it will blow Lubuntu out of the way.
Uses very few system resources and pretty much will run on anything from my experience.
Little bit of a learning curve but not that much.

Main Page
[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

Forum
[https://www.tapatalk.com/groups/antix/](https://www.tapatalk.com/groups/antix/)

**antiX-16.2 (Berta Cáceres)** 

Download
[https://sourceforge.net/projects/antix-linux/files/Final/antiX-16/](https://sourceforge.net/projects/antix-linux/files/Final/antiX-16/)

Download #8 (32bit) 
Download #9 (64bit)

---

### Post by gordintoronto on 2017-09-25
I have a netbook with 1 GB of memory. Using Mint Mate, it's fine as a small file server.

---

