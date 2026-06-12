---
title: "Which directory should I install this binary?"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by zemega on 2014-04-27
Hi,

I wanted to install this binary package (**V**isualization and **A**nalysis **P**latform for **O**cean, Atmosphere, and Solar **R**esearchers, VAPOR) inside Ubuntu 14.04. There is this line that says "./vapor-install.csh /usr/local/apps". But I'm not sure this will be the usual directory for Ubuntu. Seems like /opt is more like it. Should I change the ownership of the files to root after installing it?

[https://www.vapor.ucar.edu/docs/vapor-installation/vapor-unix-binary-installation](https://www.vapor.ucar.edu/docs/vapor-installation/vapor-unix-binary-installation)

---

### Post by Impavidus on 2014-04-28
The usual place is either in /opt or in /usr/local. In /usr/local you can find several directories like bin, lib, include and share, which is designed to keep binary executables, libraries and shared data separate, just like in the normal directories (/usr/bin, /usr/lib etc.). It seems that your application doesn't follow this convention, so I would put it in /opt. In principle however you can put it wherever you want.

To install in /opt you'll need root access, so that would be ```
sudo ./vapor-install.csh /opt
```The files will most likely be root-owned already. The installation instructions you linked to don't say it, but they assume you are root in the installing step (but not in the user environment setup step).

---

### Post by zemega on 2014-04-29
So if I installed inside the /opt, other user will be able to use it? Next question is the instruction ". *vapor_home*/bin/vapor-setup.sh". In Ubuntu, this means I should put this line inside /etc/environment right? and include the path of the program binary inside the PATH line inside /etc/environment? I think that is what should be done.

---

### Post by Impavidus on 2014-04-29
If the package is installed in /opt, all users will be able to use it.

The instructions tell each user should put the line ". *vapor_home*/bin/vapor-setup.sh" in his .profile, assuming this user uses the bash shell. If every user uses the bash shell you could put it in /etc/environnement, but I don't think that is recommended. I haven't downloaded the software to check, but I assume this line in .profile will add the software to the PATH, so you don't have to do that yourself.

---

### Post by zemega on 2014-04-29
I put the line ". *vapor_home*/bin/vapor-setup.sh" in /etc/environment , it does nothing, I have to source it manually for the application to work. In any case, the program is working and accessible to all users albeit they have to source it manually every time they want to use it, so this thread is solved.

---

