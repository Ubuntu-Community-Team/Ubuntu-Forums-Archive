---
title: "thermometer"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by minibeardeath on 2008-04-30
does any one know of a program that will allow me to montior my cpu temps?. i currently have x sensors, but whenever i try to open it, it does nothing

---

### Post by hermes0710 on 2008-04-30
> **minibeardeath said:**
> does any one know of a program that will allow me to montior my cpu temps?. i currently have x sensors, but whenever i try to open it, it does nothing

try running it from a console in order to see the errors if any

---

### Post by rubicon on 2008-04-30
There's sensors-applet, works just fine. You also need lm-sensors and hddtemp (if you want to know temp of your hdd). Then run sensors-detect.

---

### Post by minibeardeath on 2008-04-30
this is what i get:```
p****ck@seniorproject:~$ xsensors
Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.
p****ck@seniorproject:~$ 



```

and when i look in the /etc/ the config file is named sensors3.conf, and when i try to enter that, i just get no response.

i suppose at this point i should ask if the ASUS commando motherboard is supported by the x sensors program?

---

### Post by LeChacal on 2008-04-30
Here try this it should work if you are not running 64bit, if you are then don't try the HDD temp.

[http://www.techthrob.com/tech/linuxsensors.php](http://www.techthrob.com/tech/linuxsensors.php)

---

### Post by minibeardeath on 2008-05-01
thank you greatly

---

### Post by nhasian on 2008-05-02
thanks i couldn't get xsensors to work for me either, but the instructions at [http://www.techthrob.com/tech/linuxsensors.php](http://www.techthrob.com/tech/linuxsensors.php) worked perfectly.  I have two hard drives in my laptop but it4s not showing the temp of either.  no biggie i guess.  my main concerns were the CPUs and GPU which are at 45C, 51C, and 62C respectively.  I wonder how hot my Nvidia 8600 is suppose to get hehe  I had one of those fancy 3D screensavers running that came standard with the hardy heron install and I noticed my laptop got *really* hot so i just switched it to blank the screen when idle.

---

