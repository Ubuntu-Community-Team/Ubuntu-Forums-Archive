---
title: "Usb WIFI adapter installation"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by sazza on 2012-07-11
Hi Guys,
  I am very new to ubuntu and i just installed Ubuntu 12.04 and was trying to connect my usb wifi adapter, Can somebody please teach me how to do it. I have really no idea about Linux so you might have to explain me step by step. Appreciate your help.


sarmen@sarmen-Satellite-L555:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
sarmen@sarmen-Satellite-L555:~$ ^C
sarmen@sarmen-Satellite-L555:~$

---

### Post by carl4926 on 2012-07-11
It should just work
Click the wireless manager in the top panel, do you see access points?

---

### Post by sazza on 2012-07-11
Hi, 

Oh yes, it's there but it's all greyed out, does that mean i am connected through my wifi adapter..

---

### Post by carl4926 on 2012-07-11
> **sazza said:**
> Hi, 

Oh yes, it's there but it's all greyed out, does that mean i am connected through my wifi adapter..
No it means something is not right
Can you see the Enable Wireless option?
Is it checked? Can you check it?

---

### Post by sazza on 2012-07-11
yeah, it's all checked, i just restarted my laptop and now the adapter is gone and its just connecting through my internal wifi adapter...just before it was there before i started and also i had options to choose from but not anymore..

---

### Post by carl4926 on 2012-07-11
Just to clarify...

You are trying to use a internal and and additional USB device at the same time?

---

### Post by NikTh on 2012-07-11
> **carl4926 said:**
> Just to clarify...

You are trying to use a internal and and additional USB device at the same time?

Probably yes. I understood that too. 
OP if you want to use the external usb  , try to disable the internal WiFi from Bios of close it (from a switch) before plug in the Usb adapter.

---

### Post by sazza on 2012-07-11
Nah, i just wanna use my usb adapter coz my internal wifi sucks..so how do i go about disabling it..need to go to bios settings is it?

---

### Post by sazza on 2012-07-11
Hi guys,
  I just disable by built in wifi through bios settings and after rebooting, i have got no wifi at all, my usb wifi is plugged in but in the wifi settings it say, wireless is disabled at hardware..does that mean i have not installed my driver properly..it came with a cd and also has a folder named linux and i did extracted the file to my downloads directory but i have no idea how to install it..please help

---

### Post by sazza on 2012-07-11
It's all good now..thanks guys..i didnt had to disable or anything.was only a simple matter of plugging out my usb device and restarting and then only connecting it ..and i could have the option of choosing between the two..cheers for those who helped me..appreciate it

---

