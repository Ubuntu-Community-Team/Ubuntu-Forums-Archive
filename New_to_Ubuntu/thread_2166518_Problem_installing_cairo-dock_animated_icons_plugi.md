---
title: "Problem installing cairo-dock animated icons plugin"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by marinecomm on 2013-08-09
So i downloaded this .deb package. Went to install it and got an error message stating that a dependency file is missing: libpango-1.0-0. Fired up Synaptic and checked it out. I have the file libpango1.0-0. My question is: Is the file I have (libpango1.0-0) the same file that it says is required (libpango-1.0-0)? If it is then why might I be having this issue? I'm running Xubuntu 12.04 64-bit.

---

### Post by Dennis N on 2013-08-09
The file names are different: libpango-1.0-0 is listed in the package as the dependency, while we have libpango1.0-0 installed (or available). The installer would consider them different packages, even if they are not. It cannot proceed.

---

### Post by marinecomm on 2013-08-09
Then how do I get ahold of the dependency file?

---

### Post by Dennis N on 2013-08-09
You probably could get hold of it, but no guarantee it will work (probably not) with Ubuntu. On a 3rd party .deb not from the repos, if they won't install as-is or are unable to meet dependencies with the Ubuntu repos, best to give up in my opinion.   

For information, from Debian packages:
[http://packages.debian.org/sid/libpango-1.0-0](http://packages.debian.org/sid/libpango-1.0-0)

Notice is says libpango1.0-0 is **similar** - not the same.

---

### Post by marinecomm on 2013-08-09
Clicked on the link you provided in your post and got the following error message:

HTTP ERROR: 504

Gateway Timeout

RequestURI=http://packages.debian.org/sid/libpango-1.0-0

---

