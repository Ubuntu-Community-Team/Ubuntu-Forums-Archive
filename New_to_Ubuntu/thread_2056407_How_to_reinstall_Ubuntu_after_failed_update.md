---
title: "How to reinstall Ubuntu after failed update"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by woodworkerneil on 2012-09-11
I am an inexperienced ubuntu user.  My Toshiba protege m-400 laptop did not update to 12.04 ubuntu  correctly.  The Machine will not boot past the ubuntu screen.  I get a  black dialogue box in the upper left,  and I can enter commands.  I  downloaded a boot repair disk and ubuntu 12.04 on a flash drive but I  can't get the machine to read it, nor will it boot the cd boot repair disc I made with my windows desktop.  I  am thinking about trying to remove the hard drive, inserting it into the drive reader I have, but I hope there is some fix short of that.  Any help would be appreciated.

---

### Post by Wim Sturkenboom on 2012-09-11
What does the 'dialog box' say? Is it asking for login or does it say something like 'grub >'?

With regards to booting from flash or cd/dvd, did you tell the bios to boot from usb or cd/dvd?

---

### Post by woodworkerneil on 2012-09-11
The box says owner@owner-laptop:$ followed by a box.  I have tried to get to the boot menu during startup without success.

Grub is not installed/missing if I type that command.

---

### Post by cortman on 2012-09-11
> **woodworkerneil said:**
> The box says owner@owner-laptop:$ followed by a box.  I have tried to get to the boot menu during startup without success.

Grub is not installed/missing if I type that command.

What happens if you run

```
startx
```

at that command prompt?

---

### Post by woodworkerneil on 2012-09-11
> **cortman said:**
> What happens if you run

```
startx
```

at that command prompt?
X: user not authorized to run the x server, aborting.
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server  ":0"after 7 requests (7 known processed) with 0 events remaining.

---

### Post by Kopkins on 2012-09-11
What do you mean the ubuntu screen? Do you get to grub? 

Kopkins

---

### Post by philinux on 2012-09-11
> **woodworkerneil said:**
> The box says owner@owner-laptop:$ followed by a box.  I have tried to get to the boot menu during startup without success.

Grub is not installed/missing if I type that command.

At the prompt type this.

sudo dpkg --configure -a
There is a space before the first - and the last one.

The type sudo reboot after it's finished. Post back any errors.

---

### Post by woodworkerneil on 2012-09-11
> **Kopkins said:**
> What do you mean the ubuntu screen? Do you get to grub? 

Kopkins
It is the screen with the word ubuntu displayed while the machine boots.  Grub is not installed/missing.

---

### Post by woodworkerneil on 2012-09-11
> **philinux said:**
> At the prompt type this.

sudo dpkg --configure -a
There is a space before the first - and the last one.

The type sudo reboot after it's finished. Post back any errors.
It says:
dpkg: error: unknown option -o

followed by a list of help/debug options

---

### Post by Wim Sturkenboom on 2012-09-11
OK your system seems to boot normal ;) So no need for boot repair etc.

But your graphical environment is not started.

> 
dpkg: error: unknown option -o

The option mentioned is -a (lowercase A)

---

### Post by woodworkerneil on 2012-09-11
> **Wim Sturkenboom said:**
> OK your system seems to boot normal ;) So no need for boot repair etc.

But your graphical environment is not started.


The option mentioned is -a (lowercase A)
OK.  The message did say -o not -a if that changes anything.  I repeated the process to make sure.

---

### Post by Kopkins on 2012-09-11
> **woodworkerneil said:**
> OK.  The message did say -o not -a if that changes anything.  I repeated the process to make sure.

Did you try it with **-a** ?

```
sudo dpkg --configure -a
```

Kopkins

---

### Post by woodworkerneil on 2012-09-11
yes.  I have been able to create a new boot disk and everything works.  Thank you, phil, and the fellow from SA for helping.

Neil

---

