---
title: "Why is my bash profile empty?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by rustix on 2008-07-15
I tried ```
vi ~/.bash_profile
``` but when it opened it was empty. I've installed Java 6 JDK as well.. shouldn't this show in the bash profile?

---

### Post by cmnorton on 2008-07-15
On my system -- Kubuntu 8.04. -- .profile has entries comparable to the .bash_profile on Red Hat Systems. I have installed a bunch of things and neither .bashrc or .profile have been altered, at least that I can tell.

---

### Post by rustix on 2008-07-15
so then how could i view/edit classpaths?

---

### Post by cmnorton on 2008-07-15
Environment variables are set in .bashrc and .profile. That does not mean you cannot put things in .bash_profile, but you will have to find out the precedence for its being read, and I cannot remember that on an Ubuntu system.

---

### Post by rustix on 2008-07-15
but neither of them contain the classpaths for java :-/

---

### Post by Inxsible on 2008-07-15
> **cmnorton said:**
> Environment variables are set in .bashrc and .profile. That does not mean you cannot put things in .bash_profile, but you will have to find out the precedence for its being read, and I cannot remember that on an Ubuntu system.The precedence is .bash_profile, .bashrc and .profile, in that order.

---

### Post by rustix on 2008-07-15
> **Inxsible said:**
> The precedence is .bash_profile, .bashrc and .profile, in that order.
i'm sory but i'm a bit confused now...

---

### Post by ibuclaw on 2008-07-15
The precedence is the order of which they are read.
ie, if you set the same variable at different values in the .bashrc and .profile files, the .profile settings will take effect.

But back on track...
If you've installed java with apt, then it would most likely put those classpaths in the system profile files.

as follows:
```

/etc/bash.bashrc
/etc/profile

```
But its not as simple as that either.

There are a mass of levels where certain variables get loaded and such at different runtimes.

If you wish to see your JAVA classpaths, use echo.
If you wish to change/append them, type in "**export NAME="$NAME:/new/path**" in your ~/.bashrc file.

Regards
Iain

---

### Post by rustix on 2008-07-16
> **tinivole said:**
> The precedence is the order of which they are read.
ie, if you set the same variable at different values in the .bashrc and .profile files, the .profile settings will take effect.

But back on track...
If you've installed java with apt, then it would most likely put those classpaths in the system profile files.

as follows:
```

/etc/bash.bashrc
/etc/profile

```
But its not as simple as that either.

There are a mass of levels where certain variables get loaded and such at different runtimes.

If you wish to see your JAVA classpaths, use echo.
If you wish to change/append them, type in "**export NAME="$NAME:/new/path**" in your ~/.bashrc file.

Regards
Iain
actually its not in bash.bashrc or profile. 

how do i use echo to find the java classpath? I tried **"echo $JAVA_HOME"** but it just returned an empty line

---

