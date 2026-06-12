---
title: "HP Deskjet 3520 printer/scanner problem"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by rberger on 2013-02-22
I set up a friend running Ubuntu 10.40 on a notebook a couple years ago and has now bought a HP Deskjet 3520 printer/scanner to replace his old printer. He brought it and his notebook over to my place and we got it running on my WiFi. Both the printer and scanner worked from his notebook on WiFi and from my Ubuntu 12.10 desktop on the network. 

He took it home and changed the WiFi access key for his WiFi. From his notebook he gets a 5012 communication error. With the old desktop box that I just installed 12.04 on for him, I got him to set it up under System Settings. It says it prints but there's nothing. Now his partner, she is able to print from her Windows 7 laptop successfully via Wifi. 

Any suggestions?

Rick

---

### Post by coffeecat on 2013-02-22
To save me typing it all out again have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)

There should be all you need to get it working in 12.04 from post #4 on.

---

### Post by rberger on 2013-02-22
I not sure it's the same situation because it works on my home network with his 10.04 notebook via WiFi and with my desktop running 12.10. Switching to his network should just require his WiFi key and maybe an different IP address for the printer. Shouldn't it?

---

### Post by aprilspyder on 2013-02-22
I just purchased an HP Deskjet 3520 e-all-in-one.  It shows up in the printers section but will not print.  I can scan and print documents I have, but nothing from the computer.  Says it's processing, has even said completed, but nothing prints.  Please help!  New to Ubuntu as well.  For surfing, loving it.  Getting so frustrated with not being able to use this printer.

---

### Post by kurt18947 on 2013-02-23
> **aprilspyder said:**
> I just purchased an HP Deskjet 3520 e-all-in-one.  It shows up in the printers section but will not print.  I can scan and print documents I have, but nothing from the computer.  Says it's processing, has even said completed, but nothing prints.  Please help!  New to Ubuntu as well.  For surfing, loving it.  Getting so frustrated with not being able to use this printer.

Have you installed the latest hplip as coffeecat recommends in the linked thread?  I haven't had an HP printer for some time so am not current.  It seems the version of hplip in the repositories is dated and doesn't recognizer newer models.   It used to be necessary to install hplip-gui as well to get a GUI interface.  I don't know if that's still the case.

---

### Post by coffeecat on 2013-02-23
> **rberger said:**
> I not sure it's the same situation because it works on my home network with his 10.04 notebook via WiFi and with my desktop running 12.10. Switching to his network should just require his WiFi key and maybe an different IP address for the printer. Shouldn't it?

The old version of the HPLIP driver that comes with 10.04 will certainly not be able to run the Deskjet 3520. I can only assume that when connected to your network your friend  is printing via your 12.10 setup - the version of the HPLIP driver in 12.10 is able to. If he is running a version of Ubuntu prior to 12.10, he needs to install the latest HPLIP driver from the HP website as linked in the thread I linked earlier. This will work in 12.04. I don't know about 10.04 - HPLIP has dependencies which may or may not be satisfiable in 10.04

Another thing for your friend to consider. The desktop version of 10.04 will become end-of-life in April this year and they will need to upgrade to either 12.04 or 12.10. Long story short: The HP Deskjet 3520 works out of the box in 12.10, and works in 12.04 if you install the HPLIP driver from the HP website.

---

### Post by aprilspyder on 2013-02-23
Well, my computer has hplip 3.12.2-1 installed on it.  I"ve gotten to a point that has an installation window but when I click next it still won't find the drivers.  I think I'm going to take it in and have someone else try it.  I have been trying for a while and am completed frustrated and out of ideas.  I have never had as many problems with a regular windows os.  My unbuntu is 12.04.

---

