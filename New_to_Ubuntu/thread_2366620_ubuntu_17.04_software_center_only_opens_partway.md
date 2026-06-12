---
title: "ubuntu 17.04 software center only opens partway"
date: 2017-07-19
forum: New to Ubuntu
---

### Post by birchheisenberg on 2017-07-19
I just installed ubuntu 17.04 and tried to open "software" from the menu and if loads to the point of having the options but no images etc... ran (apt-get update) still wont open correctly. Please help,

---

### Post by plucky on 2017-07-20
> I just installed ubuntu 17.04 and tried to open "software" from the menu and if loads to the point of having the options but no images etc... ran (apt-get update) still wont open correctly. Please help, 
Open a terminal and type ```
gnome-software
``` Post any errors shown.

If you are opening Software Centre for the first time,it takes a while before the images appear.

Also try running ```
sudo apt upgrade
``` from the terminal window. 

Post any errors shown.

Good Luck

---

### Post by monkeybrain20122 on 2017-07-20
Gnome software is broken. It is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1606238"). 

I don't use the software centre myself. A much better software manager is synaptic
```
sudo apt install synaptic
```

P.S. Seems that it might be fixed in 16.04 but not 17.04.

---

### Post by pauljw on 2017-07-21
> **monkeybrain20122 said:**
> Gnome software is broken. It is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1606238"). 

I don't use the software centre myself. A much better software manager is synaptic
```
sudo apt install synaptic
```

P.S. Seems that it might be fixed in 16.04 but not 17.04.

+1 on using synaptic.

---

### Post by RobGoss on 2017-07-22
There has been a lot of issues with the Software center in the pass and I'm still seeing issues, using  **synaptic package manager **would be your best option at this point, it's a lot faster installing your new soft altogether

```
sudo apt-get update

```

```
sudo apt-get upgrade

```

```
sudo apt-get install synaptic 

```

---

