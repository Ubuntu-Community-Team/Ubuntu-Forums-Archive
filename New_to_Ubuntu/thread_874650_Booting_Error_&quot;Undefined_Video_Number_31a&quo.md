---
title: "Booting Error: &quot;Undefined Video Number 31a&quot;"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Limitlesschannels on 2008-07-30
Hi Everyone,

Upon booting my hardy installation I have recently started getting this error.  It tells me to press enter to choose the following options for VGA-xxx (where x is some number) from a list to boot correctly(?) into my system.  The other option is to press space to "continue" or "wait 30 seconds" in which is continues anyway.
   I can either press space to continue which is successful, or wait, but either way it is a hassle and error that I would really prefer to solve.  I found [this mention]("http://support.zenwalk.org/viewtopic.php?f=46&t=17413") of the error in the zenwalk forums but there is no explanation at all and I am not sure if that will even work for my system, any ideas?

---

### Post by plucky on 2008-07-30
> **Limitlesschannels said:**
> Hi Everyone,

Upon booting my hardy installation I have recently started getting this error.  It tells me to press enter to choose the following options for VGA-xxx (where x is some number) from a list to boot correctly(?) into my system.  The other option is to press space to "continue" or "wait 30 seconds" in which is continues anyway.
   I can either press space to continue which is successful, or wait, but either way it is a hassle and error that I would really prefer to solve.  I found [this mention]("http://support.zenwalk.org/viewtopic.php?f=46&t=17413") of the error in the zenwalk forums but there is no explanation at all and I am not sure if that will even work for my system, any ideas?

I had this problem on a Pentium 3 with an Intel i810 VGA onboard the motherboard.This was caused by putting the value **vga=791** in the kernel line in menu.lst to try and get the splash screen to display in 1024X768 mode.

Have you set up your menu.lst with a vga number?

If so, remove it or try to get the correct number.

This table might help,but for me removing the **vga=791** worked.

```
 
Screen  640x480  800x600 1024x768 1280x1024 1600x1200
Colors 					
256      769 	   771      773      775 	796
32,768 	 784 	   787 	    790      793 	797
65,536 	 785 	   788 	    791      794 	798
16.8M 	 786 	   789      792      795 	799

```

Good Luck

---

