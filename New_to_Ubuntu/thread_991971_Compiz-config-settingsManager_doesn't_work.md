---
title: "Compiz-config-settingsManager doesn't work"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by darek_jestem on 2008-11-24
When I try to open ccsm i have the output like this:

```
dariusz@dariusz:ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

```

---

### Post by whitethorn on 2008-11-24
Have you already activated your graphic card?  Go to System -> Preferences -> Appearance -> Visual Effects then click on Extra.  If that works then you should be able to start ccsm. If not then you'll first have to get drivers for you graphic card.

---

### Post by darek_jestem on 2008-11-24
I alreadty installed graphic drivers but i have not this option(Visual Effect)

---

### Post by philinux on 2008-11-24
Which version of ubuntu are you running

---

### Post by darek_jestem on 2008-11-24
```
dariusz@dariusz:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

```

---

### Post by Keen101 on 2008-11-24
you installed it with this right?

> sudo apt-get install compizconfig-settings-manager


I've never started it from the command line, but the shortcut on the menu is not under the System -> Preferences -> Appearance -> Visual Effects anymore. The regular compiz settings should be there, but the compizconfig-settings-manager i think will now be under System -> Preferences -> or System -> Administration ->

---

### Post by darek_jestem on 2008-11-24
Yes I installed it with this right:
```
dariusz@dariusz:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for dariusz:
Reading package lists... Done
Building dependency tree
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 142 not upgraded.

```
I have newest version...
I installed drivers from Envy..
I have been looking for this option everywhere...
I simply have not this option...:/

---

### Post by setsuna on 2009-01-15
> **darek_jestem said:**
> When I try to open ccsm i have the output like this:

```
dariusz@dariusz:ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

```

i've the same problem before,
but i fixed this with reinstall ccsm and its python

[I]```
sudo apt-get install python-compizconfig compizconfig-settings-manager 

```[/I]

~thx~

---

### Post by Vantrax on 2009-01-15
Setsunas fix should work, if it doesn't let us know and we will try to work out something else.

Also check that the mesa driver supports compiz for your card.

---

### Post by vahnx on 2009-05-12
I don't know what I did to encounter the problem but I am also getting:

```

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

``` 

Re-installing python-compizconfig and ccsm did not solve it for me =(

---

### Post by vahnx on 2009-05-13
Running 

```
sudo apt-get autoremove --purge compiz* libcompiz* emerald* libemerald* libdeco*
```

Then searching for compiz in Synaptics and checking off only 'compiz' then 'compiz settings manager' fixed it for me.

---

