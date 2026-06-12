---
title: "Help with linkysys"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Jaduncan1450 on 2008-07-16
I just downloaded ubuntu on my other machine (my main one) last night, and cant seem to be able to access internet. I use linksys, and so far only thing i can find is wired or modem connections. Any idea's on how i can get it to use my wireless linksys?

---

### Post by snowpine on 2008-07-16
> **Jaduncan1450 said:**
> I just downloaded ubuntu on my other machine (my main one) last night, and cant seem to be able to access internet. I use linksys, and so far only thing i can find is wired or modem connections. Any idea's on how i can get it to use my wireless linksys?

Hi Jaduncan, yes, you can get Linksys working from Ubuntu. However, the exact method depends the model and version number of your Linksys adapter. I have a WUSB54Gv4.0, for example. Look at the little white sticker to get the exact model number, and then post back.

This is the method that worked well for me: [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

ps Welcome to the forums!

---

### Post by Jaduncan1450 on 2008-07-16
ok just looked on the sticker, it says MEQ10E301856

---

### Post by snowpine on 2008-07-16
> **Jaduncan1450 said:**
> ok just looked on the sticker, it says MEQ10E301856

That sounds like a serial number, not the model number... try finding your model on the [www.linksys.com](www.linksys.com) by clicking Technical Support (and bookmark the page once you find it, because you will need it eventually to download the driver).

ps Maybe it is not a white sticker after all, I am at a different computer right now. But there should be a model number somewhere on the unit.

---

### Post by halitech on 2008-07-16
can you open a terminal (Applications - Accessories - terminal) and post the output of

```
lsusb
```

---

### Post by Jaduncan1450 on 2008-07-16
WUSB54G  sound better?

---

### Post by Jaduncan1450 on 2008-07-16
> **halitech said:**
> can you open a terminal (Applications - Accessories - terminal) and post the output of

```
lsusb
```

When i did that i got a bunch of "BUS" things, most refering to logitech.

---

### Post by snowpine on 2008-07-16
> **Jaduncan1450 said:**
> WUSB54G  sound better?

Yes, WUSB54G is the same one I have. You need to know which version  number (should be somewhere on there, mine is v4.0) and then carefully follow the instructions in post #1 of the link in my previous post. Good luck!

---

### Post by halitech on 2008-07-16
if you don't get anything that looks like your wireless card it may not be installed or working properly. 

```

daryl@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 032: ID 067b:2571 Prolific Technology, Inc. 
Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 004: ID 045e:00f6 Microsoft Corp. 
Bus 001 Device 002: ID 03eb:0902 Atmel Corp. 
Bus 001 Device 001: ID 0000:0000  
daryl@ubuntu:~$ 

```

is it a usb wireless adapter or a card or built in?

---

### Post by snowpine on 2008-07-16
ps I also recommend installing wicd by typing 'sudo apt-get install wicd' at the terminal command line. This is optional, not required, but I like it better than the built-in network manager with the Linksys WUSB54G.

Also, if you have any problems while following the instructions in that thread I linked for you, you should post them in that thread for the best reply. Good luck!

---

### Post by snowpine on 2008-07-16
> **halitech said:**
> if you don't get anything that looks like your wireless card it may not be installed or working properly. 

```

daryl@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 032: ID 067b:2571 Prolific Technology, Inc. 
Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 004: ID 045e:00f6 Microsoft Corp. 
Bus 001 Device 002: ID 03eb:0902 Atmel Corp. 
Bus 001 Device 001: ID 0000:0000  
daryl@ubuntu:~$ 

```

is it a usb wireless adapter or a card or built in?

Halitech, it is a USB adaptor that uses the rt2500usb driver (at least, v4.0, which I have, does). The thread I am referring him to is the ndiswrapper method. Do you think that is good advice for the OP?

edit: oops, wrong driver number

---

### Post by Jaduncan1450 on 2008-07-16
> **halitech said:**
> if you don't get anything that looks like your wireless card it may not be installed or working properly. 

```

daryl@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 032: ID 067b:2571 Prolific Technology, Inc. 
Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 004: ID 045e:00f6 Microsoft Corp. 
Bus 001 Device 002: ID 03eb:0902 Atmel Corp. 
Bus 001 Device 001: ID 0000:0000  
daryl@ubuntu:~$ 

```

is it a usb wireless adapter or a card or built in?


USB Wireless

---

### Post by Jaduncan1450 on 2008-07-16
> **snowpine said:**
> Halitech, it is a USB adaptor that uses the RT2500 driver (at least, v4.0, which I have, does). The thread I am referring him to is the ndiswrapper method. Do you think that is good advice for the OP?

edit: oops, wrong driver number

Anychance you could find the link for me? I am trying my hardest but just cant find where i download the driver, ALSO, can i put the driver on disc from this machine to put on the other? 

PS: It is 4.0 btw

---

### Post by halitech on 2008-07-16
> **snowpine said:**
> Halitech, it is a USB adaptor that uses the rt2500usb driver (at least, v4.0, which I have, does). The thread I am referring him to is the ndiswrapper method. Do you think that is good advice for the OP?

edit: oops, wrong driver number

if it is the same as yours then that probably is a good idea.

Jaduncan1450, do you know how to copy info from the terminal? I would recommend that if you do, you copy the info from lsusb into a text file and then post it here so we can determine the best steps. Will be useless to go any farther if the machine isn't seeing the adapter

---

### Post by Jaduncan1450 on 2008-07-16
> **halitech said:**
> if it is the same as yours then that probably is a good idea.

Jaduncan1450, do you know how to copy info from the terminal? I would recommend that if you do, you copy the info from lsusb into a text file and then post it here so we can determine the best steps. Will be useless to go any farther if the machine isn't seeing the adapter

How would i do that if im not on that machine? lol

---

### Post by snowpine on 2008-07-16
> **Jaduncan1450 said:**
> Anychance you could find the link for me? I am trying my hardest but just cant find where i download the driver, ALSO, can i put the driver on disc from this machine to put on the other? 

PS: It is 4.0 btw

Here is the link for you: [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3DWUSB54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775B01&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3DWUSB54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377543775B01&displaypage=download#versiondetail)

Click on "Driver" and it should download an .exe file for you. You can download this file on a different computer and then copy it (usb drive, burn a cd, etc.) to a different computer.

Good luck!

---

### Post by halitech on 2008-07-16
> **Jaduncan1450 said:**
> How would i do that if im not on that machine? lol

save the text file to a thumb drive then copy it to the other computer with internet access and open it and post the info.

---

