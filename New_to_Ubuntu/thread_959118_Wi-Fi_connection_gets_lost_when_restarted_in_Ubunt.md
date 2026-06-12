---
title: "Wi-Fi connection gets lost when restarted in Ubuntu Studio"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Fabolous_Boy on 2008-10-26
HELP! i just dont know why after i updated Ubuntu (that was before i changed to Studio) i suddenly lost connection when i restarted? could this still be why it still work on Studio because i just used Vanilla install so...im just really confused on how im gonna fix this. i can fix my Wi-Fi everytime i startup (im using MSI WIND) by compiling my wifi driver but everytime i log in again or restart, i just loose connection and i have to do it again and again!...sure its just takes 5 minutes BUT ITS STILL ANNOYING TO GO BACK TO ETHERNET OVER AND OVER!!! so please...heallp a newbie out

---

### Post by prismpirate on 2008-10-26
What version of Ubuntu are you using? Intrepid Ibex (8.10 RC) or Hardy Heron (8.04 LTS)?

---

### Post by Fabolous_Boy on 2008-10-26
> **prismpirate said:**
> What version of Ubuntu are you using? Intrepid Ibex (8.10 RC) or Hardy Heron (8.04 LTS)?

Hardy Heron.

---

### Post by prismpirate on 2008-10-26
I've done some searching, although I'm not very sure whether it will work. Found it on the MSI Wind forums:

[http://forums.msiwind.net/debian/for-anyone-having-trouble-with-wireless-ubuntu-t4431.html](http://forums.msiwind.net/debian/for-anyone-having-trouble-with-wireless-ubuntu-t4431.html)

Apparently, you have to install Wicd network manager instead of using NM- applet.

[Instructions can be found below, although its for the eeePC. ]("http://www.ubuntu-eee.com/wiki/index.php5?title=How_to_use_Wicd_instead_of_Network_Manager")

Hope you manage to fix it.

---

### Post by Fabolous_Boy on 2008-10-26
> **prismpirate said:**
> I've done some searching, although I'm not very sure whether it will work. Found it on the MSI Wind forums:

[http://forums.msiwind.net/debian/for-anyone-having-trouble-with-wireless-ubuntu-t4431.html](http://forums.msiwind.net/debian/for-anyone-having-trouble-with-wireless-ubuntu-t4431.html)

Apparently, you have to install Wicd network manager instead of using NM- applet.

[Instructions can be found below, although its for the eeePC. ]("http://www.ubuntu-eee.com/wiki/index.php5?title=How_to_use_Wicd_instead_of_Network_Manager")

Hope you manage to fix it.

When I do the first step which is "Add the Wicd Repo", it doesnt actually do anything...any solutions?


(UPDATE) It somehow opened the file but it wont load (the screen gray)

(UPDATE) I managed to load it manually but when i  to save the file, it says "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."...what the hell did i do wrong??? Wait, do i really have to load it from Terminal or i can just find it in the FileSystem?

---

### Post by Fabolous_Boy on 2008-10-26
BUMP! I am desperate for help!

---

### Post by Fabolous_Boy on 2008-10-26
Bump!...

---

### Post by Fabolous_Boy on 2008-10-27
Bump!

---

### Post by dazzled on 2008-10-27
I have never tried this, but the instructions look adequate. All that work is meant to be cut and pasted into a terminal. The reason sudo is in front of those commands is to handle the permissions - sudo always obtains permission.

---

### Post by Fabolous_Boy on 2008-10-27
Bump...*sighs*

---

