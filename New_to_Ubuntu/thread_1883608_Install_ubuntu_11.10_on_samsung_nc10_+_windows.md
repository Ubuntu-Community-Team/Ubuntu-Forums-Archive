---
title: "Install ubuntu 11.10 on samsung nc10 + windows"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by antobbo on 2011-11-19
Hi there,
I was wondering if anybody can help me to install ubuntu 11.10 on my samsung nc10 netbook. At the moment it runs windows only and I would like to install ubuntu and keep windows so to have dual boot.
I wonder if you guys could tell me how to go about it, how to perhaps partition and things like that because I am not 100% how to do it. 
Also if you could point me to some resources too, maybe give me any suggestions as to whether there are issues with the ubuntu 11.10 and the samsung netbook. In terms of spec it has 2gb RAM but I installed ubuntu on a dell inspiron 1300 so it should be ok on the samsung
thanks a lot

---

### Post by xdragonforce on 2011-11-19
1)Download Ubuntu from [http://ubuntu.com/download/ubuntu/download](http://ubuntu.com/download/ubuntu/download)
2)Follow the instructions on the page on how to install in to a USB/CD/DVD
3)Reboot and press the key that enters Boot device order (usually DEL) and choose USB/DVD
4)Choose "Install Ubuntu to a Hard Drive" and wait while it loads up
5)Go through the installer and when it says what do you want to do, hit "Install alonside windows" and thats basically it.

---

### Post by roger_1960 on 2011-11-19
Hi

As always when doing anything with partitions, back up all your data to an external drive/cloud before you start the process. (In case of murphy being around)

---

### Post by Nikhil Parmar on 2011-11-19
Hey you can also try to install using WUBI.exe....This allows you to install Ubuntu in your Windows partition, without formatting. Its just a process of 15 mins and you have powerful Ubuntu in dual boot  :).
Here are the steps:
1. Burn the .iso file in a cd and put it inside your CD drive.
2. Windows  will prompt you to run the autorun Wubi.exe file found in the CD.
3. Double click on Wubi.exe and then you have simple option of selecting the destination windows drive, try installing in other drive rather than C: ie OS drive (since you are installing UNDER WINDOWS).
4. Allot a fixed space (Your allotted size will not grow nor shrink its fixed )
5. Next--> username->password
6. Boot and let Ubuntu do rest its things.

Enjoy Ubuntu in dual boot.

NOTE: If U format your windows OS i.e C: drive, Your Ubuntu wont boot since it is installed under Windows, reinstalling Windows will again boot ur Ubuntu..............:)

---

### Post by antobbo on 2011-11-19
Excellent, all done, inserted the cd and installed it alongside windows, thanks guys for the advices

---

