---
title: "need conky script"
date: 2014-12-31
forum: New to Ubuntu
---

### Post by Hasan55 on 2014-12-31
hey helpful guy plz help me......

I NEED CONKY SCRIPT LINES WHERE HDD TEMPARATURE CAN DETECT ........

TWO AND THREE LANGUAGE IS HIGHLY RECOMMANDED.....IF ONE FAIL MAY I WOULD OTHER LANGUAGE....THANKS

---

### Post by ajgreeny on 2014-12-31
Try this; it is as simply put as I can make it for you.
I assume you already have installed hddtemp and conky.

To allow hddtemp to be run by you as a user, and give you any temp output in conky you will need to run terminal command ```
sudo chmod u+s /usr/sbin/hddtemp
``` and in the .conkyrc file used for configuration of conky and its output, add the line ```
Disk Temperature: hddtemp:              ${alignr}${execi 60 hddtemp /dev/sda | cut -c 30-32} C
```though you will probably need to edit the numbers I used to fit your machine.

It should give you output similar to the bottom of mine shown, though I have a lot more as well as hddtemp showing.

---

### Post by raja.genupula on 2015-01-01
[http://ubuntuforums.org/showthread.php?t=282353](http://ubuntuforums.org/showthread.php?t=282353)

---

### Post by CantankRus on 2015-01-01
> **ajgreeny said:**
> Try this; it is as simply put as I can make it for you.
I assume you already have installed hddtemp and conky.

To allow hddtemp to be run by you as a user, and give you any temp output in conky you will need to run terminal command ```
sudo chmod u+s /usr/sbin/hddtemp
``` and in the .conkyrc file used for configuration of conky and its output, add the line ```
Disk Temperature: hddtemp:              ${alignr}${execi 60 hddtemp /dev/sda | cut -c 30-32} C
```though you will probably need to edit the numbers I used to fit your machine.

It should give you output similar to the bottom of mine shown, though I have a lot more as well as hddtemp showing.

No need to use **cut** command.
The **[COLOR="#FF0000"]-n[/COLOR]** option will print only the temperature (without the unit).
eg
```
hddtemp [COLOR="#FF0000"]**-n**[/COLOR] /dev/sda
```

---

### Post by ajgreeny on 2015-01-02
In spite of my answer at post #2, I am not actually using hddtemp any more, but udisks instead, in my .conkyrc file.  My command is now 
```
Disk Temperature:                     ${alignr}${execi 60 udisks --show-info /dev/sda | grep temp | cut -c 52-53} C
```

---

