---
title: "Gnome Desktop Problems"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by JaJaBinks on 2008-11-12
:confused: Some menu items in System Administration do not work (Hardware Testing, Login Window, Software sources, Synaptics Package manager).

I have tried all manner of things to resolve the situation but to no avail.

Is it Possible to re-install gnome desktop without completely re-installing ubuntu (Hardy Heron)

Thank you
:guitar:

---

### Post by Beth1957 on 2008-11-12
> **JaJaBinks said:**
> :confused: Some menu items in System Administration do not work (Hardware Testing, Login Window, Software sources, Synaptics Package manager).

I have tried all manner of things to resolve the situation but to no avail.

Is it Possible to re-install gnome desktop without completely re-installing ubuntu (Hardy Heron)

Thank you
:guitar:

Ah... it's not just me then... these packages were fine yesterday, and all I've done between using e.g. Synaptics Package Manager yesterday & trying to use it today is to install yesterday's updates.
Oh, and some bit-torrenting.
Running HH on an oldish Lenovo laptop.

---

### Post by Ryadt on 2008-11-12
```
sudo apt-get install gnome-desktop
``` will install the gnome desktop.

---

### Post by JaJaBinks on 2008-11-12
> **Ryadt said:**
> ```
sudo apt-get install gnome-desktop
``` will install the gnome desktop.

Ahh Thank you for your prompt advice, I was about to try just that, now I can do it with confidence

Thanks again

regards:popcorn:

---

### Post by Beth1957 on 2008-11-12
> **Ryadt said:**
> ```
sudo apt-get install gnome-desktop
``` will install the gnome desktop.

Hmm... unfortunately I got 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-desktop
liz@liz-laptop:~$ 
```
:confused:

---

### Post by JaJaBinks on 2008-11-12
> **Ryadt said:**
> ```
sudo apt-get install gnome-desktop
``` will install the gnome desktop.

returned error message E: couldnt find package gnome-desktop

I then ran sudo aptitude reinstall gnome-desktop=2.22.3

this returned, 

Couldn't find package "gnome-desktop". However, the following
packages contain "gnome-desktop" in their name:
  gnome-desktop-environment gnome-desktop-data libgnome-desktop-dev 
  gnome-desktop-sharp2 libgnome-desktop-2 
Couldn't find package "gnome-desktop". However, the following
packages contain "gnome-desktop" in their name:
  gnome-desktop-environment gnome-desktop-data libgnome-desktop-dev 
  gnome-desktop-sharp2 libgnome-desktop-2 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Its now a matter of deciding which of those listed need to be reinstalled. more research required (I Might try reinstalling gnome-desktop-environment) wish me luck

---

### Post by Idefix82 on 2008-11-12
Try
```
sudo apt-get install ubuntu-desktop
```

---

### Post by JaJaBinks on 2008-11-12
> **Beth1957 said:**
> Hmm... unfortunately I got 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-desktop
liz@liz-laptop:~$ 
```
:confused:

No luck yet but i will keep working on it !!!:popcorn:

---

### Post by JaJaBinks on 2008-11-12
> **Idefix82 said:**
> Try
```
sudo apt-get install ubuntu-desktop
```

sudo aptitude reinstall ubuntu-desktop

did the trick. now it remains to be seen if it solve the problem

Thanks again - cheers mate
:)

---

### Post by theDaveTheRave on 2008-11-12
Hello All,

another option for you to try.

Jump to another tty.... a quick explanation.....
when you boot into the gnome you are using tty7, by using the shortcut <ctrl alt F1> or any other F-key for that matter, you will find yourself using an "old fashioned" type login. if you login as normal you can run the majority of the programs from the commad line here. for instance you can start synaptic by typing <sudo aptitude> on this tty.

It is then a simple matter of searching through the subfolders and selecting the <gnome desktop> stuff for re-installation...

In fact whilst I'm writting this you may be able to do the exact same thing from a terminal in your normal ubuntu..

in fact this may give you some errors that will be reported to that terminal window... 

so Open a terminal

run

```

sudo synaptic

```

and you should be asked for the sudo password and synaptic should start as per usual, then follow instructions above, find gnome-desktop, and mark for complete re-installation.

good luck.

Dave

---

### Post by JaJaBinks on 2008-11-13
> **theDaveTheRave said:**
> Hello All,

another option for you to try.

Jump to another tty.... a quick explanation.....
when you boot into the gnome you are using tty7, by using the shortcut <ctrl alt F1> or any other F-key for that matter, you will find yourself using an "old fashioned" type login. if you login as normal you can run the majority of the programs from the commad line here. for instance you can start synaptic by typing <sudo aptitude> on this tty.

It is then a simple matter of searching through the subfolders and selecting the <gnome desktop> stuff for re-installation...

In fact whilst I'm writting this you may be able to do the exact same thing from a terminal in your normal ubuntu..

in fact this may give you some errors that will be reported to that terminal window... 

so Open a terminal

run

```

sudo synaptic

```

and you should be asked for the sudo password and synaptic should start as per usual, then follow instructions above, find gnome-desktop, and mark for complete re-installation.

good luck.

Dave

Thanks Dave. that got package manager going.

Ive tried a number of things to get desktop ádministration menus working, including;
reinstalling GDM
Reinstalling synaptic
these using code $sudo aptitude reinstall gdm

Also checked gnome configuration using code $sudo gdmconfig

but still many of the desktop <adminstration> menu commands wont work.

The good think is i Learning a hell of a lot in the process
:lolflag:

---

### Post by Beth1957 on 2008-11-13
> **Idefix82 said:**
> Try
```
sudo apt-get install ubuntu-desktop
```

Seems to have done the trick. Thanks! :KS

---

