---
title: "Unhandled Lockdown error (-16)"
date: 2015-11-25
forum: New to Ubuntu
---

### Post by rillidyll on 2015-11-25
updated my iPhone 4S to iOS 9.1, now i can't access the DCIM folder to download my photos, i can't access the phone whatsoever. instead i get this message:

Unable to access "steven's iPhone"
Unhandled Lockdown error (-16)

what's going on? any workarounds? i see similar questions in the forums re the same message but citing other numbers, eg., error (-20) or (-15) but am reluctant to attempt their solutions.

all i can currently do is access my photos online via iCloud, downloading 3 at a time, where i was used to simply "copy & pasting" from the folders within DCIM into my Picture's folder

running a 32-bit ubuntu 14.04

---

### Post by jesse52 on 2016-04-17
I am finished with Apple products they do not allow you to use them as you want without buying more Apple products.  I hope someone figures out a way for us to access our photos again.  I am mad I updated the IOS that was a big mistake and I knew better but they kept hitting me with update messages and I finally caved in.  My next device will most def be an android and even better an ubuntu phone when they become available and the right price point.

---

### Post by slickymaster on 2016-04-17
Do you have **libimobiledevice** and **ifuse** installed in your system?

If not, unplug your iPhone, open a terminal and run```
sudo apt-get install libimobiledevice-utils ifuse
```Afterwards connect your iPhone to the computer and run again in terminal```
idevicepair unpair && idevicepair pair
```

---

### Post by fmouse on 2016-11-19
> **slickymaster said:**
> Do you have **libimobiledevice** and **ifuse** installed in your system?

If not, unplug your iPhone, open a terminal and run```
sudo apt-get install libimobiledevice-utils ifuse
```Afterwards connect your iPhone to the computer and run again in terminal```
idevicepair unpair && idevicepair pair
```

I installed these two packages with no problem but when I run the command
```
idevicepair unpair && idevicepair pair
``` I get the reponse ```
ERROR: Device b17dd56473a4ec6fd1610b542bfe69062bd45274 is not paired with this host
```
and I still can't connect my iPhone.

---

### Post by slickymaster on 2016-11-20
> **fmouse said:**
> I installed these two packages with no problem but when I run the command
```
idevicepair unpair && idevicepair pair
``` I get the reponse ```
ERROR: Device b17dd56473a4ec6fd1610b542bfe69062bd45274 is not paired with this host
```
and I still can't connect my iPhone.
Closed thread. Necromancy.

This thread is almost a year old, please create a new thread.

In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

