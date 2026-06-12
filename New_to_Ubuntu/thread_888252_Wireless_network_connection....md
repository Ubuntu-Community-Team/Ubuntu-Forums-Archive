---
title: "Wireless network connection..."
date: 2008-08-12
forum: New to Ubuntu
---

### Post by nethanjavier on 2008-08-12
Hello everyone...Im just a newbie here and i just wanna ask if there is a program that will automatically connect to wireless network and ask for password...It seems that i cannot  manually connect to any wireless network around me...please help me..

---

### Post by noobuntu35 on 2008-08-12
> **nethanjavier said:**
> Hello everyone...Im just a newbie here and i just wanna ask if there is a program that will automatically connect to wireless network and ask for password...It seems that i cannot  manually connect to any wireless network around me...please help me..

can you see the network around you? or is it the wi-fi drivers are not installed give us more information it makes troubleshooting quicker for you...

---

### Post by WinterMadness on 2008-08-12
> **nethanjavier said:**
> Hello everyone...Im just a newbie here and i just wanna ask if there is a program that will automatically connect to wireless network and ask for password...It seems that i cannot  manually connect to any wireless network around me...please help me..

theres wifi radar, but i dont think that works that well personally.

what you're going to have to do is get ndiswrapper and its utilities, and ndisgtk and the .inf file for your wireless driver that you use for windows

if you dont know where the .inf file is try going to the website of your wireless card manufacturer and just downloading the driver.

you can find a bunch of really good ndiswrapper tutorials, so if what i say isnt effective, just try one of them

terminal:
sudo ndiswrapper -i nameoffile.inf
sudo ndiswrapper -l
you should see the driver saying its installed, and it should say hardware present too

sudo modprobe ndiswrapper

after that goto system>administration>windows wireless drivers and then find the .inf file  and load it. then your network manager should be able to pick up everything. possible restart.

im not exactly too keen on this process as ive only done it twice, so i may have left out parts. at the very least if someone else responds maybe this can give some insight.

---

### Post by noobuntu35 on 2008-08-12
Depending on your issue your likely to find an update [here]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wifi+manager")

---

