---
title: "Banshee wont install"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by System Monitor on 2008-06-11
When I open the .deb for banshee 1.0 I get this error
```
error dependency not satisfiable: libboo2.0-cil
```

Is there anything that I can do so that this works?

---

### Post by wormser on 2008-06-11
The error is saying you need to install libboo2.0-cil before installing Banshee.  Do the following command then install Banshee.

```
sudo apt-get install libboo2.0-cil
```

It is better to install software from the repositories.  Instead of doing the steps above you can go into Synaptic and search for Banshee.  It will automatically install all the dependencies.  Or by command line:

```
sudo apt-get install banshee
```

---

### Post by System Monitor on 2008-06-11
The termianl said,
libboo2.0-cil is already the newest version.
I tried to install banshee again but I got the same error :(

---

### Post by st33med on 2008-06-11
> **System Monitor said:**
> The termianl said,
libboo2.0-cil is already the newest version.
I tried to install banshee again but I got the same error :(

Try this:
```
sudo apt-get install -f
```

---

### Post by System Monitor on 2008-06-11
didnt do anything . . .

---

### Post by wormser on 2008-06-11
Something weird is going on.  Try removing and installing libboo2.0-cil.

```
sudo apt-get remove libboo2.0-cil
```
Then install it again.
```
sudo apt-get instsall  libboo2.0-cil
```
Now try to install Banshee again.  Which version of Ubuntu are you using?

---

### Post by Frak on 2008-06-11
```
gksudo gedit /etc/apt/sources.list
```

Insert these 2 lines to the end of the file.

```
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main
```

Then run this in the terminal

```
sudo apt-get update
sudo apt-get install banshee-1
```

You're done.

---

