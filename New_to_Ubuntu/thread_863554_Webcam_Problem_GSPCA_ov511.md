---
title: "Webcam Problem GSPCA ov511"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by BGFG on 2008-07-18
Hi, 
I have a MSI Starcam 370i that i can't get to work. I recently visited the forums about this problem and was given these instructions:
i ran sudo modprobe for both gspca and ov511 then i ran lsmod to ensure that they had loaded and they had.

When i opened skype and check my video options, i was getting video from the webcam. I assumed all was well, closed skype and moved on. Since then i have not been able to get any feed from the cam.

I ran lsmod today and saw that gspca was loaded. I then modprobed ov511 and tried getting video in cheese but no luck.

I installed cheese to test and still no results. Any help would be appreciated.

NB. any noobs like myself that happen across this thread please note

```
 sudo modprobe gspca

sudo modprobe ov511
```

Loads the webcam drivers (they are included in the kernel)

```
 lsmod 
```

is a list of kernel modules (i think :)) currently loaded 
please correct me if my terminology is wrong.

---

### Post by cariboo on 2008-07-18
Could you run :

```
lsusb
```aying that 

so that we can see who manufactured your web cam. MSI will not support linux, so no linux drivers for any of their equipment. Saying I use MSI motherboards, and I've never had a problem getting everything to work properly, sometimes it just takes a bit of digging.

Jim

---

### Post by BGFG on 2008-07-18
Thanks for the response Jim, here's my output

Bus 002 Device 005: ID 0644:0201 TEAC Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 009: ID 046d:c719 Logitech, Inc. 
Bus 001 Device 008: ID 046d:c718 Logitech, Inc. 
Bus 001 Device 007: ID 413c:8130 Dell Computer Corp. 
Bus 001 Device 006: ID 046d:0b05 Logitech, Inc. 
Bus 001 Device 005: ID 413c:3012 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:2105 Dell Computer Corp. 
Bus 001 Device 003: ID 0c45:60c0 Microdia 
Bus 001 Device 001: ID 0000:0000

On another note, unluckily, i didn't build this machine :( 
Dell inspiron 531, Not too bad though.

---

### Post by BGFG on 2008-07-21
I should also add, that it's a usb cam and the audio works fine. Anyone else out there with a working MSI cam ?

---

