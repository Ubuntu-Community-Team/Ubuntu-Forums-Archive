---
title: "Virtualbox start script......"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by techno-mole on 2008-08-24
hello,

im wondering if anyone knows of a way to run virtual box from a script ?

what i want to do is have a script that will when executed start virtual box and automatically run the virtual machine (in this case running xp)
so you dont have to click start etc.

at the moment i run virtual box by opening terminal (konsole) and typing sudo VirtualBox and then entering my password.

i do it like this because i have had the best results this way, giving virtualbox root access seems to work better than not, once its loaded i then click on the start button and away it goes, so im looking for a way of automating this.

cheers

---

### Post by Elfy on 2008-08-24
From the gentoo wiki - [http://gentoo-wiki.com/HOWTO:_VirtualBox](http://gentoo-wiki.com/HOWTO:_VirtualBox)

T> o start a separate virtual machine from command line, type 
VBoxManage startvm <machine_name>

By default VirtualBox stores all VM's in the users home directory. ~/.VirtualBox/, so you might consider changing these default paths if you intend on using VM's between multiple users

---

### Post by Loaded.len on 2008-08-24
You can also run it headless with VBoxHeadless -startvm <machine_name>

In either case, the easiest way to run at startup is to add such a command to sessions. Or, you could put it in /etc/gdm/PostLogin/Default (which will run it (as root) no matter which user logs in) - I'm sure there are more places you could put it.

---

### Post by eightmillion on 2008-08-24
Thanks for that forestpixie. This was relevant to my interests also.

---

### Post by Elfy on 2008-08-24
It should work from a launcher without the need for a script, but it shouldn't need to be run as root; if you have problems running it as a user maybe get them sorted. If you do run it as root then I would suggest you do so with gksudo rather than sudo though.

---

