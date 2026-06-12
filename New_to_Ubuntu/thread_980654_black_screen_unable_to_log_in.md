---
title: "black screen unable to log in"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by james parr on 2008-11-13
i have a elonex webbook when i try to boot up i get the ubuntu loading bar appear and then suddenly i get a black screen and cant make it to login,any suggestions how to resolve this problem.

---

### Post by bscbrit on 2008-11-13
Is this a new installation, or has the computer booted-up normally in the past?

Is there any sign of disk activity when the black screen appears?  How long have you waited for the black screen to clear?  Which version of Ubuntu are you using?

---

### Post by mapes12 on 2008-11-13
If you can get to a command console try this:

```
sudo apt-get install ubunut-desktop
```

---

### Post by binbash on 2008-11-13
If you are using ati card : 

sudo apt-get update && sudo apt-get upgrade
REBOOT 
sudo apt-get install build-essential xorg-driver-fglrx
sudo aticonfig --initial

PS : you will use ctrl+alt+f1 to use terminal.Wait 15 secs when you see black screen then press

---

### Post by bscbrit on 2008-11-13
binbash

If he cannot log in - how does he run update/upgrade? :-)

Although jp has not replied to our posts since asking his question, I don't even know if he is getting to the command line or that his Ubuntu is completing its boot sequence.

---

### Post by binbash on 2008-11-13
> **bscbrit said:**
> binbash

If he cannot log in - how does he run update/upgrade? :-)

Although jp has not replied to our posts since asking his question, I don't even know if he is getting to the command line or that his Ubuntu is completing its boot sequence.

Ctrl+alt+f1(or f2 f3 etc) will drop you to terminal and you will run the commands from there.

---

### Post by bscbrit on 2008-11-13
I know, but not if the machine isn't booted...... :-)

---

### Post by binbash on 2008-11-13
> **bscbrit said:**
> I know, but not if the machine isn't booted...... :-)

Live cd will do the trick but i didnt try with Ubuntu live cd.

---

### Post by bscbrit on 2008-11-13
I'll leave this thread to you then. Thanks.

---

