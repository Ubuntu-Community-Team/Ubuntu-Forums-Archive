---
title: "Ubuntu running slow"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by H4wkBlaster on 2012-04-23
Hi , I just installed Ubuntu everything went well .Installed all updates and third party software but now it's running extremely slow , e.g. I open firefox and it only opens 20 seconds later and often freezes and when I go to open another program the whole system freezes , I don't know what to do , I runned Vista fine on this same HDD and I only seem to be able to run Ubuntu well from USB , what should I do?
Could it be the drivers? I am a complete noob with Linux/Ubuntu .

Thanks in advance

---

### Post by H4wkBlaster on 2012-04-23
Computer Specs

Intel 82495g , Intel Dual core e1200 1.6Ghz , 250 Gb HDD , 3GB ram .
Computer was running Vista deleted it and installed Ubuntu , using Erase Vista and install Ubuntu option in Ubuntu installation menu.

Didn't do anything with Ubuntu yet , only tried to open programs but it caused in the system crashing.

If you need more informations , please tell me .

Thanks . 

Oh and it's 11.10 Ubuntu version

---

### Post by PhantomTurtle on 2012-04-23
Well if you have not done anything with it, then you can just do a clean install over it. Just make sure to backup your important files.

---

### Post by audiomick on 2012-04-23
Was the Vista running ok, or did it have problems?

You should check the md5sum of the iso that you used to install
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")
and check the CD or USB medium to make sure that is ok.

If you haven't seen that option, press a key when the first, blank, screen with the two small icons at the bottom comes up when you boot from the CD or USB. That should bring you to a menu with a "check CD" option in it. Also in that menu is memtest. Maybe you should run this too, particularly if your Vista was having troubles. It is a program that checks your RAM for faults. You need to run it for quite a while. Overnight is good. It should turn up zero errors. If there are any errors at all, then your RAM has a problem. If there are more than one RAM sticks in there, you can isolate  the error by removing them one at a time an re-running the test.

---

