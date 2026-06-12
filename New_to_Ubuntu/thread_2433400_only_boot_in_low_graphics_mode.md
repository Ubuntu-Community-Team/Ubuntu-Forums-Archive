---
title: "only boot in low graphics mode"
date: 2019-12-18
forum: New to Ubuntu
---

### Post by flyinghigh2 on 2019-12-18
Hi i,m a noob running 16.04 for the last few years, i recently did an update and upgrade manually from the command line

now it will only boot in low graphics mode with no internet

any advice?

is on a dell inspiron laptop m5030

i also "took out" the onboard mouse key and audio line-out (below it) with a falling cd case recently, not sure if that had any detrimental effect on the OS

---

### Post by Autodave on 2019-12-18
Possible, but not likely.  Try this: download 18.04 to a thumb drive or DVD disc and boot from that and see what the graphics are like.  Upgrading from one release to another often causes problems like this.

---

### Post by cpt-ankitsharma on 2019-12-20
Most probably your display driver is not compatible with the new OS. 

Copy and paste this command and post the results here:

> lspci -v | grep -A5 "VGA"

---

