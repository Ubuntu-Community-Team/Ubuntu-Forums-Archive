---
title: "ATI 5770 fan speed is high all the time"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by Andariel on 2012-06-13
I am new to Ubuntu (and Linux in general) and thoroughly enjoying it. One little problem that I have is that the fan speed of my graphics card is automatically set to very high and I can't find a way to change it. This is not a problem on windows as I use amd catalyst to set the fan speed to automatic. I installed the amd proprietary drivers but don't really know if they can be used in some way to maintain the fan speed manually. Any help would be appreciated? =)

---

### Post by linuxsam777 on 2012-06-13
Your are using a desktop PC right? Presumiong you are why dont you try and enter your BIOS and usually it will give you options on how to change the fan speed. If you don't know how to enter your BIOS usually you can pressing escape as soon as you turn on your computer.

---

### Post by buzzingrobot on 2012-06-13
The delete key is often the BIOS access key, as well.

Your BIOS likely has some option about fan speed.  Whether your AMD driver  takes advantage of it is another matter. I had the same problem when I used an AMD card.  There are scripts around to alter fan speed, but I've never tried them.

Also, sometimes a newer kernel can make a difference.  If you haven't updated, that might be worth trying.

---

### Post by ratcheer on 2012-06-13
What driver are you using, @Andariel?

I have a HD6770 which is, I understand, the same card. Running the open source radeon driver, it ran at 64-68C and the fan ran over 50% of max, all the time. After I switched to the proprietary Catalyst driver (fglrx), it runs at 42-50C and the fan runs at 35-50% max. Right now, for example, it is at 42C and the fan is running at 41%.

Tim

---

### Post by QIII on 2012-06-13
How did you install the driver?  Are you sure it is working?

---

