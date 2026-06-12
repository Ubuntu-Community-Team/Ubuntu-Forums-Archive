---
title: "Installing libwxgtk2.8-0 package."
date: 2013-05-16
forum: New to Ubuntu
---

### Post by niharika89 on 2013-05-16
Hi when I try to install libwxgtk2.8-0 using command
sudo apt-get install libwxgtk2.8-0

I am getting error as:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwxgtk2.8-0: Depends: libgconf2-4 (>= 2.31.1) but 2.28.1-0ubuntu1 is to be installed
                 Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not installable
                 Depends: libjpeg62 (>= 6b1) but 6b-15ubuntu1 is to be installed
E: Broken packages
```

To met its dependency i installed libgconf2-4 and ibjpeg62. But when I  try to install libgdk-pixbuf2.0-0 package. Its giving me error:
```
sudo apt-get install libgdk-pixbuf2.0-0

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgdk-pixbuf2.0-0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgdk-pixbuf2.0-0 has no installation candidate
```

How to fulfill the dependency for libwxgtk2.8-0 package.
Please help....

---

### Post by sandyd on 2013-05-17
The forum you originally posted in (Ubuntu, Linux and OS Chat) is not a support forum.

I have moved your post to the Absolute Beginners Section where you can get help.

Welcome to Ubuntu! :)

---

