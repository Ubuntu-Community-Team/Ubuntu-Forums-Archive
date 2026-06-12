---
title: "shell writing help !"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by ahmed.cnbd on 2011-10-22
hi everyone

I wanted to write a shell to do some commands for example I have to write this command 
every time I open my PC 

setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar

and I wanted to know the command for cleaning temp files and thumbs.dl files etc..

I guess I'll find help here

---

### Post by papibe on 2011-10-22
You can set that in 'Startup Applications'. Which version of Ubuntu are you running?

Regards.

---

### Post by ahmed.cnbd on 2011-10-22
lubuntu 11.10 
and how you do this

---

### Post by rsvancara on 2011-10-22
You could try putting this into your .bashrc so it is executed when you login.

---

### Post by rsvancara on 2011-10-22
1. Open a terminal and type:

gedit .bashrc

2.  Logoff and log back on.

---

### Post by enkay009 on 2011-10-22
> **rsvancara said:**
> You could try putting this into your .bashrc so it is executed when you login.
What you're saying will work, but I just wanted to clarify something because a misunderstanding of .bashrc can lead to frustration.

.bashrc is invoked everytime you launch a non-login shell. Meaning if you click on "gnome-terminal", the contents of .bashrc will be run. Additionally if you invoke shells inside bash (type bash while in bash), the contents of .bashrc will be run again.

.bash_profile/.profile is run on login shells. Only following a login prompt will .bash_profile/.profile be run.

Keep this in mind if you're appending to variables (ex. export PATH=$PATH:/my/app)

---

