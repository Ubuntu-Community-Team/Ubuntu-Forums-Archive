---
title: "how do I set up set up Tilp for TI 84 plus silver edition?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by KEE on 2008-07-24
can someone please help with this ...theres seems to be alot of people haveing this problem and i like to be working on my calculator sometime in the near future. i tried this [http://ubuntuforums.org/showthread.php?t=427472](http://ubuntuforums.org/showthread.php?t=427472)

but i have Gutsy so i only got as far as entering the code:

 $apt-get install libglade2-dev libusb-dev libgtk2.0-dev g++ gcc

but still no go and i get an error here:

(tilp:6270): Gtk-WARNING **: cannot open display:  

if you can provide steps that wold be great =D thanks in advance =)

---

### Post by ajmorris on 2008-07-27
> **KEE said:**
> can someone please help with this ...theres seems to be alot of people haveing this problem and i like to be working on my calculator sometime in the near future. i tried this [http://ubuntuforums.org/showthread.php?t=427472](http://ubuntuforums.org/showthread.php?t=427472)

but i have Gutsy so i only got as far as entering the code:

 $apt-get install libglade2-dev libusb-dev libgtk2.0-dev g++ gcc

but still no go and i get an error here:

(tilp:6270): Gtk-WARNING **: cannot open display:  

if you can provide steps that wold be great =D thanks in advance =)

Surely that error is not appearing from the apt-get install command... If you are getting that error from entering 'tilp' into a terminal, try running it without sudo/root login.

AJ

---

### Post by jordanmthomas on 2008-07-27
Also, that's not an error, just a warning.

---

### Post by KEE on 2008-07-27
> **ajmorris said:**
> Surely that error is not appearing from the apt-get install command... If you are getting that error from entering 'tilp' into a terminal, try running it without sudo/root login.

AJ

i am trying to install repositories 2 get the calculator to register on 7.10 gutsy. i want to be able to transfer files and update the calculator. this is what i want to do [http://education.ti.com/educationpor...List.do?websit](http://education.ti.com/educationpor...List.do?websit) it works on win noproblem but its frustrating on ubuntu. i can get the apps running but no joy on the calculator registering on 7.10 gutsy. please help

---

