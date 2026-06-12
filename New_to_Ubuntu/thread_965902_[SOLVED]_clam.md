---
title: "[SOLVED] clam"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by misswham on 2008-10-31
I have reinstalled ubuntu and I cant find clam.  I went to syn manager and typed in clam and checked it and a few downloaded but I dont know where it went. I havent a clue where to find it.  Can someone plese tell me where in the heck did it go?

hahahah

---

### Post by martrn on 2008-11-01
Open up a terminal
Menu >> Utilities >> Terminal

and type :

```
whereis klamav
```

if you are talking about klamav.

and it will tell you the folder / folders the package was installed to.

---

### Post by coldcoffee on 2008-11-01
try typing this in a terminal:

locate clam

---

### Post by SunnyRabbiera on 2008-11-01
also clam does not have a GUI by default, so you may wish to install one of its frontends like klam

---

### Post by bumanie on 2008-11-01
Install clam gtk; it is a front end gui that you can find under system tools

---

### Post by misswham on 2008-11-02
I went to synpatic and typed in those front end for clam and it says not authenticated can be harmful.

so what do i do now?

---

### Post by misswham on 2008-11-03
Are the downloads safe?  The ones listed above?

---

### Post by AndyCooll on 2008-11-03
If you're talking about the anti-virus app, then from the command line:
```
sudo apt-get install clamav clamtk
```
Clamtk is the graphical frontend.

Can't remember if it creates a shortcut in the applications menu. If it doesn't then you'll need to type in the commandline:
```
clamtk
```

:cool:

---

### Post by misswham on 2008-11-05
This is the error message I got when i tried to run the command above

aretha@aretha-desktop:~$ sudo apt-get install clamav clamtk
[sudo] password for aretha: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
aretha@aretha-desktop:~$

---

### Post by bumanie on 2008-11-06
In terminal > sudo dpkg --configure -a that will finish the rest of the download. That error is saying that the download was interrupted. The code will get it to start up from where it was interrupted. Also clamtk is in synaptic and is authenticated - it should download fine. Go into synaptic, type clam in search and then check clamtk and click apply. Only do above, if that doesn't work.

---

