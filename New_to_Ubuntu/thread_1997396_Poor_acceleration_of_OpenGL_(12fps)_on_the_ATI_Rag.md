---
title: "Poor acceleration of OpenGL (12fps) on the ATI Rage 128 - 8MB."
date: 2012-06-05
forum: New to Ubuntu
---

### Post by m75 on 2012-06-05
Hi.
 It has a Dell Latitude C600 laptop with a Pentium III 750 (800) chipset Bx / Zx, 256MB RAM and ATI Rage 128 with 8MB on board.
 The problems began when I wanted to upgrade to Lubuntu 12.04.
 OpenGL acceleration runs very slowly (about 12FPS on glxgears) and can not even play in the chromium-BSU :-(.
 All previously worked as it should.
 Edited xorg.conf in many ways but it did not bring the expected results, it was even worse.
 OpenGL acceleration runs a few frames faster than without the xorg.conf file from my old xorg.conf file.
 In the earlier distribution Lubuntu glxgears worked at least 400 - 700 FPS.
 Speedstep not working well (no such module) and the lack of hibernation.
 Can you recommend something for the above-mentioned ills?
 You may need to manually compile the egg?
 Can you hint how to compile on a faster host egg?
 Best regards.

---

### Post by gordintoronto on 2012-06-05
I'm astonished that you can do anything useful with a 12-year-old laptop.

---

### Post by onewheeltom on 2012-06-19
I'm astonished that you are astonished. So there!

I'm having the same problem with Lubuntu 12.04 after a recent update. I'm seeing this on two different systems. One of them is a Dell Inspiron 1100 (look it up...its a 9 year old laptop) and a Dell Latitude D420 (a 3 year old laptop), so I don't think this problem is specific to a computer.

Also, the slowness began after the last update (I believe Monday). Both systems were fine until then,

--tom

> **gordintoronto said:**
> I'm astonished that you can do anything useful with a 12-year-old laptop.

---

### Post by anewguy on 2012-06-19
However, the rage 128 is an extremely old and badly, if at all, supported any more.  It never was a "good" GPU, as it was normally meant for lower-end systems.  I had a Rage 128 YEARS ago, and it didn't perform the best with Linux then.  I don't know what support there is in the available Linux drivers - I believe ATI/AMD discontinued the drivers that support that GPU as well, so if there may be some support in the old drivers in Linux.  It's possible that in your previous versions of Linux you were still using a driver supported by ATI/AMD.  I believe now it would probably just be the open-source driver that might support it.

I could be wrong - it sure wouldn't be the first time, but I think that is the OP's problem.

onewheeltom:  I've had 12.04 running on some old laptops ok, on others not.  More importantly to this thread would be whether your GPU's are the ATI Rage 128 or not.

Dave ;)

---

### Post by HiImTye on 2012-06-19
youll need to manually compile your drivers for your RAGE card as it hasnt been officially supported for years

---

### Post by anewguy on 2012-06-20
I suspected as much, but didn't know if the open-source replacement for the old ATI drivers included it or not.

Dave ;)

---

### Post by fr05t on 2012-08-06
i'm glad i'm not the only one, mint linux worked fine, changed to lubuntu and open gl is not working; i have the same drivers installed as before no luck

---

