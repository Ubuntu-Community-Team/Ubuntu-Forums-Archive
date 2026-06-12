---
title: "Connecting Ubuntu 7.10 to a Motorola Razr (MOT V3)"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by sid351 on 2008-04-30
Hi,

I'm trying to connect my Motorola Razr (MOT V3) to an Ubuntu 7.10 install.

The screen on it (the phone) has stopped working, and I need to rescue all my numbers from it.  I've got the usb cable.

Any ideas on where to, and how to start?

All I really need is the address book off it.

Cheers,

Sid

---

### Post by stuart.reinke on 2009-04-15
I'm having the same trouble. I want to back up my phone book via a usb cable. I've tried kmobile tools and moto4lin. Even ran Motorola Phone Tools under Wine. Always tells me the phone is not connected.

---

### Post by FrostDust on 2009-04-15
> **stuart.reinke said:**
> I'm having the same trouble. I want to back up my phone book via a usb cable. I've tried kmobile tools and moto4lin. Even ran Motorola Phone Tools under Wine. Always tells me the phone is not connected.

Motorola phones have have two separate modes: one lets you simply browse files, including those on a memory card (like ringtones and pictures), while another lets you actually access the phone data, like your contact list, call history, text messages, and so on. Go into settings on the phone, then connections, and check to make sure the USB connection set to whatever sounds most appropriate (or try all the modes available until something works). If this works, you may just be able to use moto4lin instead of Moto Phone Tools with Wine.

If your RAZR is a Verizon phone, I think you have to use Verizon's software, instead of Motorola's.

I'd also guess that while Wine can run programs fine, it has a problem interfacing with hardware because there's another layer between the Window's program code and your device. Like, the phone's data goes through the cable to your motherboard, is interpreted by Ubuntu, and then is sent to the Motorola Phone Tools program. Even if the program is running, thanks to Wine, Ubuntu itself may not be able to properly "pass along" the data. Google this issue to see if it is indeed the situation at hand.

---

### Post by gali98 on 2009-04-15
If you have a sim card, all the numbers should be stored on it.
Kory

---

### Post by stuart.reinke on 2009-04-15
I have two options under the connection settings on my phone (razr v3m). Modem/comm and usb drive. Tried them both in that order. It appears the phone is being detected and connected but I don't know what the error messages mean. Here is what terminal shows:
Modem/com setting on phone:

stuart@stuart-laptop:~$ moto4lin
Form1
PhoneMan
New mode: 2
P2kProc::doConnect()
doActConnect
sendControl Error:[error sending control message: Operation not permitted]
sendControl Error:[error sending control message: Operation not permitted]
(E_getPhoneName: E001)
sendControl Error:[error sending control message: Operation not permitted]
sendControl Error:[error sending control message: Operation not permitted]
(E_getDriveName: E001)
sendControl Error:[error sending control message: Operation not permitted]
(E_fileCount: E001)
sendControl Error:[error sending control message: Operation not permitted]
sendControl Error:[error sending control message: Operation not permitted]
(E_getDriveName: E001)

Usb drive setting on phone:

doActConnect
doActConnect
doActConnect
doActConnect
doActConnect
P2kProc::doConnect()
doActConnect
sendControl Error:[error sending control message: Operation not permitted]
sendControl Error:[error sending control message: Operation not permitted]
(E_getPhoneName: E001)
sendControl Error:[error sending control message: Operation not permitted]
sendControl Error:[error sending control message: Operation not permitted]
(E_getDriveName: E001)
sendControl Error:[error sending control message: Operation not permitted]
(E_fileCount: E001)
sendControl Error:[error sending control message: Operation not permitted]
sendControl Error:[error sending control message: Operation not permitted]
(E_getDriveName: E001)
doActConnect
doActConnect
doActConnect

Hope this helps to find my problem. I really don't want to dual boot with windows just to back up my phone book.

---

