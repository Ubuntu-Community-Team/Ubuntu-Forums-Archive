---
title: "Frequent Hanging on 8.10"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by phantomgunex on 2008-11-21
Hey! I have been experiencing numerous hanging when i upgraded to intrepid. After i log in, I will see my desktop (the panels, everything) but my com will suddenly hang for no reason. This happened many times already. Sometimes when i am doing my development, my com suddenly hangs and i have to force restart it. Fortunately there is auto save. I found out the hangings are more common in KDE than GNOME. I have already reinstalled the system and i am still experiencing the hangings! PLEASSE HELP!!!

---

### Post by eeried on 2008-11-21
Do you have compiz and all the 3D effects on? I heard that could cause some problems.

What is "com"?

---

### Post by phantomgunex on 2008-11-21
com = computer
A... now i cant update my system the update manager says: "A problem occured when checking for updates"
Now i am afraid of turning off my computer. Ok i wil try to remove compiz

---

### Post by Peter09 on 2008-11-21
Hangs are often caused by the video driver.

Can you post the output of the terminal command to confirm the driver that you are using.
```
lshw -C display
```

---

### Post by eeried on 2008-11-21
> "A problem occured when checking for updates"
Now i am afraid of turning off my computer.

Never fear you can stop an upgrade anytime except if it is an upgrade to the next Ubuntu version.

The message means the Ubuntu servers were unavailable or your connection was down.

> Hangs are often caused by the video driver.

I'm all ears as a member of our lug is having hangs all the time and I suspect her nasty ATI 9200.

---

### Post by phantomgunex on 2008-11-22
```
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV11 [GeForce2 MX/MX 400]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: b2
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list
       configuration: latency=32 maxlatency=1 mingnt=5

```

Here u are

---

### Post by nhasian on 2008-11-22
just out of curiosity, do you have an Intel PRO/Wireless 4965 adaptor?

```
lshw -C network
```

I had frequent lockups and blinking caps lock light until i installed the intrepid backports because i have that wifi adaptor.

---

### Post by Peter09 on 2008-11-22
From the output of your lshw command it appears that your video driver is not installed properly.

Have you checked in 

System->Admin->Hardware Drivers

to see if you have any drivers waiting to be enabled?

---

### Post by davidsrsb on 2008-11-22
The MX400 family is legacy so far as Nvidia is concerned

---

### Post by eeried on 2008-11-24
Hello,

We have some old Nvidia video cards too but not your exact model, phantomgunex. They work fine with 8.04 and an NV 32 MMX is fine with 8.10.

Does the fact Nvidia drivers are no longer available means all these cards are doomed and won't work in Ubuntu anymore? :confused:

---

### Post by eeried on 2008-11-27
> NV11 [GeForce2 MX/MX 400]
I have just checked: we have exactly the same card on a Pentium III 128 MB Rambus and a hog of a CRT*monitor: fine with Hardy

I installed Xubuntu 8.10 and things looked all right but I uninstalled it because I felt 8.10 was a bit heavy for this machine and not really needed.

---

