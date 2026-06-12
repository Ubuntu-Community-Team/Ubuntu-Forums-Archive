---
title: "how to install Ubuntu to be owner."
date: 2013-01-25
forum: New to Ubuntu
---

### Post by boaventura on 2013-01-25
I have Ubuntu 12.10, 64 bits, installed for me as Administrator.

I would like to reinstall it, for me as Owner.

Presently  (as Administrator) I am unable to access the root directory which I need to activate my Fortran 64 Intel compiler.

What DVD engraving option should I use, and what would be the installation sequence ?

Thank you for your attention,
boaventura

---

### Post by Frogs Hair on 2013-01-25
Hello and Welcome

See this page before reinstalling. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

The root file system can be accessed using gksudo nautilus in the terminal to open the file system  GUI but I'm not clear about what you are looking for.

---

### Post by d4m1r on 2013-01-25
1) You won't get support on here on how to login as root user as it is not advised to do so for many reasons.

2) You can get temporary access to root user privileges using your regular user, which should be enough to install anything.

---

### Post by jatos on 2013-01-25
Aah, well we clearly have a new converted Windows user here :)

Never a bad thing!

---

### Post by Double.J on 2013-01-25
> **d4m1r said:**
> 1) You won't get support on here on how to login as root user as it is not advised to do so for many reasons.

2) You can get temporary access to root user privileges using your regular user, which should be enough to install anything.


+1

Don't forget it's 
```

gksudo
```

Instead of just```

sudo
``` if you want super user (administrator) access to a graphical program.

For example
```

sudo apt-cache search fortran
``` means search for available packages for fortran as the root user

```

gksudo nautilus 
``` means start the file manager nautilus as administrator. this allows you to edit system Config files and such. Always be careful running "as administrator" in Linux. Remember once you type in 'sudo' or 'gksudo' you are telling the system "I know exactly what I'm doing, let me get on with it" and ever obedient, the system will... even if you're killing it, it will happily complete your instructions... Then fail to boot.

Most users first experience with the terminal is installing, so it's easy to think that when the terminal checks back "requires root privileges" you just type in sudo to get round the problem, or worse sticking sudo  infront of any command you run. Remember "requires root privileges" means "are you sure?"

---

