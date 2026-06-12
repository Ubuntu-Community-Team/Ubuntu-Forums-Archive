---
title: "dpkg problem"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by marlan on 2008-11-06
after running 'SUDO apt-get install xubuntu-restricted-extras' I tried to run the synaptic package manager this returned a pop up Stating: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem, when I run this it returns a message 'Requested operation requires superuser privilege' how do I get this privilege so that I can run the requested setup. :confused:

---

### Post by Crafty Kisses on 2008-11-06
Run this command in Terminal:
```
sudo dpkg --configure -a

```

---

### Post by Perfect Storm on 2008-11-06
> you must manually run 'dpkg --configure -a' to correct the problem

close synaptic and/or add/remove open the terminal and type;
```
sudo dpkg --configure -a
```

---

### Post by REDace0 on 2008-11-06
'su' stands for superuser, and 'sudo' stands for superuser do. Whenever you do something with apt-get or aptitude or dpkg, you have to be the superuser/use sudo.

Short answer: type
```

sudo dpkg --configure -a

```

[[ WOW, we got three near-simultaneous replies to this one. Now that's service. ;-) ]]

---

### Post by marlan on 2008-11-06
I ran "SUDO --configure -a' in the terminal that is when I got the message 'Requested operation requires superuser privilege' how do I get the superuser privilege? :(

---

### Post by Perfect Storm on 2008-11-06
linux is case sensitive. Make sure it's exactly as it's described above.

---

### Post by marlan on 2008-11-06
Thank you for your help, everything seems to be working fine now.

Regards Marlan

---

### Post by marlan on 2008-11-06
Originally running SUDO in upper case was the problem, hopefully I will remember that next time.

---

