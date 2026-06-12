---
title: "My computer freezes every 30 mins (Lubuntu 15.1)"
date: 2015-10-30
forum: New to Ubuntu
---

### Post by pablo48 on 2015-10-30
I recently was using Windows 10, and once and for all, decided to kick Windows in the butt and give Linux a shot. I formated the drives and proceeded to install Lubuntu. But after a while of using it, every 30 mins/1hr my computer just freezes, and I wouldn't like it to happen if I'm in the middle of doing work papers, or study.

Does anybody know the cause of this?

I have no knowledge on programming and stuff. I only follow tutorials and forum threads and copy exactly what they say on the terminal.

My specs: Lubuntu 15.1 + Motherboard Intel DH55TC + CPU Intel i5 650 + 4Gb RAM + GPU 240GT + 2 HDD (160Gb and 80Gb).

---

### Post by HereInOz on 2015-10-31
Hi pablo48,

First question:  Does it freeze at the same place in the same program, or is it a complete random freeze, totally unrelated to what you are currently doing?  Random freezes can be tough, so we need as much info as we can get.

Second question:  Why Lubuntu?  Any reason?  That machine would probably have supported Ubuntu quite nicely.

---

### Post by yeah3 on 2015-11-25
Hi, the same happened to me, under windows too with the new (old) notebook.

I bought it with 2 gb ram on ebay and when it came it froze and crashed regularly until I removed one of the ram chips. Now it runs under 1024 and faster than before. 

Less ram, more performance - strange but it works. Maybe you should experiment with the amount of RAM you put into that thing. 

Good luck!

Sounds eerie, but that  was really all it would take to get me a stable machine and OS environment. I am sure there is a mor proper workaround to the problem. Maybe it has to do with the secret OS that are in almost every damn chip and SIm out there and thus in several ones of your notebook too (I guess). Eerie, spooky stuff!

---

### Post by mastablasta on 2015-11-25
install psensor or similar to monitor the system temperatures. : [http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/)

do you have proprietary drivers installed' is this an optimus PC (dual/hybrid graphics)?

ram can be tested with memtest but it take a long time.

a freeze (when he whole desktop freezes) can be caused by a lot of things. most common ones are bad graphics drivers, overheating.

system logs contain plenty of information about what was happening up to when the system crashed.

---

### Post by l1nux2 on 2015-11-25
[B]1.Run system update

2.Check HDD,freezing is usually caused by damaged HDD
[/B]
Good luck

---

### Post by ozygaro on 2015-12-19
Exactly, check HDD first (gnome-disk-utility) and also RAM ([www.memtest.org](www.memtest.org)).

---

