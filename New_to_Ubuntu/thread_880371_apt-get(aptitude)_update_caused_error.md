---
title: "apt-get(aptitude) update caused error"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Anjue on 2008-08-04
After I updated my hardy with aptitude I got this error even though I use apt-get also got this error.

```
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

What should I do? I tried a solution in the archive section and it's not worked!

---

### Post by phidia on 2008-08-04
Take a look at the possible solution [here]("http://ubuntuforums.org/showthread.php?t=822072") and let the thread know if that works or not.

---

### Post by beanhead on 2008-08-04
well its just a security update if its not sysem critical and your system runs fine, dont worry about it, if you are too worried you might try using the update manager and if you stillr get errors you could report a bug in launch pad with a post of your hard ware and the error. most likely if it ant broke dont fix it.

---

### Post by zvacet on 2008-08-05
@ **beanhead**

> well its just a security update if its not sysem critical and your system runs fine, dont worry about i

What is critical if security updates are not?

@ **Anjue**

Thar error mean that your source list is not sync with server,so fix will be

```
sudo apt-get update && sudo apt-get upgrade
```

You can try what **phidia** suggested.

---

