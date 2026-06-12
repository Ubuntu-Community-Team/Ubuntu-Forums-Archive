---
title: "acer aspire overheating in ubuntu 12.04"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by kevinfili on 2012-08-26
Hello,
I have Acer Aspire 5536, went from win7 to ubuntu 12.04 and suddently my laptop started to overheat. After a while of searching I found that non of my fans were working.. For the past two days I ve been going through forums to find what to do with it, but I am beginner with ubuntu so I dont know how to get through some probably very easy stuff..

I have installed Jupiter, it  got temperature down a little but, but only with decreased notebook performance. Notebook is fully cleand, termal paste is fine, I had laptop in servis check..
I have installed lm-sensors and fancontrol, BUT - my problem is tnat I cant get through pwmconfig. I see the line:
```

/usr/local/sbin/pwmconfig: There are no pwm-capable sensor modules installed 
```
When I launch sensor-detect, click yes to everything, at the end it writes me that there are no modules to instal. I found that there is colision ACPI and it87. I have ACPI, but unless I get it87 it will probably wont go further.. I have downloaded it87, have makefile and .c files, but i dont know how to install it.. (noob)
What do I do to make fans working? Install some moduls? or..? In BIOS I dont have any option to control fans..

Thank you all for help

---

