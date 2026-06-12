---
title: "Minimum requirements for Ubuntu 11.04"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Autodave on 2012-04-21
I have been looking and keep finding the same thing about minimum requirements got  11.04.  However, I still don't understand.  I have a little cheapy ASUS netbook, 9', with one gig ran, 700Mhz processor.  11.10 runs *great *on it.  Then, I have a Pentium 4  2.8 Mhz  running 32 bit with 4 gig ram and an ATI 128M video card that will not run 11.04.  With 3 of my other machines' Ubuntu no longer being supported, I would like to move up to 12.04 next week, but really have concerns.

Does anybody know minimum specs?

---

### Post by oboedad55 on 2012-04-21
> **Autodave said:**
> I have been looking and keep finding the same thing about minimum requirements got  11.04.  However, I still don't understand.  I have a little cheapy ASUS netbook, 9', with one gig ran, 700Mhz processor.  11.10 runs *great *on it.  Then, I have a Pentium 4  2.8 Mhz  running 32 bit with 4 gig ram and an ATI 128M video card that will not run 11.04.  With 3 of my other machines' Ubuntu no longer being supported, I would like to move up to 12.04 next week, but really have concerns.

Does anybody know minimum specs?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Autodave on 2012-04-21
> **oboedad55 said:**
> [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)


I have seen that page and many quite like it.  But, my ASUS should NOT work according to that, and my Pentium 4 should have no problem at all.  But, the opposite is true.  And, I am trying to figure out why.

---

### Post by mastablasta on 2012-04-21
> **Autodave said:**
> I have seen that page and many quite like it.  But, my ASUS should NOT work according to that, and my Pentium 4 should have no problem at all.  But, the opposite is true.  And, I am trying to figure out why.

because the graphics card on Pentium mashcine has poor linux 3D support. porbably by reverse engineered opensource driver. while asus's card has a propper driver.

you could try with edgers PPA to solve driver issues. not sure if it will work.

also 700 Mhz? are you sure?

in any case Mhz and Ghz don't mean much these days. Raspbery Pi has i think 800 Mhz or something Arm and runs Debian LXDE smoothly.

---

