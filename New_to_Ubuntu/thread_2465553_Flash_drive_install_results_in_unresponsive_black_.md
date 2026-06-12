---
title: "Flash drive install results in unresponsive black screen. Stuck."
date: 2021-08-04
forum: New to Ubuntu
---

### Post by mumbletypeg on 2021-08-04
Attempting to install Ubuntu 20.04.2 on desktop-
Processor: Intel(R) Core(TM) i7-6700 CPU @ 3.40GHz   3.40 GHz
Ram:16.0 GB
Graphics card: NVIDA GeForce GTX 960
Generic PnP monitor

With iso on flash drive. 
Reboot to flash but get black screen. 
Have tried switching monitor from graphics card to motherboard, with no result. 

Give up and reboot to windows and see my clock has been reset, which I remember would happen in past, when I dual booted a computer with Linux. 

Thank you in advance :)

---

### Post by TheFu on 2021-08-05
**20.04 release notes** discuss nvidia issues. Please read those.

---

### Post by tea for one on 2021-08-05
How did you prepare your bootable flash drive?

---

### Post by TheFu on 2021-08-05
> **tea for one said:**
> How did you prepare your bootable flash drive?

Excellent question.  To the OP, you can't just copy the .iso file onto a flash directory using Windows. There are special tools to put the ISO onto the flash drive in a specific way.  **Rufus** is a popular tool. I've never used it, so cannot guide.  If you like bloat, **Etcher** is another.

For Unix-like OSes, there are lots of methods/techniques that don't need special programs. This is how I do it, using the built-in programs like cp or dd.

---

### Post by garvinrick4 on 2021-08-05
I have always used "startup disk creator" on ubuntu made most likely  a 100 of them
for all versions of linux and never had a problem simple as you can get.

---

### Post by mumbletypeg on 2021-08-06
I used Rufus 3.14.1788

---

### Post by mumbletypeg on 2021-08-06
> **tea for one said:**
> How did you prepare your bootable flash drive?

I used Rufus 3.14...

Sorry, can't find or figure out how to delete my extra post. 

-------------
TheFu "**20.04 release notes** discuss nvidia issues. Please read those" 				

Thanks TheFu, I searched the release notes which did mention fixes stuff like 'Fix the way we validate the nvidia modules metapackages ." and driver fixes but nothing that I could see as relating to me.

---

### Post by tea for one on 2021-08-06
> **mumbletypeg said:**
> I used Rufus 3.14

What were your choices for partition scheme and target system? 
Do you have to do anything special for your PC to boot from external media?
Try a different flash drive?
Another USB port?

---

### Post by mumbletypeg on 2021-08-06
> **tea for one said:**
> What were your choices for partition scheme and target system? 
Do you have to do anything special for your PC to boot from external media?
Try a different flash drive?
Another USB port?

Thank you tea for one! You solved it. Used another flash drive and it worked like a charm. 
Now I hope to change the post title, to solved. :)

---

