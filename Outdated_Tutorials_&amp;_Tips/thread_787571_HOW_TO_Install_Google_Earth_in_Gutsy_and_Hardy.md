---
title: "HOW TO: Install Google Earth in Gutsy and Hardy"
date: 2008-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by NightwishFan on 2008-05-09
**GOOGLE EARTH HOW TO:** <('.'<)(>'.')>
_This involves using the Medibuntu repository._
Also works for both 32bit and 64-bit.

You will have to accept the Google Earth EULA.


**For Hardy:**

**Google Earth 4.3 (latest)**
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install googleearth-4.3
```
**Google Earth 4.2**
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install googleearth
```

**For Gutsy:**

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install googleearth
```


Please ask if you have any questions or additions to this how to. May the force be with you.

---

### Post by donaldshelton on 2008-10-10
I copied and pasted the code for 4.3.

After about 5 minutes of lots of gobbledy gook in the terminal window, I believe the program was downloaded and installed.

But how do I access the program?  Should there be an icon on the desktop?

---

### Post by kamitsukai on 2008-10-11
> **donaldshelton said:**
> I copied and pasted the code for 4.3.

After about 5 minutes of lots of gobbledy gook in the terminal window, I believe the program was downloaded and installed.

But how do I access the program?  Should there be an icon on the desktop?

It should be located in Applications-->Internet-->Google Earth if not try the command 

```
googleearth %f
```

in the terminal:KS

---

### Post by donaldshelton on 2008-10-13
It works, but the places on the globe are very distorted.  the screen is fuzzy and looks a bit like the old test screens we used to have on the tv.

any advice?

---

### Post by treesurf on 2008-10-13
Google Earth runs extremely slowly on Ubuntu, but flys along just fine in Windows.  I have an Intel Graphics Accelerator card, which I previously thought was running just fine in Ubuntu, but obviously there is some problem.  Any ideas what I need to do to get Google Earth running at a reasonable speed?

---

