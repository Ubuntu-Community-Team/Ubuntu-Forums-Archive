---
title: "Linux is for me, but i know nothing about it"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by linuxinireland on 2008-05-19
I have a homebuilt machine. Already have ubuntu 8.04 up and running.  But i know nothing about this interface, and i need to do some very advanced, at least to me, things, to include;
Sync compatability with a 16G Ipod touch
Sync compatability with a Generic USB Mp3 Player,(no SD)
Network with wireless router 
ATI Radeon X850XT Video Card utility program ( fan control )- optional
I want these things to run seemlessly, I think Linux would make this easy, however I lack the basic knowledge necessary.
Anyone out there who can help I would like to thank you in advance.
Thank you, 
Linuxinireland

current status
stranded

---

### Post by Inxsible on 2008-05-19
Try this for syncing your Ipod Touch

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

For your wireless...what wireless card do you have? Better yet, give us your system specs.

---

### Post by decoherence on 2008-05-19
check out [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by linuxinireland on 2008-05-19
Alright I built a AMD dual core 939 chipset i think its dual 2.0 Ghz
MSI motherboard its got a 2000 mhz FSB its smaller though, only 2 PCI slots
Ive got 2g of RAM
ATI Radeon x850-xt video card
Ive got this all in an Aspire Cube and I have sufficient cooling as well
Does this help?

---

### Post by tamoneya on 2008-05-19
for the wireless you should open terminal (applications -> accessories -> terminal) and type:```
lspci
```copy the output and post it here.  If you cant get access to a wired internet connection you could copy it into a text file and throw it on a usb drive.

---

### Post by mmb1 on 2008-05-19
Have you plugged in the "generic" mp3 player yet? If not, try it.  You may be surprised.

---

### Post by linuxinireland on 2008-05-19
wow tamoneya, that is incredibly helpful. I am unfortunateley at work right now, not at home.  I though this forum would take days to get my answers fixed not minutes or I would have done this from home, so you could experience my enlightenment. What else does this forum have for me?

---

### Post by jakupl on 2008-05-19
> **Inxsible said:**
> Try this for syncing your Ipod Touch

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

before you do this, be sure to have a backup of your music. I tried it with my 8 GB touch (with firmware 1.1.4), but it did not work... ended up having to restore and loosing my music.
luckily I had a backup.

---

### Post by tamoneya on 2008-05-19
> **linuxinireland said:**
> wow tamoneya, that is incredibly helpful. I am unfortunateley at work right now, not at home.  I though this forum would take days to get my answers fixed not minutes or I would have done this from home, so you could experience my enlightenment. What else does this forum have for me?

I think you will find that this forum is very resposive and always willing to help.  This is typically true of most active open source projects but I feel as if the Ubuntu Forums in particular do a very good job in helping people find solutions.

---

### Post by linuxinireland on 2008-05-19
Can anyone tell me in any more depth about my Ipod touch and how syncing it with GTKPod will work?

---

### Post by zeifertstc on 2008-05-19
While I can't really tell you anything useful about an iPod (any version, can't stand them really), I can help with the wireless access to a certain extent if you have information relating to which hardware you have. The router doesn't matter as much as what make and model of Wireless Adapter you have in your machine. 

If, by chance, you have a Broadcom 43xx card in your machine Ubuntu provides real easy access to what you need to get that up and working. You'll find it under the restricted drivers manager. Anything else you'll likely need to have the original driver disc that came with your hardware. We can go from there on that one. 

I'll wish you luck on the iPod touch, hope you get an answer to that one. Though, it may be as easy as plugging it in like any other MP3 player. But, yeah, good luck with that part.

---

### Post by jakupl on 2008-05-19
> **linuxinireland said:**
> Can anyone tell me in any more depth about my Ipod touch and how syncing it with GTKPod will work?

As far as I understand (I am no expert) you will need to jailbrake your ipod. I tried it using "ziphone" witch is a program for windows, but it actually broke the 1.1.4 firmware on my ipod, and forced me to restore it.

Right now I am too busy, but in about one week, I will try again. It will probably involve downgrading the firmware on my ipod. maybe to 1.1.1... hwo knows. But I sure will keep you informed when I try it.

by the way, congratulations. you (and me) succeeded in buying what must be the most ubuntu un-compatible ipod ever. ;)

But bear in mind, I have and 8 GB. you have the 16 GB. it might not be the same.

---

