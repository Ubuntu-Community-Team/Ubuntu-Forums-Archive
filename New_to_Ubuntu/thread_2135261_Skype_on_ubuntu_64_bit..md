---
title: "Skype on ubuntu 64 bit."
date: 2013-04-13
forum: New to Ubuntu
---

### Post by naidZ on 2013-04-13
Hello.
I m currently having an issue installing skype on my system.
I've ubuntu 12.10 64 bit WUBI and i can't install it.
I've searched google and youtube yet i found nothing , eventhough i checked that calonical partners from othersoftware.
When i try to install skype from ubuntu software center an error message pop ups 
Package dependencies cannot be resolved
"This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."
The following packages have unmet dependencies:


skype: Depends: skype-bin but it is not going to be installed

Could someone help me, thanks in advance.

---

### Post by jimafternoon on 2013-04-13
In some cases similar problems of other people have turned out to be caused by a mis-configuration of the package management system related to multiarch support.

Please issue the following commands in the terminal:

```
dpkg --print-foreign-architectures
dpkg --print-architecture
```

If the first comand does not show any output, and the second one gives "amd64" you shouly try the following commands

```
sudo dpkg --add-architecture i386
sudo apt-get update
```

and then again

```
sudo apt-get install skype
```

---

### Post by naidZ on 2013-04-13
Thanks a lot!!!
It worked.

---

