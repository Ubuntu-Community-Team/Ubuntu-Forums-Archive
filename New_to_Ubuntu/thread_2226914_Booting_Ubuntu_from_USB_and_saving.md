---
title: "Booting Ubuntu from USB and saving"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by pat18 on 2014-05-29
Hello,

I am trying to run Ubuntu off my flash drive. I want to be able to boot and run Ubuntu live from the USB whenever it is plugged in. I hope to be able to plugin the USB into any computer and have my Ubuntu operating system with all of my saved files and preferences self contained on the USB drive.

I have already gone through a variety of steps but every time I make a USB startup drive - I have no problem booting to Ubuntu, but whenever I make changes to the OS or add files and then restart - it boots a clean version without any of my files and changes. I would like any changes I make to be saved onto the USB. 

- Macbook Pro running OS X 10.9.3
- 16 gb flash drive

Thank you for any tips or advice.

---

### Post by sudodus on 2014-05-29
Welcome to the Ubuntu Forums :-)

There is a thread at the Ubuntu Forums addressing your task. I hope it will help you
[URL="http://ubuntuforums.org/showthread.php?t=2174630"]
Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac[/URL]

---

### Post by pat18 on 2014-05-29
Thank You :D

Yes I have followed those instructions and was successful in booting from the USB - My problem is that every time I boot and I make changes, whether that be changing system preferences or creating documents, it is never saved the next time that I book from the USB.

Everytime (as stated in your linked tutorial) - I start from the option "Try Ubuntu without Installing" - I get to the main desktop but my changes will not hold upon further boot ups.
 
Do I need to follow to installation on my USB drive?

---

### Post by sudodus on 2014-05-29
You must follow all the instructions including to create a casper-rw file or partition and to add the boot option persistent. Otherwise there will be no persistence, and your data will be lost.

If you post in that thread, I think *Quackers* will reply in a helpful way. I have no Mac computer, and can't help with the details that are specific for such computers.

---

