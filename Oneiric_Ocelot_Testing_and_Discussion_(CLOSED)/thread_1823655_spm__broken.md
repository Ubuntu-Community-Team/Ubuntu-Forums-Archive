---
title: "spm  broken"
date: 2011-08-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-08-12
just me or others

---

### Post by dino99 on 2011-08-12
spm ?  give some details please

---

### Post by Quackers on 2011-08-12
Synaptic? It's good here.

---

### Post by fjgaude on 2011-08-12
It's good too, on multiple boxes.

---

### Post by sgage on 2011-08-12
If indeed we're talking about synaptic, it seems there's been a goodly amount of apt-related stuff being updated today, so perhaps you fell in between some updates. I'd just get to a terminal and run apt-get to see if you can get squared away.

Everything working fine here, though.

---

### Post by rburkartjo on 2011-08-12
will keep trying if i try to open synaptic nothing happens. weird. running xfce says it doesnt exist. and if running unity just wont open

---

### Post by rburkartjo on 2011-08-12
keep getting this error message

Could not launch 'Synaptic Package Manager'
Failed to execute child process "synaptic-pkexec" (No such file or directory)

note spm was fine early yesterday

---

### Post by Harry33 on 2011-08-12
> **rburkartjo said:**
> keep getting this error message
Could not launch 'Synaptic Package Manager'
Failed to execute child process "synaptic-pkexec" (No such file or directory)
note spm was fine early yesterday

There was an update to synaptic yesterday (new version is 0.75.2ubuntu3).
The authentication was switched from gksu to pkexec.

> Changelog
synaptic (0.75.2ubuntu3) oneiric; urgency=low

  * Use pkexec instead of gksu for authentication:
    - debian/patches/02_ubuntu_desktop_file.dpatch: switch to pkexec
      wrapper.
    - debian/patches/06_ubuntu_su_to_root.dpatch: switch to pkexec wrapper.
    - debian/patches/11_use-pkexec.dpatch: add policy file and adjust
      Makefiles.
    - debian/control: remove gksu from recommends.
    - debian/rules, debian/synaptic-pkexec: install wrapper to work around
      .desktop files not being able to call pkexec directly.
 -- Marc Deslauriers <email address hidden>   Thu, 11 Aug 2011 08:48:51 -0400

So, what if you downgrade to the earlier version 0.75.2ubuntu2
Here:
[https://launchpad.net/ubuntu/+source/synaptic/0.75.2ubuntu2](https://launchpad.net/ubuntu/+source/synaptic/0.75.2ubuntu2)

Just download the deb file and then from terminal go to that folder and install with dpkg:
```
sudo dpkg -i *.deb
```

---

### Post by rburkartjo on 2011-08-12
tks harry

---

### Post by rburkartjo on 2011-08-17
after the lastest series of updates synaptic is now working

---

