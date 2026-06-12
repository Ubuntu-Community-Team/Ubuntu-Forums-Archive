---
title: "Inconsistent repository information"
date: 2010-09-14
forum: Repositories &amp; Backports
---

### Post by henrikr on 2010-09-14
Hey
I have just installed Ubuntu 10.04 and need to use the libgtk2.0-dev package for some develop project.. I install the package with:
```
 apt-get install libgtk2.0-dev
```But i get an the message:```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu2 is to be installed
                 Depends: libglib2.0-dev (>= 2.21.3) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
E: Broken packages
```The package i'm installing is depending on libgtk2.0-0 version 2.20.0-0ubuntu4 but a full search  on the  libgtk2.0-0 package reveals that version in the repository is an older 2.20.1-0ubuntu2

```

# apt-cache search --full libgtk2.0-0  
Package: libgtk2.0-0
Status: install ok installed
Priority: optional
[...]
Source: gtk+2.0
_Version: 2.20.1-0ubuntu2_
Provides: gtk2.0-binver-2.10.0
```If i do a search on packages.ubuntu.com for libgtk2.0-0  it says that the repository contain the right version (2.20.0-0ubuntu4) 
[http://packages.ubuntu.com/lucid/libgtk2.0-0](http://packages.ubuntu.com/lucid/libgtk2.0-0)

Of course i have cleaned and updated apt cache:
```

# apt-get clean
# apt-get update
# apt-get upgrade
```I have also tried with the main repository instead of my default one.

Anyone know how i can solve this mismatch problem??

---

### Post by personificator on 2010-10-02
I also have the same problem. Its currently preventing me from installing E17 latest.


This seems like a simple version mismatch... can anyone confirm?

RELATED POST:
[http://ubuntuforums.org/showthread.php?t=1533631](http://ubuntuforums.org/showthread.php?t=1533631)

---

### Post by unforgiven8419 on 2010-10-25
Same Problem Here!
no one can help!? should i use old repository?

---

