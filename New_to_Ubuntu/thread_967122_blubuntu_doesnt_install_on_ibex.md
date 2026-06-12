---
title: "blubuntu doesnt install on ibex"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Miroku on 2008-11-01
hello
im trying to get blubuntu onto my freshly installed ibex. i am using ubuntu 8.10 32 bit.
 
```
sudo apt-get install blubuntu-look
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  blubuntu-look: Depends: blubuntu-theme but it is not going to be installed
E: Broken packages

```

any help? thanks.

---

### Post by Patrick793 on 2008-11-01
Try this.

```
sudo apt-get install -f && sudo dpkg --configure -a && sudo apt-get install blubuntu-theme blubuntu-look
```

---

### Post by Miroku on 2008-11-01
got this:

```
sudo apt-get install -f && sudo dpkg --configure -a && sudo apt-get install blubuntu-theme blubuntu-look
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  blubuntu-theme: Depends: gtk2-engines-ubuntulooks but it is not going to be installed
E: Broken packages

```

its being so forceful, tellin me its NOT GOIN TO BE INSTALLED. lol.

---

### Post by Patrick793 on 2008-11-01
It keeps saying it needs a new package each time.

Try this.
```
sudo apt-get install blubuntu-look blubuntu-theme gtk2-engines-ubuntulooks
```

---

### Post by Miroku on 2008-11-01
o sweet! thanks man. this is wat happens when i have been on windows for the past 3 months, i think my brain slowed down. thanks again.

---

### Post by fooman on 2008-11-01
try it in synaptic...open synaptic and click on settings > repositories > ubuntu software tab.  make sure the first 4 choices are checked.

back in synaptic...search for "blubuntu-look" and mark for installation.

hope that works.

---

### Post by Dolmio on 2010-02-26
> **Patrick793 said:**
> It keeps saying it needs a new package each time.

Try this.
```
sudo apt-get install blubuntu-look blubuntu-theme gtk2-engines-ubuntulooks
```

Thanks, you are the best :D

I couldn't install Blubuntu on Ubuntu 9.10 (Karmic) but it worked with your help.

However, the Human-theme is missing now but I don't think I am going to use that again anyway ;)

Thanks again :P

---

