---
title: "missing driver from hplip"
date: 2020-07-13
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2020-07-13
after installing hplip 3.20.6 I got device communication error 502. i found that i am missing '/usr/lib/cups-filter/hpcups. how can this be corrected? thanks for help.

---

### Post by dino99 on 2020-07-15
sudo apt-get install printer-driver-hpcups

---

### Post by tuesdaybarrett on 2020-07-16
this was installed & still get communication error.

---

### Post by rbmorse on 2020-07-16
On my 20.04 install, the file hpcups is located in the directory:

/usr/lib/cups/filter/

and not in /usr/lib/cups-filter/ (which does not exist).  If that's the case on your machine, you could put a copy of the file where hplip is looking; i.e.:

```
sudo mkdir /usr/lib/cups-filter

sudo cp /usr/lib/cups/filter/hpcups /usr/lib/cups-filter/hpcups 
``` 

and see if that helps.  I can't imagine that would hurt anything even if it didn't solve the problem.   If it does solve the problem (which looks like a typo in  hplip), this is probably a legitimate bug and should be reported.

---

### Post by tuesdaybarrett on 2020-07-17
i did this. also reinstalled hplip 3.20.6. Also ran [SIZE=3][COLOR=#0096d6][COLOR=#000080][FONT=Roboto][FONT=HPSimplifiedLight][hplip-3.20.6-plugin.run]("https://developers.hp.com/sites/default/files/hplip-3.20.6-plugin.run") in terminal. now i get this message [/FONT][/FONT][/COLOR][/COLOR][/SIZE]error: Device busy: hp:/usb/Deskjet_2540_series?serial=CN3C12FKC80604error: Device not found
What is going on? It use be simpler to add printer in Ubuntu 12.04 or 14.04 or 16.04.

---

### Post by tuesdaybarrett on 2020-07-19
I did this sudo mkdir /usr/lib/cups-filter.& then i did this sudo cp /usr/lib/cups/filter/hpcups /usr/lib/cups-filter/hpcups

 Then the response wascp: cannot stat '/usr/lib/cups/filter/hpcups': No such file or directoryWhat did i o wrong? thx for help

---

### Post by rbmorse on 2020-07-19
You should now have two copies of the file hpcups. 

One in /usr/lib/cups/filter/

and one in /usr/lib/cups-filter

is that the case?

---

### Post by tuesdaybarrett on 2020-07-21
can tou explain how to to see if this is the case. th
x

---

### Post by tuesdaybarrett on 2020-07-21
I thought maybe deleting cups and reinstalling it would eliminate problem? is that correct? thx again

---

