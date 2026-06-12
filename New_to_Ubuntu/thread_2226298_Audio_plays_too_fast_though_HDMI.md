---
title: "Audio plays too fast though HDMI"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by shoebox2 on 2014-05-26
I've resently installed ubuntu 14.04 and just getting my head round everything. When I play audio though HDMI it plays too fast and sounds really high pitch, though if I play audio though the laptop speakers or my headphones everything sounds perfect.

I have a Toshiba Satellite C55.

---

### Post by sandyd on 2014-05-26
Hi and welcome to Ubuntu!
What video card do you have? Knowing it will allow us to diagnose your issue further.

If you don't know your video card, you can run the following command in the terminal to display your video card.
```

lspci | grep -i VGA
```


Thanks!

---

### Post by shoebox2 on 2014-05-26
It says:

Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)

---

### Post by torrit2 on 2015-02-08
Hi,
I've had a similiar problem. It was linked with kernel and Intel driver (see here: [https://bugzilla.kernel.org/show_bug.cgi?id=74861](https://bugzilla.kernel.org/show_bug.cgi?id=74861)).
Passing i915.disable_power_well=0 on the kernel command line works around the problem.

Cheers.

---

