---
title: "Fails to boot"
date: 2011-05-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-05-24
I'm not sure if this is related to the /run/dev thing, so I'm just asking if anyone here is seeing lots of failing boots (blinking cursor in the top-left)?

4 out of 5 boots fail, using Intel HD graphics (looks like it fails to enable KMS - i get the text Ubuntu logo and big letters).

---

### Post by Harry33 on 2011-05-24
> **MacUntu said:**
> I'm not sure if this is related to the /run/dev thing, so I'm just asking if anyone here is seeing lots of failing boots (blinking cursor in the top-left)?

4 out of 5 boots fail, using Intel HD graphics (looks like it fails to enable KMS - i get the text Ubuntu logo and big letters).

Cannot say I have.
Do you use the latest grub 1.99 release (1.99-4ubuntu1)?

---

### Post by lucazade on 2011-05-24
In a virtualbox machine the issue is not present (i've only a /dev/run not writable warning from some days but doesn't brake bootup)

---

### Post by Hanmac on 2011-05-24
i dont know why but sometimes linux think that my sda is sdc (and i does not change something with the hardware)
the solving: do fsck with all unmounted partions and boot again

but that linux is confunsed with sda->sdc .. is a little bit funny

---

### Post by MacUntu on 2011-05-24
> **Harry33 said:**
> Cannot say I have.

What graphics card does your machine have? I will later test the notebook with nvidia instead of intel. If that fixes the problem, then it's gotta be a kernel thing.

Not sure which GRUB version I'm using, I updated ~15 hours ago.

**Edit:**

No issue with Nvidia (and GRUB is at -4ubuntu1).

---

### Post by cariboo on 2011-05-24
I get the error message on my Compaq netbook with the Intel 945 chipset, but the error is on screen for a couple of seconds, then the system continues on to the desktop. I'm running Oneiric on a 8GiB sd card.

---

### Post by Skelator on 2011-05-24
I'm getting /dev/run  on my VMWare machine but it's booting fine.
 
I am getting this error in classic mode though:
 
 
[IMG]http://steeky.com/error.png[/IMG]

---

### Post by MacUntu on 2011-05-24
I could pinpoint this to the latest udev version.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/787610](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/787610)

---

