---
title: "How do i run a program which is installed. But does not show on any of my desktop men"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Mark.H on 2008-07-07
How do i run a package that is installed in Ubuntu 8.04. but does not show up in any of my drop down desktop menu's  for example if I open synaptic Package manager and view all installed packages there sre some programs I would like to run but do not know how?

How do I start the desired packages?

Cheers for now...

---

### Post by Immolatus on 2008-07-07
Generally you can run anything by typing it's name in a terminal window as an argument. For instance, you can start synaptic by opening an terminal and just typing synaptic and press enter.

What program is it you are trying to run? As the problem may be that you haven't got all of it's components installed.

---

### Post by Car60n on 2008-07-07
Type the program name in terminal,
like firefox in terminal to open mozilla firefox..

---

### Post by Mark.H on 2008-07-07
Ok Thank's

So I need to open terminal and type in the name of the desired package (as it is spelled in synaptic).

If this does not work?
What is that about having all correct components installed??

How do I find out this and also rectify it??

---

### Post by AOZ on 2008-07-07
could you clarify what it is you downloaded and are trying to run?

---

### Post by Car60n on 2008-07-07
i think you are taking about dependencies..
to check for broken dependencies type--
```
sudo apt-get check
```
if you want to install anything type--
```
sudo apt-get install 'package name'
```

---

### Post by txcrackers on 2008-07-08
> **Mark.H said:**
> So I need to open terminal and type in the name of the desired package (as it is spelled in synaptic).

Nope - you need to determine what the executable filename is that's *in* the package. Select the package you're curious about, right-click, select properties, select Files/provided. The interesting bits are installed to /usr/bin

> 
What is that about having all correct components installed??

How do I find out this and also rectify it??
*Technically*, this isn't supposed to happen using the package-management system. The odds are pretty good that you don't have to worry about this...

---

### Post by hyper_ch on 2008-07-08
if it's not added to the menu then it is most likely a CLI program.

---

### Post by InlawBiker on 2008-07-08
Nah this happens to me all the time - stuff installed in Synaptic sometimes does not show up in your menus.  For instance I just installed webalizer.

First find the executable name.  Odds are it's pretty intuitive.  Go to a terminal and type the first few letters of the "guessed" program and and hit Tab.  If nothing happens hit tab again.

For instance:

```
user@host~# fi<tab><tab>
```

All of the executables in your path that start with "fi" are shown.  Is yours in there?  Type a few more letters, if it finds only one it'll auto-complete the filename.

```
user@host~# fire<tab><tab>
```

This completes as "firefox"

If it's not showing up them you may not have the right filename, or it's not in your path.

Try going into Synaptic again, and find the package you installed.  Right click it and hit Properties.  One of the tabs is "installed files."  Every file it installed is listed here.

Once you find it you can add an icon to the menus in the normal way.

---

### Post by sdennie on 2008-07-08
Or, if it's a CLI only package and you know the name of the package you just installed, you can probably find the binaries it installed using:

```

dpkg -L name_of_the_package | grep bin/

```

---

### Post by bumanie on 2008-07-08
Sometimes alt+F2 will work. A box appears, type the program name in there and that will often run it.

---

