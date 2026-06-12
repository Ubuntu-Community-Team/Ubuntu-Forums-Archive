---
title: "how do I get back to windows 7"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by l0o on 2012-12-30
I have just recently installed Ubuntu, it is giving me problems & I want to redownload it.
But I can't do that on Ubuntu because it won't connect me to my wireless... Lol

So I need to know how to get back to Windows 7? If anybody can please tell me how. I've got the newest version.

Thanks all

---

### Post by Slaygod on 2012-12-30
What kind of problems is wireless giving you? Run these commands in Terminal and tell me what you see, and I'll see if I can spot the wi-fi card:

> lspci

> lsusb

---

### Post by adityamagadi on 2012-12-30
have you done a dual boot(windows alongside ubuntu)? using wubi? your question is not descriptive enough to help you... get back to windows 7??

---

### Post by NikTh on 2012-12-30
Hi ,
if you want to get back to Windows  it is your choice and I respect it,  whilst I cannot help you with details the procedure is quite simple... 

Boot from Windows DVD and install. 

Thanks

---

### Post by l0o on 2012-12-30
I have done what you have asked, this is what I get
Bus 001 Device 002: ID 8087:0024 Intel Corp. Intergrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Intergrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. Card reader



I've split my hard drive into 2. One half is Ubuntu & the other is windows 7... How do I switch to windows 7?
That's the problem I am having. But if someone can get my wifi working, then I can redownload it here then burn to disk then put it back on. & hopefully it works

---

### Post by l0o on 2012-12-30
I have tried installing indows again. It won't work :( I don't know why it won't work.
I even tried to install Windows 8. But it won't work

---

### Post by ajgreeny on 2012-12-30
So you can boot into Ubuntu but not into Windows; correct?

Do you see the grub menu when you boot the computer giving you the option of either Ubuntu or Windows?

From ubuntu terminal let's see the output of ```
sudo fdisk -l
``` which will show us if windows is still on the computer, which from your answers so far is not at all clear.

---

