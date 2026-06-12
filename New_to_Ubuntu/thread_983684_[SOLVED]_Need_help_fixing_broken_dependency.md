---
title: "[SOLVED] Need help fixing broken dependency"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by hckirsch on 2008-11-15
My system froze while updating Kubuntu, apparently because the package libhtml-parser-perl depends on perl being >=5.10.0-10 (and I have 5.8.8-12 currently installed).  

Ok, so I can see where libhmtl-parser-perl would be broken.  Unfortunately,  su apt-get -f install   returns that it's unable to correct the situation (perhaps because the right perl is not yet installed?). 

In Synaptic, I can locate the broken package, but not remove it.  It also won't let me install the correct perl (it won't do that until I fix the broken package).  So I'm in a loop...

Thanks for your suggestions.

hck

---

### Post by taurus on 2008-11-15
Try

```
sudo apt-get --config -a
sudo apt-get -f install
sudo apt-get update
```
If there is a error message, post the whole thing here and from what command that error message came from.

---

### Post by hckirsch on 2008-11-16
Thanks for the reply.

Unfortunately, the first line: "sudo apt-get --config -a"  returns: "E: Command line option --config is not understood"  

Since I have seen that general syntax in another post, I tried "sudo dpkg --config -a" just in case that's what you had in mind, and it returned: " ...dependency problems - leaving unconfigured".  

Continuing, then, the "sudo apt-get -f install" command still complained of the dependency problem.  And the "sudo apt-get update" returned: "...Correcting dependencies... failed..."

Regards,
hck

---

### Post by handydan918 on 2008-11-16
I have found that when ap-get and synaptic get fouled up, sometimes aptitude can straighten things out. Unfortunately, the only thing I can tell you at this point is install it and try...

```
aptitude install <packagename>
```

---

### Post by hckirsch on 2008-11-16
Thanks - Aptitude let me roll back the offending package so nothing is broken anymore.  Maybe I won't try to upgrade after all...

Regards,
hck

---

