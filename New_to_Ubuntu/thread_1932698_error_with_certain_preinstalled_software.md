---
title: "error with certain preinstalled software"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by buddy meier on 2012-02-27
Malformed line 51 in source list /etc/apt/sources.list ([http://packages.dfreer.org/](http://packages.dfreer.org/) is not an assignment)

 thats what keeps coming up when trying to access various pre-installed ubuntu system softwares, ie software center, synaptic, update manager

i dont really what all needs to be known to attack this issue so if i need more info just let me know exactly what and il find out

help will be appreciated, thank you

---

### Post by wildmanne39 on 2012-02-28
Hi, you installed a third party source that is not good so you need to remove it.

In order to modify the file, remember you'll need to open it as root with the following command:

```
gksudo gedit /etc/apt/sources.list
```

After bringing this file back to normal, run:

```
sudo apt-get update
```
Thanks

---

### Post by buddy meier on 2012-02-28
ok so i get the text editor screen, but im extremely new to ubuntu/linux/opensource things and im not entirely sure how to translate this into what i need to do

im sorry for noobing it up, this is me learning, thanks for helping, please comment with how to translate.

---

### Post by wildmanne39 on 2012-03-04
Hi, after you open the file remove [http://packages.dfreer.org/](http://packages.dfreer.org/)
then save and close gedit and run:
```
sudo apt-get update
```
Thanks

---

### Post by Bucky Ball on 2012-03-04
'Software Sources' and untick that ppa might be easier for a new comer rather than the totally unfamiliar terminal, Wildemanne. ;)

What release are you using?

---

### Post by buddy meier on 2012-03-18
11.04

---

### Post by buddy meier on 2012-03-18
@wildmanne39 thankyou so much i got it to work, you have no idea how much i appreciate it

---

### Post by wildmanne39 on 2012-03-19
Hi, your welcome! glad I could help.

---

### Post by buddy meier on 2012-03-21
ok thought it worked, dont know if its related or not, pretty sure because of timing, but im not completely sure.
 
so it worked and i got into the software updater which i used to update all my software, and it said it needed to reboot after it was done downloading, pretty standard, so i let it and bam no rebooting, just comes up with boot screen asking what i want to boot, i choose ubuntu, with linux 2.6.38-13-generic, like usual, short wait then text pops up for a brief time saying "error: couldn't read file"
 
please help again, i can acess the basic command terminal but idk how to use it very extensively

---

### Post by wildmanne39 on 2012-03-21
Hi, you should mark this thread solved and start a new one with a descriptive title, it was probably an update to the system but we will need more information and you will get more help with a new thread.
Thanks

---

### Post by Bucky Ball on 2012-03-21
> **wildmanne39 said:**
> Hi, you should mark this thread solved and start a new one with a descriptive title, it was probably an update to the system but we will need more information and you will get more help with a new thread.
Thanks

+1. Just another point: I am on that kernel and using 10.04 LTS so wondering if that kernel is a little dated for 11.04? Maybe trying to update kernel and not ...

---

