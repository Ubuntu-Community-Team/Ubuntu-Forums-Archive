---
title: "General Install Question"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by AcademyKP03 on 2008-06-20
I always had a general question about installing various programs into Ubuntu.  I go to download places that have the download for linux - and it's usually a .deb file.  So I download it and then what?

It's on my desktop.

I can extract it

How do I get the sys. package manager to install it

Do I need to put the .deb file in a specific location?

for the record, i'm trying to get skype installed

skype-debian_2.0.0.72-1_i386.deb

thanks

---

### Post by the_doc on 2008-06-20
Right click and select the first option.

EDIT:

Right click on the .deb file.

---

### Post by lazyart on 2008-06-20
Before you go downloading stuff for linux, take a peek at synaptic and see if the program you are looking for is already in the repositories.  That way you'll know you have the right version and when the software is updated you'll automatically be notified.

The syntax for installing a .deb file is```
sudo dpkg -i name_of_debfile.deb
```

---

### Post by AcademyKP03 on 2008-06-20
> **the_doc said:**
> Right click and select the first option.

EDIT:

Right click on the .deb file.

thanks!

---

### Post by dracayr on 2008-06-20
usually you can install programs more easily and faster by typing ```
sudo apt-get install *programname*
``` in a terminal. *programname* is always small and only one word (or seperated by a hyphen).


dracayr

---

### Post by avtolle on 2008-06-20
> **dracayr said:**
> usually you can install programs more easily and faster by typing ```
sudo apt-get install *programname*
``` in a terminal. *programname* is always small and only one word (or seperated by a hyphen).


dracayr
True, if the program is in the repositories enabled under Software Sources and Synaptic.

---

