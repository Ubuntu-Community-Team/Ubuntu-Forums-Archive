---
title: "My synaptic package manager doesn't open"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by swapna123 on 2008-07-12
Hi,

I was trying to install medibuntu on my computer, but it failed and the synaptic package manager that used to work b4, has stopped working.

It gives the following message when I try to open synaptic package manager:
---------------------------------------------
E: Type '--19:09:04--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
-----------------------------------------------

I want to get my synaptic package manager working. Somebody please help me with this. I have just swtiched from windows to ubuntu.

Thanks in advance!!
Swapna

---

### Post by roquefilipe on 2008-07-12
it seems that your /etc/apt/sources.list.d/medibuntu file is bad. make a backup and remove it, then try again.

---

### Post by unutbu on 2008-07-12
Hello swapna123, your problem is fixable.
Open a terminal. Type
```

sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/mediubuntu.list-20080712     # Save a copy of your sources.list just in case
gksu gedit /etc/apt/sources.list                                 # Edit sources.list 

```
Find any line that mentions medibuntu, and put a # symbol at the beginning of the line. (This will "comment it out")

Then add to the end of the file

```
deb http://packages.medibuntu.org/ hardy free non-free
```

change hardy to gutsy or whatever distro you are using.

Save and quit gedit. 

```
wget -q -O - http://packages.medibuntu.org/medibuntu-key.gpg | sudo apt-key add -
sudo apt-get update
```

Synaptic should now work.

---

### Post by drs305 on 2008-07-12
For hardy:
Backup your old medibuntu.list
```
sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
```

Reinstall medibuntu repository:
```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by karankrn on 2008-07-14
thank you! thank you!

i screwed up with medibuntu as well....but now i got it working again!!

no wonder i love Ubuntu!

---

### Post by swapna123 on 2008-07-22
Hey thanks a lot....my synaptic package manager works very well now...

Swapna

---

### Post by BGFG on 2008-07-22
I love Synaptic but in some of these cases, once the Universe and Multiverse are activated, wouldn't
```

sudo apt-get install medibuntu-desktop or
                     kubuntu-desktop or
                     xubuntu-desktop

```

and etcetera work also, 
i mean if I'm right in thinking that the main difference in the flavours is the desktop ?
i was a windows baby, but the terminal is the stuff.....

---

