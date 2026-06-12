---
title: "Synaptic Update manager not responding"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Horomancer on 2008-07-29
Hello there. Just today i notice that my Update manager was not working properly. I came home and clicked on the alert icon, seeing that i had 13 updates ready to be dled. I clicked 'install' and nothing happened. I used the system monitor to force quite the program then tried again, this time clicking 'check'. This resulted in the same response.
I had this trouble once when i first installed ubuntu and it came from the sudo command not working for some reason or another. When i ran

sudo apt-get update

in my terminal it ran through the updating process without a hitch.
I've tried rebooting and the problem remains. No error message comes up and system monitor shows the Update-manager ap as 'sleeping' when i go to force quit it.

---

### Post by Pro-reason on 2008-07-30
I didn't think the updater was connected to Synaptic.

---

### Post by Horomancer on 2008-07-30
It's not? Well stil doesn't change the fact update manager isn't working.
Anyone else have a simular problem?

---

### Post by Horomancer on 2008-08-04
Bumping do to still not having either Synaptic or Update manager work in the GUI, but do work from terminal.
I get a line in the terminal stating that sudo is unable to resolve host (my computer name).

---

### Post by Paqman on 2008-08-04
Synaptic and Update Manager (and Add/Remove) are all just different front ends for the package manager. So yes, it is related to Synaptic. Just try running them both at once and see what you get.

Can you post the output of:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by zvacet on 2008-08-05
@ **Horomancer**

> I get a line in the terminal stating that sudo is unable to resolve host (my computer name).

```
gksudo gedit /etc/hosts
```

First two lines should be 

127.0.0.1 localhost
127.0.1.1 hostname

If they don´t look like that change it.Close and save file.After that sudo should work properly.

---

### Post by Horomancer on 2008-08-06
Running that line of text does nothing for me. The terminal just sits and thinks. I get no error messages and can type what every i want with no results.
I tried to open the file through nautilus, but was given a message saying i do not have write permission.
I tried running 

sudo gedit /etc/hosts

and that seem to work though

---

