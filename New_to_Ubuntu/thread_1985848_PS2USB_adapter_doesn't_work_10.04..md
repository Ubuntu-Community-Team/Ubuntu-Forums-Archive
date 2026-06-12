---
title: "PS2/USB adapter doesn't work 10.04."
date: 2012-05-23
forum: New to Ubuntu
---

### Post by cabman46 on 2012-05-23
I recently built a new system for a friend with Ubuntu 10.04 OS. The motherboard doesn't have PS2 connectors so I loaned him my only spare USB keyboard while I ordered him a PS2/USB adapter so he could use his PS2 keyboard.. The system works great. However, I received the adapter and plugged it in and it is not recognized? Unfortunately, I'm not too swift with Linux to help him. I know USB keyboards are a dime a dozen but was curious why this don't work?

---

### Post by mörgæs on 2012-05-24
Why did you pick 10.04 and not 12.04?

---

### Post by duracella on 2012-05-24
Open Terminal with Ctrl + Alt + T , type ```
lsusb
``` and post the output here.

And yeah, 12.04 LTS is great!

---

### Post by cabman46 on 2012-05-24
> **mörgæs said:**
> Why did you pick 10.04 and not 12.04?
I kinda thought someone would ask this. It just so happened that my broadband router died the week I was building this PC and couldn't get to 12.04. All I had on CD was 10.04. One of these days I'll get 12.04 on his PC.

---

### Post by cabman46 on 2012-05-24
> **duracella said:**
> Open Terminal with Ctrl + Alt + T , type ```
lsusb
``` and post the output here.

And yeah, 12.04 LTS is great!

I have a question. I will have to put the USB keyboard on the PC to type this in. Will the lsusb results be any different without the adapter?

---

### Post by cabman46 on 2012-05-24
> **cabman46 said:**
> I have a question. I will have to put the USB keyboard on the PC to type this in. Will the lsusb results be any different without the adapter?
bill@bill-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 004 Device 002: ID 050f:0003 KC Technology, Inc. KC82C160S Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bill@bill-desktop:~$

---

### Post by cabman46 on 2012-05-25
I found out this adapter doesn't work on Windows either!

---

### Post by duracella on 2012-06-05
> **cabman46 said:**
> I found out this adapter doesn't work on Windows either!

So the usb to PS2 connector was broken then, huh?
Or was it your motherboard that did not support the adapter?

Most of the times when things don't work in Ubuntu, it doesn't work in Windows either...;)

---

