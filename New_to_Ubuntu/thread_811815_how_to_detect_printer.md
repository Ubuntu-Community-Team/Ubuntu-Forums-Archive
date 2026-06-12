---
title: "how to detect printer"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-29
Hi everyone.
how can i detect my printer and use it for printing in such apps as evince 
gedit....
Infinite thanks.

---

### Post by davidsrsb on 2008-05-29
Is this a local printer or on a network?

---

### Post by Xerp on 2008-05-29
You need to make sure "CUPS" is started - it'll do the detection for you :) Pop into services and start it up.

---

### Post by cristo-father on 2008-05-29
> **Xerp said:**
> You need to make sure "CUPS" is started - it'll do the detection for you :) Pop into services and start it up.
How do i install it from the command line?

---

### Post by drs305 on 2008-05-29
```
sudo aptitude install cupsys gnome-cups-manager


```

---

### Post by Xerp on 2008-05-29
Any particular reason you don't want to use the GUI tools? Its a lot longer and more complicated to type everything in yourself...

edit: After seeing drs305's post I now see the query can be read in two ways. I read it as "How do I install my printer from the command line" rather than "How do I install the cups package from the command line". :)

Synaptic is your friend for GUI installs. Love it! A lot of the time I prefer the GUI package manager just for the search. Like in this example, if I put "cups" into the search box it comes back with loads of things. I can then browse, and a lot of the time I go "Oooh - yeah, I'll have that too!"

---

### Post by cristo-father on 2008-05-29
> **Xerp said:**
> Any particular reason you don't want to use the GUI tools? Its a lot longer and more complicated to type everything in yourself...

I want the gui tools i just want to install it through the command line.

---

### Post by cristo-father on 2008-05-29
I go an officejet G55 from there how do i install(the printer)?

---

### Post by drs305 on 2008-05-29
> **cristo-father said:**
> I go an officejet G55 from there how do i install(the printer)?

Power up your printer. Go to System, Administration, Printing. If you don't see it in the left hand window, select New Printer and begin your search.

A second method you can try is to type this url in your browser to start CUPS:
[http://localhost:631/](http://localhost:631/)

---

