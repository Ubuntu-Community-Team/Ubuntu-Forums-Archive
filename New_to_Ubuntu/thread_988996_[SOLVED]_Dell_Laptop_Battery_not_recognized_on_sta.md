---
title: "[SOLVED] Dell Laptop Battery not recognized on startup..."
date: 2008-11-21
forum: New to Ubuntu
---

### Post by DarkSoul1984 on 2008-11-21
Hi,

I'm new to Ubuntu, and for the past five years I've worked almost solely with Windows, so I'm relearning things as I go.

Basically, my issue is I formatted my laptop and installed Ubuntu 8.04 (hardy) in an attempt to "expand my horizons."

I am working with a Dell Inspiron 1501 and everything works great so far, except I just noticed a set up warning when I rebooted my machine for the first time since updating everything. It said it doesn't recognize the battery and it won't be able to recharge it.

It's a DELLXU8827 battery, lithium ion by Panasonic (the cheapest one they had) so I don't expect it to work as well now that it is more than a year old and has been used rather consistently due to my job requirements.

The battery info screen says it has a capacity of 36% but a charge of 100%, and if I am reading this correctly, this means that the battery is basically dying (1/3 as productive as it used to be), but that it is being charged by the system.

Am I correct in this?

Is there a way to resolve the startup message/issue? I'm not so lazy I can't just press another button, but ideally it would boot right up into Ubuntu.

Thanks for the help.

---

### Post by Kobalt on 2008-11-21
These notifications can be enabled/disabled in gconf. Press Alt+F2 and enter *gconf-editor*
Navigate to apps > gnome-power-manager > notify and check/uncheck what you wish.

---

### Post by DarkSoul1984 on 2008-11-23
Thanks for the information.

Except, what do we do is our F2 key is broken? Does alt-F2 just bring up the console?

---

### Post by Kobalt on 2008-11-24
No it brings an app-launcher, but you can also launch apps the same way using the console.

---

### Post by Cheetah74 on 2009-06-28
I fixed this by taking out the battery and putting it back in, can't take credit for this ingenious fix, I Googled it and found it after searching unfruitfully in the Ubuntu Forums. I didn't even turn off my Laptop, just took the battery out and put it back in, worked 1st time, you may want to be more cautious that that I just stupidly yanked it out while the computer was still running, no probs yet! The post I found the guy said he had to do it 2x. Hope this helps.):P

---

### Post by betty320 on 2010-03-02
do you have the latest version of Dell's Quickset program. This program just recognized my laptop battery is getting near the end of it's life cycle.

I think it might be this program that is not recognizing your battery.

Go here and download and install any programs and drivers you need.

[http://support.dell.com/support/downloads/index.aspx](http://support.dell.com/support/downloads/index.aspx)

Since the computer is fairly new, then make it a warranty issue.
you can buy a new [dell inspiron 1501 battery]("http://www.laptopbatteryinc.com.au/dell-inspiron-1501.html") from [www.diggingshop.com]("http://www.diggingshop.com")

---

### Post by Blinkend on 2011-11-21
What if I don't have the service info they ask for at the dell link? Any tips on getting that info? My friend gave me my laptop so all I have is the machine, no paperwork.

-April

---

### Post by aaysha on 2013-01-08
hi.. 
im new with ubuntu (linux programming), 
currently im working with ubuntu 11.10, 
i have "dell inspiron 1545". 
and i recently changed its battery 2 time , but it doesn't recognize my battery, 
whn ever i plugged in but it show (battery not present)

please help me im completely lost...... 
 :(

---

### Post by mlentink on 2013-01-08
Hi aaysha, welcome to the free world.

I really can't help you with your specific problem. You posted it in a rather old thread, that was also marked as "Solved". This means that not many of us will go and lokk at such a thread, because the problem of the original poster is already solved. 

In these cases, it's best to start your own new thread which is likely to get more attention

---

### Post by howefield on 2013-01-08
What he said ^^  :)

Old thread closed.

---

