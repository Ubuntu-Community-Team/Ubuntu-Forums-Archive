---
title: "Ubuntu on Acer Aspire P3-171 touchscreen"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by aps0 on 2013-12-26
With Windows 8 pre-installed, I installed Ubuntu 12.04 LTS 32 bits. I don't know why, the installation of 12.04 64 bits and 13.10 64 bits stopped with only an error sound. Without any error message. This computer is like a tablet with a keyboard connectable via bluetooth. I'm not succesful connecting the keyboard with Ubuntu, but I can work with the virtual keyboard in the screen. But with a lot of problems. At the moment I'm trying to use the touchscreen only like a mouse, with one finger, but I have troubles anyway. Sometimes Ubuntu ignores permanently any touch on the screen and I must reinitiate the computer. Anyone knows what can I do to advance in the use of Ubuntu on this computer?

---

### Post by ariadrianto on 2013-12-29
Hi,
I've the same device and very disappointed with windows 8. It's very slow, even with 4 Gb RAM and core I5 processor. I never found this laggy in Ubuntu. I'd like to change this OS into Ubuntu, but no luck. I will waiting your progress and any suggestions....

---

### Post by patrik-bjoerkman on 2014-04-09
Booted 14.04 beta2 off an usbstick and the onlything that doesent work is sound, im going to install it to harddrive and report back !

---

### Post by hilfans on 2014-04-28
I have the same problem also, I think the hardware not supported by vendor to provide the correct driver in [linux]("http://hilfans.wordpress.com").

---

### Post by patrik-bjoerkman on 2014-05-19
I was wrong previously, everything works just fine with 14.04 sound and all


Cant Connect acer keyboard cover, other bt keyboards work fine.

**UPDATE:**

Use the GUI to launch the configuration process, as normal. The passkey printed on bluetooth gui is **wrong**, so you have to install some tools.


sudo apt-get install bluez-hcidump
sudo apt-get install bluez-utils blueman


On a console type:


sudo hcidump -at | grep -A 1 "User Passkey Notification"
which will display the correct passkey.


2013-09-25 14:35:40.653393
HCI Event: User Passkey Notification (0x3b) plen 10
bdaddr XX:XX:XX:XX:XX:XX passkey[B] 66235

[/B]
Type the passkey on the bluetooth keyboard and hit enter.


Reboot and you could see that bluetooth gui still registers your new keyboard.

---

### Post by sven11 on 2014-07-27
Hi,

just registered to say Thank you. that was a great Tip ...

Sven

---

### Post by patrik-bjoerkman on 2014-08-06
I have one issue that i need help with, i cant get rightclick to work on the touch screen.
I have tried a few tips, but i would like to get longpress to give me rightclick, but i dont know how to.


So for now i use a mouse.... :(


//P

---

