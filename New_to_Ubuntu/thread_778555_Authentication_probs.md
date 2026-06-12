---
title: "Authentication probs"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by timr92 on 2008-05-02
I think i am having authentication issues after upgrading from 7.10 to 8.04. When i am trying to do,
```
sudo dpkg --configure -a
```
it says;
```
sudo: unable to resolve host lcars_ubuntu
```

I am also having trouble running administrative apps and noticed errors in the auth.log;
```
sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
```
etc, let me know if anyone needs more logs or anything

Thanks,
Tim

---

### Post by Monicker on 2008-05-02
How to fix the "unable to resolve host" issue is covered here:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

Once that is taken care of, you should be able to run the dpkg command.


The messages about pam_smbpass.so are a known bug, and can be ignored.  Details about that are here:

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990")

---

