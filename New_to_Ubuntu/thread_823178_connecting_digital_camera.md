---
title: "connecting digital camera"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Sham885 on 2008-06-09
I can't open my sanyo camera.  I ran sudo lsusb and it shows up:

Bus 005 Device 007: ID 0474:0274 Sanyo Electric Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0053 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

and under places a "usb device" now appears when it's plugged in but it says unable to mount location.

---

### Post by wolfen69 on 2008-06-09
try installing gthumb to import any photos.
```
sudo apt-get install gthumb
```it has worked great with 3 different cameras for me.

---

### Post by starcannon on 2008-06-09
I've had few camera's that wouldn't play nice with Ubuntu, I just use a card reader when that happens.

---

### Post by Sham885 on 2008-06-09
Gthumb and Fspot don't even know it's there.  The usb device doesn't show up on their lists and fspot says no camera connected.  Attempting to use the "open with" to get these programs to open the camera did nothing in fspot and froze gthumb.

---

### Post by Sham885 on 2008-06-10
What's a good card reader around $10 that works with ubuntu and windows and reads SD and memory stick pro duo?  I was considering this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820310001]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820310001")

---

### Post by spyrosebastos on 2009-06-12
Same problem with a Kodak EasyShare P712; was working in 8.10.  Any work arounds to date?

---

