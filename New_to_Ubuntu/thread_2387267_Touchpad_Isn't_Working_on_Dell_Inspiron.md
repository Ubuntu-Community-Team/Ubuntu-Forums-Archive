---
title: "Touchpad Isn't Working on Dell Inspiron"
date: 2018-03-16
forum: New to Ubuntu
---

### Post by pcoppock on 2018-03-16
Hi:

Today I bought a 11.6" Dell Inspiron with Windows 10 on it. After wiping it and successfully installing Lubuntu 16, I am having touchpad problems. After I turn my computer on, I can use the touchpad for about 30 seconds before it stops working. I am currently using a USB mouse. After it stops working, I run the 'xinput' command in the terminal and can see that the computer does still recognize the touchpad.

Does anyone have any ideas about how to fix the touchpad?

Thank you very much in advance.

---

### Post by wildmanne39 on 2018-03-16
*Thread moved to **New to Ubuntu, a more appropriate forum**.*

---

### Post by Geoffrey_Arndt on 2018-03-17
Does the touchpad work in a "Live" DE media?

---

### Post by pcoppock on 2018-03-17
I don&#8217;t understand. (I am very new to OS&#8217;s in general.) Could you elaborate?

---

### Post by mörgæs on 2018-03-18
Live booting means that the operative system is not installed on the computer. It runs from a USB stick or DVD and lives only in memory for as long as the computer is turned on.

Yes, a live boot of 18.04 (beta) is worth trying.

---

### Post by pcoppock on 2018-03-18
Thank you @mörgæs. I live booted Lubuntu 17.10.1 (I wasn't sure how to get version 18). The touchpad acted the same in the live boot. It worked for several seconds, and then stopped. The System Profiler and Benchmark program showed me that the touchpad was still recognized. By the way, I forgot to mention that the touchpad worked perfectly in Windows 10. [Here]("https://photos.app.goo.gl/NLB2UIXO0lF8LGri2") is a link to a Google Photos album with the following images--two from the System Profiler about my touchpad and one of a message that came up during the live boot.

---

### Post by pcoppock on 2018-03-18
Thank you both for your suggestions. I Googled around some more, and found the following solution on askubuntu: [http://askubuntu.com/a/632570/55128](http://askubuntu.com/a/632570/55128).

I ran the code and my touchpad now works. Hurray!

---

