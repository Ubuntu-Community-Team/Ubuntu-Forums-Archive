---
title: "Installing Packages errors"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by bhinton on 2008-07-12
I am new to Linux. When I try to install a new program using "add/remove" or Synaptic Package Manager I get the following error:

E:dpkg was interrupted, you must manually run 'dpkg--configure-a' to correct the problem. E:cache-> open () failed, please report.

I tried going into the terminal and typing:   dpkg--configure-a
but nothing happened

I would appreciate any help as I cannot install any third party software.

Byron

---

### Post by abn91c on 2008-07-12
sudo dpkg --configure -a
check your typing it is case sensitive

---

### Post by lisati on 2008-07-12
You might need to prefix the command with "sudo", e.g. ```
sudo dpkg--configure-a
```

---

### Post by bumanie on 2008-07-12
You have to do it with root privileges, therefore put sudo in front of the command and it should work.

---

### Post by alienexplorers on 2008-07-12
> **lisati said:**
> You might need to prefix the command with "sudo", e.g. ```
sudo dpkg--configure-a
```

Remember to leave spaces between dpkg and the hyphens:
> sudo dpkg --configure -a

---

### Post by augie48 on 2008-08-09
tried sudo dpkg--configure-a
got command not found
downloaded dpkg_1.13.25_alpha.deb
need deb.something???

---

### Post by augie48 on 2008-08-09
need dpkg-dev   where do I get it?

---

### Post by Ryadt on 2008-08-09
> **augie48 said:**
> tried sudo dpkg--configure-a
got command not found
downloaded dpkg_1.13.25_alpha.deb
need deb.something???

copy and paste the command. it prevents any typo.
```
sudo dpkg --configure -a
```

---

### Post by augie48 on 2008-08-09
tried again with your sudo dpkg --configure -a still get command not found tried downloading alpha says I need dpkg-dev

---

### Post by zipperback on 2008-08-09
> **augie48 said:**
> need dpkg-dev   where do I get it?



```

sudo apt-get update && sudo apt-get install dpkg-dev

```

- zipperback
:popcorn:

---

### Post by starcannon on 2008-08-09
copy paste the codes you are being given. I noticed in your error output that your commands don't have spaces where they belong.

---

### Post by t0p on 2008-08-09
> **augie48 said:**
> tried sudo dpkg--configure-a
got command not found
downloaded dpkg_1.13.25_alpha.deb
need deb.something???

Where are you downloading this stuff from?  If you install software through Synaptic (**System > Administration > Synaptic Package Manager** or with an **apt-get** command, all dependencies (required software) should be dealt with.

Also, you say you tried

> sudo dpkg--configure-a

but the command should be

```
sudo dpkg --configure -a
```

Notice the spaces after dpkg and configure?  They are *important*!

---

### Post by augie48 on 2008-08-09
cannot access sudo, request sudo password, updated new password no luck

---

### Post by starcannon on 2008-08-09
If you have no sudo password, your basically locked out of administering your system.

Your sudo password should be the same as your regular login password.

---

### Post by augie48 on 2008-08-09
got in  now cannot access dpkg access area, read only file sx

---

### Post by t0p on 2008-08-09
"Read-only"?  :confused:

Can you paste in here the actual error message you're getting?

---

### Post by augie48 on 2008-08-09
still get dpkg        interrupted manually install dpkg --configure -a even when I did the apt-get stuff

---

### Post by augie48 on 2008-08-09
don't remember how but it was recommended I download a alpha deb , but it would not install am still having problems using synaptic package manager because I continue to get dpkg interrupt and cannot sudo dpkg --configure -a command not found even after running fschk

---

### Post by augie48 on 2008-08-09
Thanx everyone, finally got sudo working, password working, synaptic package manager working, ubuntu loads without looping control D, update manager is working, downloading over 200 updates maybe I can do linux after all, this old dog is learning new tricks, who said old people cannot learn, slower maybe but also have old wisdom.  augie 48

---

