---
title: "No GRUB menu! Ubuntu/Windows 7 Dual Boot Issues."
date: 2013-04-23
forum: New to Ubuntu
---

### Post by Sayuu89 on 2013-04-23
I'm attempting to setup a dual boot system on my computer, involving the already existing Windows 7 Professional, and Ubuntu Server 12.10. After partitioning around 20 Gigs for Ubuntu Server, I went ahead and completed the install process using a bootable CD. At the end of the process I was asked to restart my computer. Every time I restart my computer it boots straight to Windows.The boot order is correct in my BIOS, but my computer seems to want to skip over GRUB completely. I'm at a loss, any ideas? Thanks!

I should also mention that I did see GRUB installing (so far as I could see), and that every time my computer boots up now it shows a black screen with a cursor flashing, which moves down the page as if someone had hit Return 3 times, before booting up Windows.

---

### Post by carl4926 on 2013-04-23
Make sure you set sda for bootloader location
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png)

---

### Post by Sayuu89 on 2013-04-23
For Ubuntu Server 12.10 I was never given those options in the installation process. I've heard things about choosing a bootloader location on other forums/threads, but I never got a chance to choose.

---

### Post by Akhj on 2013-04-24
Please let us know your Partition lay out so that 1 can help you in a better way.

---

