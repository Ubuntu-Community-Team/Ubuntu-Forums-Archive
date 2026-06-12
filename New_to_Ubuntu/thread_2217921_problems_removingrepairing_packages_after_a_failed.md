---
title: "problems removing/repairing packages after a failed 14.04 install"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by ganeshsugunan on 2014-04-18
apt-get/dpkg refuse to admit that I have kde-window-manager installed, and when I try to repair it, I get the following error:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 kde-window-manager : Depends: libwayland-egl1-mesa (>= 10.0.2) but it is not going to be installed or
                               libwayland-egl1
E: Unable to correct problems, you have held broken packages.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 kde-window-manager : Depends: libwayland-egl1-mesa (>= 10.0.2) but it is not going to be installed or
                               libwayland-egl1
E: Unable to correct problems, you have held broken packages.


I don't appear to have any held packages, but it still fails.

---

### Post by ian-weisser on 2014-04-21
I'm not sure how the system could be more clear about the problem.

> **ganeshsugunan said:**
> The following packages have unmet dependencies:
 kde-window-manager : Depends: libwayland-egl1-mesa (>= 10.0.2) but it is not going to be installed or

kde-window manager needs libwayland-egl1-mesa to be installed or reinstalled first.
Looks like you edited the output, go back and look at the error message for that package.

Try installing it. If there's an error, please show us the entire session including the error.

---

