---
title: "Can't change brightness in Ubuntu 13.10"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by 0N3 on 2013-11-07
This worked fine till the other day I have tried every tutorial possible via google searches and nothing has worked. I just can't change the brightness it changes but the screen remains the same. Most answers I get to this I have probably tried already. 

Editing kernel parameters does nothing I have tried them all well actually it does something gives me absolutely no way of changing the brightness.

---

### Post by Toz on 2013-11-07
Can we get a little more information (all commands run from a terminal window - paste back the results):

1. The make/model of your computer.

2. The current set of kernel parameters being used:
```
cat /proc/cmdline
```

3. Your video card(s) and drivers:
```
lspci -k | grep -iA2 VGA
```

4. Your current backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

5. A copy of your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by 0N3 on 2013-11-07
Toz thanks for the reply. I just wiped Ubuntu might wait for 14.04 to come out doubt it will be much better as for me the newer the Ubuntu the worse it's getting.

13.10 alone caused:

System settings to keep disappearing from the unity panel and clock ect.....

Wouldn't go into suspend mode and when it did I would renter my password log in and the whole screen flicker and crash

Horrible battery life just over the hour if lucky

Can't change screen brightness

Wireless disconnecting 3 - 4 times daily

The Unity dash was always slow but even more horiffically slow with the new "smart scopes" no idea why so smart......

Had 3 differen't mouse themes 1 at log in 1 when a window was open and a different mouse theme displaying when only the desktop open.

Google Chrome just won't open a single page even tho every other browser worked fine.

Takes well over a minute to log in to the laptop after putting in my password.

I could name a lot more but those are my main issues.

Horrible experience with the AMD closed source graphics the open source were grand but the fan never stopped spinning and became quite uncomfortable and ate the already poor battery life.

Computer specs:

Toshiba Satellite Pro
1 TB HDD 7,200rpm
Core i7 2.4GHz
8GB DDR3 RAM
1 GB AMD Radeon HD7670M dedicated graphics.
Intel wireless card

Just in my opinion Ubuntu is great for email, FB, Youtube ect..... simple computing tasks as a productive machine it is a horrible experience.
It may sound like a rant but I love Ubuntu it's just getting more and more less productive with each release. AMD and Nvidia are no help to the cause either.

---

