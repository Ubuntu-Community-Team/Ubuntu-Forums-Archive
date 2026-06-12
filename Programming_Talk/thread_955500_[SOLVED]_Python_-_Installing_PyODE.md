---
title: "[SOLVED] Python - Installing PyODE"
date: 2008-10-22
forum: Programming Talk
---

### Post by Zoomulator on 2008-10-22
I'm all new to linux and Xubuntu, but I've done some python programming in windows.

I've been using the PyODE library in windows, and would like to continue doing so in Xubuntu. However, I get a furious amount of errors when I try to easy_install PyODE. I'm guessing it can't find the dependencies, which would be ODE.

However I've got a really hard time following the steps to setup ODE in Xubuntu. The steps are [_here_](http://ode.org/ode-latest-userguide.html#sec_2_1_0), under section 2 in the document.

I've been trying to find the /config/user-settings/ folder, but to no avail. I've found a /root/.config/ , but I can't figure out how to access the darn thing to see what's in it =P

I've done step 5, but it doesn't seem to help the install of PyODE without doing step 3 and 4. Atleast that's what I'm guessing.

"edit the settings in the file /config/user-settings"

I'm tearing my hair off because of all these poorly articulated step-through lists for everything. Makes it pretty damn difficult to start out with programming.

Thanks for any help!

---

### Post by newbuntuxx on 2008-10-22
I can not help you install it, since I dont know how. But to access /root/.config/ (note its a hidden directory) open terminal (accessories-terminal)

type: 

```
cd /root/.config/
```

if you want to edit a specific file in that directory, say: config then type:

```
sudo gedit config
```

good luck

---

### Post by Zoomulator on 2008-10-22
> **newbuntuxx said:**
> I can not help you install it, since I dont know how. But to access /root/.config/ (note its a hidden directory) open terminal (accessories-terminal)

type: 

```
cd /root/.config/
```

if you want to edit a specific file in that directory, say: config then type:

```
sudo gedit config
```

good luck

I've tried the cd command, and it gives me "permission denied" when I try to enter. When I put "sudo" infront of it to try to give root privs, it says "sudo: cd: command not found". :confused:

---

### Post by escapee on 2008-10-22
Did you type it ```
sudo cd /root/.config/
```

---

### Post by unutbu on 2008-10-22
Let's back up. Have you tried installing python-pyode from Synaptic? Or are you trying to install this from a tar.bz2 file?

Unless you need the tar.bz2 version for some reason, the easiest way to install this should be to simply type
```

sudo apt-get install python-pyode
```


(or use Synaptic or equivalent package manager). All necessary dependencies will be pulled in for you.

PS. cd is a bash command. You can't "sudo cd" because sudo only works on actual executables. To cd /root, you probably have to change the permissions on the /root directory. That is a totally separate problem. You should not need to touch any file in /root to install software.

---

### Post by Zoomulator on 2008-10-22
> **unutbu said:**
> Let's back up. Have you tried installing python-pyode from Synaptic? Or are you trying to install this from a tar.bz2 file?

Unless you need the tar.bz2 version for some reason, the easiest way to install this should be to simply type
```

sudo apt-get install python-pyode
```


(or use Synaptic or equivalent package manager). All necessary dependencies will be pulled in for you.

PS. cd is a bash command. You can't "sudo cd" because sudo only works on actual executables. To cd /root, you probably have to change the permissions on the /root directory. That is a totally separate problem. You should not need to touch any file in /root to install software.

Thanks! Works perfectly! I'll have a closer look at the Synaptic manager too.

Problem fully solved! Cheers

---

