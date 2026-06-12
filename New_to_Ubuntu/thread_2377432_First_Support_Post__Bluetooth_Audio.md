---
title: "First Support Post : Bluetooth Audio"
date: 2017-11-13
forum: New to Ubuntu
---

### Post by dave.todd on 2017-11-13
Hello everyone.
This is my first post and therefore I put in beginners section as requested in the welcome message.
I would have gone for wireless or hardware personally.

To cut to the chase I have finally had it to the point of no return with MS Windows and the latest creators update (save the massive changes for new versions, and just roll out patches pls)
I have a laptop (Lenovo Yoga 3 Pro) that has always happily bluetoothed audio to a Logitech UE Boom (original) speaker.
I just stuck on the latest download of Ubuntu (Budgie Desktop, love it) and everything basic worked except bluetooth to the speakers.
I have turned off all other devices that have the potential to interfere with the connection and am quite fluent in dong this process with both Windows and Android.

What do I do, where do I start, what do you need from me to help me resolve the issue? 
What tool do I use to ID the Yoga 3 model if that helps?
What bluetooth diagnostic tools do I have available?
Is there an advanced bluetooth UI app that I can get?

Thank you in advance for your time.

EDIT : Other things I need to check I can get working after this:
- Internet and Wireless (working)
- File Sharing (working)
- Wine a simple windows app
- Torrent Client
- Universal Media Server
- Virtual Machines
- Facebook Chat client
- Finish LFCS training/exam

---

### Post by dave.todd on 2017-11-17
I didn't get much response , not sure what you guys need from me.
I took a few screen shots, they don't help much.
And of course i cant upload images, no where to store them.

Basically it goes :
Not Set Up
Searching (circle animation)
Not Set Up
Disconnected

When i double click on UE Boom, the  device is paired but not connected
When i click connect it goes into Searching (circle animation) then back to not connected.
The sound settings don't have it as an available device.


I really don't have any sort of diagnostics to understand any thing further.

Looking for help please.

---

### Post by howefield on 2017-11-17
> **dave.todd said:**
> ...I took a few screen shots, they don't help much..

Not much help with the actual problem but please use the paperclip icon to attach images to your posts, if they will furnish more detail to anyone who can offer assistance. Also bear in mind that although you may be new to Ubuntu, your question may well be better suited elsewhere so if you want it moved simply use the report button and a member of the staff will help if the request is appropriate.

---

### Post by jeremy31 on 2017-11-19
You can try using terminal with ```
bluetoothctl
```
See if you can use the connect command followed by the speakers MAC address allows it to be seen in sound settings.  I have tried helping with UE Boom 2 without any luck, here is what my terminal shows when I paired with a cheap speaker I have with commands I entered are scan on, pair, trust, and connect with the MAC address
```
 bluetoothctl
[NEW] Controller A4:DB:30:25:39:AA jeremy31-Lenovo-G710 [default]
Agent registered
[bluetooth]# scan on
Discovery started
[CHG] Controller A4:DB:30:25:39:AA Discovering: yes
[NEW] Device E8:07:BF:05:7D:BA iHome iBT60
[bluetooth]# pair E8:07:BF:05:7D:BA 
Attempting to pair with E8:07:BF:05:7D:BA
[CHG] Device E8:07:BF:05:7D:BA Connected: yes
[CHG] Device E8:07:BF:05:7D:BA UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device E8:07:BF:05:7D:BA UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device E8:07:BF:05:7D:BA UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device E8:07:BF:05:7D:BA ServicesResolved: yes
[CHG] Device E8:07:BF:05:7D:BA Paired: yes
Pairing successful
[iHome iBT60]# trust E8:07:BF:05:7D:BA 
[CHG] Device E8:07:BF:05:7D:BA Trusted: yes
Changing E8:07:BF:05:7D:BA trust succeeded
[CHG] Device E8:07:BF:05:7D:BA ServicesResolved: no
[CHG] Device E8:07:BF:05:7D:BA Connected: no
[bluetooth]# connect E8:07:BF:05:7D:BA 
Attempting to connect to E8:07:BF:05:7D:BA
[CHG] Device E8:07:BF:05:7D:BA Connected: yes
Connection successful
[CHG] Device E8:07:BF:05:7D:BA ServicesResolved: yes
[iHome iBT60]# 

```
Use CTRL + d to exit bluetoothctl

---

