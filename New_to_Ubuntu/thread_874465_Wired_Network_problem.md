---
title: "Wired Network problem"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by DocWu on 2008-07-30
I'm having a problem with my wired network connection working sometimes and then not working at others. 

I searched and finally found a **thread** ([**Re: Realtek RTL8102EL LAN / RTL8101E / r8169 - no network access**]("http://ubuntuforums.org/showthread.php?t=843398")) that describes the exact problem and a solution, but it's a bit beyond my understanding to do at this point. 

I am using the Intel D945GCLF motherboard with the RealTek R8101 onboard NIC. The code snippets of the results from **sudo lshw -C network** are exactly what is happening for me.

I have downloaded the new driver files from Intel, but the rest of the solution is a bit scary to me at this point. For one thing, the instructions are talking about Hardy, whereas I am using 7.04. There is another patch they talk about 'applying' but I don't know how to do that. It looks like C code to me.

Could anyone read the above post and translate/expand upon it so a newbie can follow it? I'm getting tired of rebooting until it works :rolleyes:

Thanks!

(BTW, the NIC works 100% of the time in Windows, so I'm pretty sure it's not a hardware failure.)

---

### Post by DocWu on 2008-07-31
Bump...

The part I need help with is in the #11 post of the thread... I should have been clearer. 

>  Re: Realtek RTL8102EL LAN / RTL8101E / r8169 - no network access
1. Download r8101 driver from Realtek official site - [http://www.realtek.com.tw/downloads/...&GetDown=false](http://www.realtek.com.tw/downloads/...&GetDown=false)
2. Apply hardy patch - [http://www.alessiotreglia.com/wp-con...hardy.diff.txt](http://www.alessiotreglia.com/wp-con...hardy.diff.txt)
3. Read README and do as it says.
4. Deactivate r8169 driver:

Code:

```
mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko.old
depmod -a
```

5. Rebuild initrd.img

Code:

```
mv /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.old mkinitramfs -o /boot/initrd.img-`uname -r`
```

6. Reboot

---

### Post by DocWu on 2008-07-31
> **DocWu said:**
> There is another patch they talk about 'applying' but I don't know how to do that. It looks like C code to me.

I found [**part of the answer to my question**]("http://en.wikipedia.org/wiki/Patch_(Unix)"):

> Updating files with *patch* is often referred to as *applying the patch* or simply *patching* the files

Anyone able to help with that?

---

### Post by DocWu on 2008-07-31
Okay, before I could even play around with patching the driver with the *.diff* file, the above thread had another post. 

Intel has come out with a new BIOS version that might fix the problem.

I've updated the BIOS (Again. I've had the board a week and it's the second BIOS update. That's a new record! I've had boards for years without ever updating the BIOS.) 

I'll see if the problem is fixed now. If not, back to the patch stuff.

---

### Post by DocWu on 2008-08-01
A bump and update.

The BIOS update didn't fix the NIC. It failed to be recognized almost the first time I rebooted. 

I was going to try to make the driver patch from the referenced thread, but when I looked for the page with it again, it had been taken down. Then I discovered the RealTek site ahd a newer driver, so I downloaded it and attempted to follow the instructions in it to install the r8101 driver and remove the r8169 one. 

Whatever I did worked at first. The r8101 driver was being used and it was working, but as soon as I tried a reboot, it didn't come up again. Whatever I did didn't stick. 

I finally replaced the r8169 driver file and things are at least working as they were. I don't know if it will work every time or if I'll have to keep nursing it. I can't say I've made much progress, but I'm going to leave it as is for now.

---

