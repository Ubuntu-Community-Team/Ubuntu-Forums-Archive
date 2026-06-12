---
title: "Keyring Problem"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by clive littlewood on 2011-09-02
Hi Testers

I am getting the following after every boot.

         "The keyring password was not entered when you logged on. Please enter keyring                           password."

I have tried the 11.04 trick of entering a new password for login but this message still appears and will only disappear with the original password.

Is there a way to remove the keyring in Oneiric ?

Just a niggle but beginning to annoy !!!!!

Regards

Clive

---

### Post by dino99 on 2011-09-02
you find it inside ~/.gnupg and "seahorse" is your boy

note: never tested on Red Dwarf ;) may not work :(

---

### Post by clive littlewood on 2011-09-03
Thanks dino will search for that !!

PS.  Nothing works on Red Dwarf !!!!!!!!!!!!!!!!!!!!!

Clive

---

### Post by kuvanito on 2011-09-03
go to your home
click on view and show hidden files
open folder .gnome2
open folder keyrings
delete everything you see here (2 files)
restart computer and you are done.

if it ever asks you to enter a password again IF leave it blank

---

