---
title: "wines  /etc/apt/sources.list"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-05-23
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) tell me how to add wines to my source list but the command 
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list 
seem not to add anything to my source list

Can someone tell me the correct command or paste there /apt/sources.list
thanks

---

### Post by Cypher on 2008-05-23
Did the WGET command succeed? Do you see the file '/etc/apt/sources.list.d/winehq.list'? Have to run "sudo apt-get update"?

---

### Post by wolfen69 on 2008-05-23
you can install wine by clicking [THIS]("apt://wine") link.

---

### Post by sam_delta on 2008-05-23
```
sudo aptitude update
sudo aptitude install wine
```

if it dosnt work, go into system>administration>software sources and click on all sources available (main, universe, restricted, multiuniverse, etc) and  try again

sam

---

### Post by ibizatunes on 2008-05-23
i have done all that twice and it seem not to have put anything in /apt/sources.list, 
I have installed wines, but it not in /apt/sources.list to get updates

---

### Post by Cypher on 2008-05-23
The command isn't going to add the WineHQ repo to your sources.list, but add it as an additional repos from the sources.list.d directory.

If you do the "sudo apt-get update" and watch all the sites it's hitting, you'll see 'wine.budgetdedicated.com' being one of them..

---

### Post by ibizatunes on 2008-05-23
yeah sorry it is in there!! im just being thick! Its friday!

---

### Post by philinux on 2008-05-23
If you want the latest wine i.e the realease candidate 1 RC1.
Then do this.


sudo gedit /etc/apt/sources.list.d/wineppa.list

paste
deb [http://ppa.launchpad.net/ubuntu-wine/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ubuntu) hardy main

Save file
and then install the newer package from synaptic
(it will be unverified because it's in the PPA and not an official archive)

---

