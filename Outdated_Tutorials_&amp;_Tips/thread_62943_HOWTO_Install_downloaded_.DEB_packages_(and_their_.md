---
title: "HOWTO: Install downloaded .DEB packages (and their dependencies) in 2 steps"
date: 2005-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by jobezone on 2005-09-06
**HOWTO: Install downloaded .DEB packages (and their dependencies) in 2 steps**

The first command will unpack the package, and most probably give an error of missing dependencies.
The second command instructs **apt-get** to fix this problem. If these dependencies are available in the repositories, it will install them, and sucessfully finish the installation of **downloaded_package.deb**.

```
sudo dpkg -i downloaded_package.deb
sudo apt-get -f install
```

Be aware though, that not all .DEB packages were made with your version of Ubuntu in mind. You should inform yourself if it was intended for Ubuntu Hoary. If it was not (for example, many are packaged with Debian in mind), it may still work, but then again it may not. It might even make **apt-get** want to remove some packages you want to keep. You'll have to tell him not to continue :), and then remove the offending reason with
```

sudo apt-get remove downloaded_package
```.
If you are not too knowledgable yet with apt-get, dpkg, or ubuntu for that matter, get your new software from the oficial Main and Backports repositories as much as you can (using Synaptic or apt-get). It have been reviewed, packaged and tested to integrate well with your ubuntu system.

---

### Post by abish on 2008-07-07
from shell, go to the folder where you have downloaded the .deb and the dependencies...
and then use:

sudo dpkg -i --force-depends *.deb

:) in a single line :D

---

### Post by abish on 2008-07-07
from shell, go to the folder where you have downloaded the .deb and the dependencies...
and then use:

sudo dpkg -i --force-depends *.deb

:) in a single line :D

---

### Post by studiogrynn on 2008-10-09
Thank you all!! Very helpful - and the 

```
sudo dpkg -i --force-depends *.deb
```

is a real time saver!

John

---

### Post by sque on 2009-08-04
**DONT USE** --force-depends! [-X
It will not install dependencies, but it will configure package without validating dependencies.
Installed package will probably **[COLOR="Red"]NOT WORK[/COLOR]** at all or work with **[COLOR="Red"]mysterious behaviour[/COLOR]**. ](*,)

From the "man dpkg" it says for "depends":
```
depends: Turn all dependency problems into warnings
```

To properly install follow the first post:
```
sudo dpkg -i downloaded_package.deb
sudo apt-get -f install
```

---

