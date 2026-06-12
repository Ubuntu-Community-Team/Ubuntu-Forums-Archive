---
title: "Is a USB install PC specific?"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-04
I have a Plop live cd and a USB 8 GB 11.10, works great on PC-a.

When I try to boot on another machine; PC-b, I see the Ubuntu desktop and the 5 dots working away, then it stops and a few lines of information appears.

Must I install 11.10 separately on machine b?

---

### Post by wildmanne39 on 2012-04-04
Hi, you are suppose to be able to take the usb and put in any pc and run ubuntu from it but if you installed graphic drivers instead of using the default then that would cause a problem going from pc to pc.
Thanks

---

### Post by QIII on 2012-04-04
Probably any specific third party driver would be problematic, not just graphics drivers.

Try plugging back in to PC-a, removing all third party drivers and plugging in to machine b.

---

### Post by Mark Phelps on 2012-04-05
By definition, any install is PC-specific.  Why? Because part of the installation process is scanning the hardware on THAT PC, finding the drivers, and loading them.

The more different each PC is from the original, the less likely the installed USB version will work.

Restricted drivers cause real problems in this case.  Say you install AMD restricted video drivers when the USB is connected to one PC, and the next PC has an Intel video chipset.  In all likelyhood, you won't see any video when you attempt to boot the second PC from the USB stick -- due to the video drivers.

---

### Post by Cheesemill on 2012-04-05
> **Mark Phelps said:**
> By definition, any install is PC-specific.  Why? Because part of the installation process is scanning the hardware on THAT PC, finding the drivers, and loading them.

For Windows yes, but I was under the impression that Linux probes the hardware and loads the correct modules every time you boot.

I have full installs on USB stick of Ubuntu, Arch and CrunchBang and I've never had a single problem with them booting on any of the machines (20+) that I've tried them on (obviously being able to boot from USB is a must). As long as you stay away from restricted drivers then there shouldn't be a problem.

Also if your above statement was correct then there would be no such thing as a Live CD, after all they are simply full installations stored on a CD.

---

### Post by Boyntonstu on 2012-04-05
> **Cheesemill said:**
> For Windows yes, but I was under the impression that Linux probes the hardware and loads the correct modules every time you boot.

I have full installs on USB stick of Ubuntu, Arch and CrunchBang and I've never had a single problem with them booting on any of the machines (20+) that I've tried them on (obviously being able to boot from USB is a must). As long as you stay away from restricted drivers then there shouldn't be a problem.

Also if your above statement was correct then there would be no such thing as a Live CD, after all they are simply full installations stored on a CD.
Thanks,

The live CD has PLOP in order to be able to select boot from USB.

What size flash do you use for your full install?

What occurs when the persistence size is exceeded?

---

### Post by Cheesemill on 2012-04-05
I've got a couple of 32GB sticks, one has Arch and Crunchbang, the other has Ubuntu and Backtrack.

I don't use a persistence file, these are full installations just like on a HD.

---

### Post by oklokl on 2012-04-05
usb -> Data corruption
Is contaminated

If you need to install multiple times

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215465&stc=1&d=1333630254[/IMG]
SDHC..  lock Memory(Pollution Prevention)
It is recommended ..

ex> SD Zander
ZIO-Zenith
[http://blog.naver.com/vnfmstjfxkd/70134719417](http://blog.naver.com/vnfmstjfxkd/70134719417)

---

### Post by Mark Phelps on 2012-04-06
> **Cheesemill said:**
> For Windows yes, but I was under the impression that Linux probes the hardware and loads the correct modules every time you boot.
Generally, yes.  But if you load restricted drivers as part of the initial USB setup, it will not replace them with other drivers.

> Also if your above statement was correct then there would be no such thing as a Live CD, after all they are simply full installations stored on a CD.
The LiveCD is not installed -- it starts fresh with every boot, and does hardware detection as part of that.

An installed version on a USB is not the same as a LiveUSB.

---

### Post by sudodus on 2012-04-06
I think the plop live systems are made from the iso files without selecting any proprietary drivers (at least most linux install iso files).

However, I have seen that different methods to make boot USB drives (from iso files originally designed for CD drives) work or don't work with different computers.

Furthermore, I have seen that different USB flash drives also behave differently with different computers. They may work with read/write, yet some are bootable, others are not.

Maybe there is no general method that works on every computer because booting from USB is not fully standardized.

---

### Post by fiatveritas on 2012-04-06
You're not trying to use a your Ubuntu USB on Mac, right? There's a different ISO file for the Mac version in case that's what the problem is.

---

### Post by Boyntonstu on 2012-04-06
> **fiatveritas said:**
> You're not trying to use a your Ubuntu USB on Mac, right? There's a different ISO file for the Mac version in case that's what the problem is.

No, it is a Win 7 PC or a SP2 XP.

---

### Post by Boyntonstu on 2012-04-06
> **Cheesemill said:**
> I've got a couple of 32GB sticks, one has Arch and Crunchbang, the other has Ubuntu and Backtrack.

I don't use a persistence file, these are full installations just like on a HD.


I am attempting to follow in your footsteps.

I installed 11.10 on a live CD and it boots fine.

Is an Install to a USB drive the next step?

If my flash drive works, could I clone it onto a 32 GB SD card when it arrives?

---

