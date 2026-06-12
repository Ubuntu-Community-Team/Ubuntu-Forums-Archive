---
title: "What is root and user?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Darksci on 2008-05-13
Yep I am a linux noob lol.

Was playing around with Ubuntu a few days ago trying to configure all my hardware when I found out that some things wouldn't install unless I was on root (su - root).

So whats the point of this? Can't I just login as root on the login page?

Should I just install everything while being root?

---

### Post by NightwishFan on 2008-05-13
Root is absolute power, you are wise to just use a normal user, and run root for a small amount of time with sudo. (it is like this by default)

---

### Post by ryanhaigh on 2008-05-13
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Darksci on 2008-05-13
So should I install everything with root or only when asked to?

If I install on user will that be available to every other user? (if I decide to create another guest user).

---

### Post by django0909 on 2008-05-13
I'm probably wrong, but I don't think you can install anything without providing your root password.

---

### Post by NightwishFan on 2008-05-13
Anything to do with the system will need to be run with root and will inform you accordingly. Then you will revert to a normal user afterwards.

---

### Post by Darksci on 2008-05-13
> **NightwishFan said:**
> Anything to do with the system will need to be run with root and will inform you accordingly. Then you will revert to a normal user afterwards.

So when I'm asked for my password - that is root temporarily?

---

### Post by SomethingCronic on 2008-05-13
Yes, sudo will be root for that one command. You can still damage systems like this, but you are less likely to.

> **Darksci said:**
> So should I install everything with root or only when asked to?

If I install on user will that be available to every other user? (if I decide to create another guest user).

This depends. If you are to install a program from apt then you need to root access. e.g.

```
sudo apt-get install xmms
```

Some applications you can download from a site (such as google earth) and install with your normal user access, however because you are not root it will only be able to install to places the users has access to e.g. /home/<username>

This is fine, but it will only work for that one user.

If your confident of what you are installing, use sudo (root) to install the application as it will general install the program to a default/general directory. 

I say this because I personally beleive programs should be installed to /usr /opt etc... and /home/<user> should be your personal files only.

---

### Post by NIT006.5 on 2008-05-13
As far as I know, pretty much everything you try to install will want your sudo password. I can't think of any exceptions off hand. Basically, installing packages requires modifications to files and paths that your normal user account won't have access to (for security reasons) so you will be prompted to do it as a sudo user. One of the advantages of this is that if by any slim chance, you did run any dangerous software (or a virus, although I've never personally seen one on Linux) then the software would only have access to what your account has access to, thereby limiting the damage it can do.

---

