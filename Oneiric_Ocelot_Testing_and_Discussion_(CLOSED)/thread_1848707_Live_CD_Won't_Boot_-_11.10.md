---
title: "Live CD Won't Boot - 11.10"
date: 2011-09-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Baloeb on 2011-09-23
I downloaded 11.10 beta 2 to try out, and I can't get it to load.  It starts up but when I select to try the live mode the computer just restarts.  It also restarts if I select check disk for errors.  I've tried booting from a USB made with unetbootin, but it won't even load up, it just stops at the cursor.  Any ideas?  Is this because it is beta, or is there something wrong?

---

### Post by garvinrick4 on 2011-09-23
> **Baloeb said:**
> I downloaded 11.10 beta 2 to try out, and I can't get it to load.  It starts up but when I select to try the live mode the computer just restarts.  It also restarts if I select check disk for errors.  I've tried booting from a USB made with unetbootin, but it won't even load up, it just stops at the cursor.  Any ideas?  Is this because it is beta, or is there something wrong?
I can see you are not getting a lot of answers right now. It is a real tough question because
it can be you need to Burn a new disk, the download was bad, graphics drivers and hard
to determine. I have downloaded and made a USB of the DVD download and was quite nice. 
I have not tried the 9-22-11 of Live Cd version today but in previous days I have used the daily builds and it has been fine. 
I would say burn another CD and try again.
Or tap any key right when you see the icons on the bottom and then hit F6 and on the
far right select to boot in nomodeset and see if that helps. Then continue with boot, that
might do it. There is no way to give a perfect answer, you have to try a few things. Sorry.

---

### Post by rbrick49 on 2011-09-23
does it give you any options when you load it into your drive and reboot your computer and also check your bios to make sure your cd/dvd drive is first boot

---

### Post by Quackers on 2011-09-23
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by zengeos on 2011-09-23
I am having a livecd boot problem as well with 11.10B2.

I get to the main Install menu and select Live Session.  The screen then goes black and the system proceeds to load a live session but with a blank screen.

I am using an Asus K53BBR6 with an AMD A6 with HD6700g2 Hybrid graphics. I suspect it's an issue with the hybrid graphics

I have tried booting with the No ACPI option as well.  

Suggestions please?

---

### Post by ventrical on 2011-09-23
> **zengeos said:**
> I am having a livecd boot problem as well with 11.10B2.

I get to the main Install menu and select Live Session.  The screen then goes black and the system proceeds to load a live session but with a blank screen.

I am using an Asus K53BBR6 with an AMD A6 with HD6700g2 Hybrid graphics. I suspect it's an issue with the hybrid graphics

I have tried booting with the No ACPI option as well.  

Suggestions please?

  I would venture to affirm that it is the graphics.

  I had a big prob with my ATI Radeon. I used the code:

sudo apt-get install  fglrx  

but that fixed it. I got the unity back.

Do that command from the terminal. You can get terminal by (ctrl+alt+F1)

If no install from CD boot them check BIOS and see if you are using the on-board graphics adapter. If you are you will have to set that to -onboard- . If you are using another card like a nvidia then choose auto.

Hope it works for you.

---

### Post by Quackers on 2011-09-23
Or possibly try the nomodeset boot option

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ventrical on 2011-09-23
> **Quackers said:**
> Or possibly try the nomodeset boot option

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thanks for that link Quackers! I think that should be required reading.!! There's a well of info.

---

