---
title: "32 bit or 64 bit?"
date: 2010-07-22
forum: Recurring Discussions
---

### Post by philipballew on 2010-07-22
hi. i have recently purchased a laptop with a Intel I5 processor, 4 gigs of memory and the like and want to know if i should install the 32 bit or 64 bit version of 10.4 ubuntu? and what is the reasons to install one vs the other?

---

### Post by mayur.shetye on 2010-07-22
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by techunit on 2010-07-22
64bit is a requirement for your system! you have to much ram to waste... in 64bit you can use all of that ram but in 32bit you will only be able to use 3gbs. The Core i5 processor probably needs a 64bit environment to work properly as well, but not necessarily...

---

### Post by philinux on 2010-07-22
Moved to Recurring Discussions.
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by pricetech on 2010-07-22
64 bit.

Yes you'll have some application compatibility issues, but most stuff will work and you'll see better performance with 64 bit.

---

### Post by techunit on 2010-07-22
Bottom line is if you want to be able to use all of your ram you have to install 64bit.

---

### Post by howefield on 2010-07-22
> **techunit said:**
> Bottom line is if you want to be able to use all of your ram you have to install 64bit.

Bottom line is he can use all his RAM with 32 bit. All 4 gigs of it.

---

### Post by michaelzap on 2010-07-22
The only issues I have had running 64-bit Ubuntu for the last year or so have been:

[LIST]
[*]64-bit Flash was buggy and has recently been discontinued (although the 32-bit nonfree plugin works fine), and
[*]offline Google apps don't work in 64-bit Linux browsers
[/LIST]

That's it. Everything else works just the same as 32-bit.

---

### Post by Tak11 on 2010-07-22
In linux, there is really no reason not to use 64 bit

---

### Post by techunit on 2010-07-22
> **howefield said:**
> Bottom line is he can use all his RAM with 32 bit. All 4 gigs of it.
Unfortunately you incorrect... he will only be able to use 3.25gbs in 32bit... tested this myself

---

### Post by howefield on 2010-07-23
> **techunit said:**
> Unfortunately you incorrect... he will only be able to use 3.25gbs in 32bit... tested this myself

Allow me to help you out.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

> Ubuntu 10.04 LTS (Lucid Lynx)
Both the CD and DVD installer of Ubuntu 10.04 automatically installs the PAE enabled kernel if it detects more than 3 Gb of available memory. In the case of the liveCD, a working network connection is required, since the PAE enabled kernel packages are not present on the CD.

If you need to enable PAE manually, follow the instructions for Karmic below.

---

