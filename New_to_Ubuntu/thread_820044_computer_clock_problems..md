---
title: "computer clock problems."
date: 2008-06-05
forum: New to Ubuntu
---

### Post by daberger on 2008-06-05
hey guys, my clock on the old laptop wont reset to the right time, currently it is an hour ahead. everytime i change it, it will remain consistent for that session and then go back to the hour ahead nxt time i log in. i know that this problem is consistent in xubuntu ubuntu and xp so i am guessing that it is a hardware problem. perhaps the motherboards button battery is dead?

---

### Post by iaculallad on 2008-06-05
Does it display "cmos date and time is not set" on boot time?

---

### Post by daberger on 2008-06-06
no. well at least i dont think so

---

### Post by bobpur on 2008-06-06
They aren't expensive. Maybe you could replace it just so you could rule that out. If your computer has much age on it you might want to consider it.
I've junked computers with the original CMOS Battery in them and, one Compaq that went through three of them in five years.
Just my $.02 (2 Cents)

---

### Post by iaculallad on 2008-06-06
Let's try another solution:

Open up your terminal and edit the /etc/default/rcS file.

```
sudo gedit /etc/default/rcS
```

Find the line which reads **UTC=yes** and change it to **UTC=no**

Then change you're laptop's system time to your correct time and do a reboot.

---

### Post by alexandremrj on 2008-06-06
I had that problem a awhile ago.

The server I was using didn't have the correct time. 

Go to "adjust date and time", unlock it and see if you are in the correct timezone. If you are, try selecting a different web server to sinc the clock.

---

### Post by daberger on 2008-06-08
> **iaculallad said:**
> Let's try another solution:

Open up your terminal and edit the /etc/default/rcS file.

```
sudo gedit /etc/default/rcS
```

Find the line which reads **UTC=yes** and change it to **UTC=no**

Then change you're laptop's system time to your correct time and do a reboot.

my rcs is blank

---

### Post by markdavidoff on 2008-06-11
I was having this problem too. I thought it was just my system clock, but after replacing the battery i realized it was ubuntu.

Thanks :)

**to daberger:**
as for the blank rcS file, make sure you are editing the correct file.

ubuntu is case-sensitive

rcS is not equal to RcS or RSC or RCs .... etc

---

### Post by daberger on 2008-06-12
well it cant be ubuntu for me bcuz windows has it to. and xubuntu.

thank you but i believe i got the right file
ill check again just for u

---

### Post by alexandremrj on 2008-06-12
If you have problems in xp and ubuntu then it must be a problem in the BIOS clock.

I recommend you enter the BIOS and see the time there.

---

### Post by daberger on 2008-06-13
once again. bad computer bios is messed up. not worth the effort

---

