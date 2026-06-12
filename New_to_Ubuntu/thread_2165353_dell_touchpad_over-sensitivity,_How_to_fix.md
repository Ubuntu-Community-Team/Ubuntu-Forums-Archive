---
title: "dell touchpad over-sensitivity, How to fix?"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by eshant_engineer on 2013-08-04
1) I have Dell Inspiron laptop with alps touchpad which is highly over-sensitive i.e. without touching pad, I can drag the cursor. Whenever I do double-tap, it moves to some other place and sometimes weird, unwanted action accidentally happens. 

2) Moreover, when I land two finger together, cursor jumps sometimes. I reproduced it in this way- let suppose two fingers are 1 and 2 when I place them at two places on touchpad and now tap 2-2 now when I lift up 1, the cursor jumps. 

For 1, Somewhere, I found about synclient FingerLow and FingerHigh, but don't know how to give them correct value and how to set them on every bootup. Hope anybody would have solution.

Thank You

---

### Post by fantab on 2013-08-05
Perhaps you need to reconfigure the Synaptics Driver. The following Wiki from another distro should help you.
[https://wiki.archlinux.org/index.php/Synaptics](https://wiki.archlinux.org/index.php/Synaptics)

---

