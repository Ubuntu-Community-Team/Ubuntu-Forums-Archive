---
title: "Trying to get fingerprint in 12.04"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by LuciferRex on 2012-11-29
I am trying to get my fingerprint, but following the GUI steps, I found the page okay, but I can't view anything on it.  I assume it is because it runs without root access.  My question is: how would I run 'Passwords and keys' with root access?  
Also, running this returns no results:```
gpg --fingerprint
```
Please and Thank you.

Thanks newb85 for the solution!
[http://ubuntuforums.org/showpost.php?p=12380233&postcount=2](http://ubuntuforums.org/showpost.php?p=12380233&postcount=2)

---

### Post by newb85 on 2012-11-29
I'm not sure I understand what you're trying to do.  The name for Passwords and Keys used in the command prompt is seahorse, so to run it with root privileges,

```
sudo seahorse
```

Don't know if that will help...

---

### Post by LuciferRex on 2012-11-29
That is is!  Thanks a bunch!

---

