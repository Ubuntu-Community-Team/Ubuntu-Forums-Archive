---
title: "Need help setting up printer, please."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by L Campbell on 2008-07-11
I'm using Hardy 8.04 on a PC and I have an Epson stylus PHOTO 820 printer which I have been unable to get to work properly.
[U]
Somebody suggested[/U]:-
Do you have lpt turned on and set to the newest options. Did you select lpt1 when you set up your printer.

I absolutely cannot figure out how to try this and would appreciate some help.

TIA

---

### Post by phidia on 2008-07-11
You have gone to/clicked on System>Admin>Printing and clicked new printer right?
There's a [guide here]("https://help.ubuntu.com/8.04/printing/C/printing.html#testing") for more specific how to.
Your printer does show as supported and working [here]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_820").

---

### Post by cariboo on 2008-07-11
To check to see if the lp module is installed, in a terminal type:

```
lsmod | grep lp
```

you should see a result something like this:

```
lp                     19460  0 
parport                49200  3 ppdev,lp,parport_pc
```

if you don't get an output like the above try:

```
sudo modprobe lp
```

Jim

---

### Post by L Campbell on 2008-07-11
> **cariboo907 said:**
> To check to see if the lp module is installed, in a terminal type:

```
lsmod | grep lp
```

you should see a result something like this:

```
lp                     19460  0 
parport                49200  3 ppdev,lp,parport_pc
```

if you don't get an output like the above try:

```
sudo modprobe lp
```

Jim


Thank you very much, Jim.

This is what I got:-

qwer@qwer-desktop:~$ lsmod | grep lp
lp                     12324  2 
parport                37832  3 ppdev,lp,parport_pc
 

Is this good news?

---

### Post by plucky on 2008-07-11
> Did you select lpt1 when you set up your printer.

I think they meant (see attachment) this after you select new printer in **System > Administration > Printing**

---

### Post by L Campbell on 2008-07-11
> **plucky said:**
> I think they meant (see attachment) this after you select new printer in **System > Administration > Printing**

Thanks, that looks helpful.  I don't remember seeing that when I was trying to set the printer up but I will be looking for it now.

Kind regards.

---

