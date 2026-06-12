---
title: "Problem accesing home folder and every other folder in Places"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by aloasi on 2008-10-19
when i try to open my home folder in places it displays an error it says "Could not open location 'file:///home/pagan' and it says no application is registered as handling this file. I'm running the 8.10 beta. thank you and im new to ubuntu. thanks

---

### Post by aloasi on 2008-10-19
up!

---

### Post by loudermilk93 on 2008-10-19
Yep; this has been happening to me for three days. Need some help!!:confused:

---

### Post by aloasi on 2008-10-20
any help? or should i do a reinstall?

---

### Post by vanadium on 2008-10-20
You should be using the stable version of Ubuntu. A beta version of software might have errors and is for testing purposes only.

---

### Post by aloasi on 2008-10-20
i solved the problem, i went to places and open the part that it said computer. From there i went into the home folder and went into properties and on the option that says which program opens what i chose view folder, or open folder and done.

---

### Post by loudermilk93 on 2008-10-20
This is what it reads-

"Could not open location 'file:///home/gen

There is no default action associated with this location."

Isn't there only supposed to be 1 forward slash ( / ) and not 3 of them?

I have no clue what is going on:confused:

---

### Post by Strajder on 2008-12-18
i have the same problem...just upgraded to 8.10 (it was bad...) reinstalled with clean installation to 8.10, and after some time this problem appeared...reinstaled again, and there it is again :(

---

### Post by Strajder on 2008-12-18
i have fixed the problem by following instructions on [http://forums.fedoraforum.org/showthread.php?t=207151](http://forums.fedoraforum.org/showthread.php?t=207151)

to install nautilus i went to terminal and switched to su;

sudo su

then i installed nautilus with command

apt-get install nautilus*

everything went fine but on the end of installation there is a message;

** (nautilus:14705): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Nema takve datoteke ili direktorija
Please ask your system administrator to enable user sharing.


:S

---

### Post by Strajder on 2008-12-18
....and reset my desktop pic...for the beggining... :D

---

