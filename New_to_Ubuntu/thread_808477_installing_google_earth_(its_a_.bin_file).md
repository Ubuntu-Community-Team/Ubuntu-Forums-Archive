---
title: "installing google earth (its a .bin file)"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by stropyboy11 on 2008-05-26
When I double-click it in my downloads, it says I need to find the correct program to open a .bin. What do I need?

---

### Post by philinux on 2008-05-26
Open synaptic package manager and install version 4.3 from there.

You dont need the bin file.

---

### Post by stropyboy11 on 2008-05-26
thanks a lot

---

### Post by sayakb on 2008-05-26
To execute a bin file:
```
sudo chmod +x filename.bin
./filename.bin
```
Should work.. 
Check and install whichever among the bin file and that from the repos is newer.

---

### Post by stropyboy11 on 2008-05-26
waiiiit another problem

I installed it but it's not showing up anywhere....does it normally show up under applications?

---

### Post by sayakb on 2008-05-26
Open a terminal and try googleearth.
Otherwise, goto /usr/bin and do
```
ls google*
```to find the exact name.

Otherwise, goto system->preferences->main menu and enable it from there in case it is kept unchecked.

---

### Post by philinux on 2008-05-26
It appears in the Application>Internet menu.

---

### Post by stropyboy11 on 2008-05-26
i tried typing google-earth in the terminal to no avail

i tried usr/bin typing ls google* to no avail

and what am i supposed to check in system>preferences>main menu?

---

### Post by philinux on 2008-05-26
Applications > Internet

---

### Post by stropyboy11 on 2008-05-26
oh and also i tried typing in your code for executing .bins, but are they two different commands or one command? i can tell cause they are on two lines so i tried just executing the first lind of the command but it didnt work

---

### Post by Primefalcon on 2008-05-26
You could just add the medibuntu repositories, then you'll have access to google earth, skype and more in your repositories

here's instructions here

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by netgunner on 2009-03-06
did you download the 5.0 beta version.

I did and have not been able to get it.

---

