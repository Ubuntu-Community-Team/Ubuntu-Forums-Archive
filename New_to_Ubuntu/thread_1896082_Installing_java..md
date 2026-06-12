---
title: "Installing java."
date: 2011-12-16
forum: New to Ubuntu
---

### Post by De.Bug on 2011-12-16
So I used this command in the terminal.

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

And this is what showed up in the terminal :P

```
ava6-jdk sun-java6-jre sun-java6-plugin
[sudo] password for drake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package sun-java6-bin
E: Package 'sun-java6-fonts' has no installation candidate
E: Package 'sun-java6-jdk' has no installation candidate
E: Package 'sun-java6-jre' has no installation candidate
E: Unable to locate package sun-java6-plugin
drake@drake-G74Sx:~$
```

Was wondering what is the problem? lol.

Thanks in advance!

-Revjester

---

### Post by drpjkurian on 2011-12-16
Hi
What I understand is that those packages are obsolete

---

### Post by De.Bug on 2011-12-16
> **drpjkurian said:**
> Hi
What I understand is that those packages are obsolete

No longer exist? Not 100% the meaning of obsolete :P

---

### Post by gandaran on 2011-12-16
> **De.Bug said:**
> No longer exist? Not 100% the meaning of obsolete :P
Ubuntu did not provide the sun-java packages for 11.10 but you can add this [PPA repository]("https://launchpad.net/~ferramroberto/+archive/java") to software sources then update package list and run the install commands or if you prefer the new java update download the latest version from java website and manually install it.

---

### Post by d4m1r on 2011-12-16
1)java.com lists the latest versions available for various distros of linux

2)software centre also has it (or the ubuntu equivalent, icedtea?)

---

### Post by oldos2er on 2011-12-16
> **De.Bug said:**
> Was wondering what is the problem? lol.


Do you have the 'partner' repository enabled?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Canonical_Partner_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Canonical_Partner_Repositories)

---

