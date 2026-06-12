---
title: "What's the best way to install eclipse?"
date: 2006-11-15
forum: Programming Talk
---

### Post by jrjazzman on 2006-11-15
I've currently got eclipse and jdt installed via apt.  However, since Eclipse likes to do updating and installing itself, won't there be some kind of conflict with APT?  I don't think APT has any way of knowing what Eclipse has installed or updated.  Is it best to prevent Eclipse from performing updates/installs?  There's probably a simple answer.  I'm still trying to get used to having a package manager control the installation of user programs.

thanks

---

### Post by hod139 on 2006-11-15
For installing the repository version, I suggest my howto: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)
(your sig suggests you are still using dapper so this howto applies).

If you are using the version of eclipse in the repository, then you will not be running the latest and greatest version.  The only updates/upgrades will come from ubuntu.  I don't mind running slightly older versions of software (except for firefox, I **love** the new spell check feature in 2.0!) relying on the comfort of ubuntu's packaging.

---

### Post by shining on 2006-11-15
> **jrjazzman said:**
> I've currently got eclipse and jdt installed via apt.  However, since Eclipse likes to do updating and installing itself, won't there be some kind of conflict with APT?  I don't think APT has any way of knowing what Eclipse has installed or updated.  Is it best to prevent Eclipse from performing updates/installs?  There's probably a simple answer.  I'm still trying to get used to having a package manager control the installation of user programs.

thanks

Firefox has also an update feature, but it's disabled in debian/ubuntu package for this reason.
I didn't pay attention in eclipse though, they didn't disable it?
In any case, I didn't have any problems, so it doesn't seem to update automatically. You just need to avoid using this feature.

I believe some ppl prefer to install it manually. In this case, I think it's better to remove any eclipse/jdt packages installed by apt, and to install eclipse to /opt/ or /usr/local/

---

### Post by jrjazzman on 2006-11-15
I think I'm more comfortable installing and updating eclipse manually.  

I did not realize I had been using GNU's jvm.  Fixed that immediately.

---

