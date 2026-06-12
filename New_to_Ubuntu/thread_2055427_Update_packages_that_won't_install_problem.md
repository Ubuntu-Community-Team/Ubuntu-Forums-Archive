---
title: "Update packages that won't install problem"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Gonda on 2012-09-09
Hi, 
Update manager has 6 recommended updates available, but when I try install them I receive an this report:

requires installation of untrusted packages: the action would require the installation of packages from not authenticated sources. 
Details:
build-essential glib-networking glib-networking-common glib-networking-services linux-firmware policykit-1-gnome

The updates are:

Recommended updates:
1.Information list of build-essential packages
Changes for the versions:
Installed version: 11.5ubuntu2
Available version: 11.5ubuntu2.1

Version 11.5ubuntu2.1: 

  * Revert the previous change, we shouldn't be foreign (LP: #1034568)
If you do not plan to build Debian packages, you don't need this package.
Starting with dpkg (>= 1.14.18) this package is required for building Debian packages.
This package contains an informational list of packages which are considered essential for building Debian packages.
This package also depends on the packages on that list, to make it easy to have the build-essential packages installed.
If you have this package installed, you only need to install whatever a package specifies as its build-time dependencies to build the package.
Conversely, if you are determining what your package needs to build-depend on, you can always leave out the packages this package depends on.
This package is NOT the definition of what packages are build-essential; the real definition is in the Debian Policy Manual. This package contains merely an informational list, which is all most people need.
However, if this package and the manual disagree, the manual is correct.

2. network-related giomodules for GLib
Changes for the versions:
Installed version: 2.32.1-1ubuntu1
Available version: 2.32.1-1ubuntu2

Version 2.32.1-1ubuntu2: 

  * debian/patches/gnutls-Try-to-find-root-certificates-locally-if-no.patch:
    - If a server erroneously sends us a root certificate, and it
      is not anchored, then try to lookup a certificate for the same
      issuer in the database (LP: #1033516)
      Thanks to Stef Walter

3. network-related giomodules for GLib - data files
4. network-related giomodules for GLib - D-Bus services
5. Firmaware for Linux kernel drivers
6. GNOME authentication agent for policyKit-1

I have tried one at a time and none will instal. 
Questions:
1. Are they necessary?
2. If not how do I stop them from coming up?
3. If they are, what do I do to get them to instal?
4. I recently installed a hp printer and sometimes i receive a message saying 'updates are available for hp printer, but when I click to instal them nothing happens - are these updates perhaps for that?

Regards,
gonda

---

### Post by jerrrys on 2012-09-09
Check this out Gonda

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=requires+installation+of+untrusted+packages&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=requires+installation+of+untrusted+packages&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Gonda on 2012-09-09
thanks, will go and take a look

---

### Post by Gonda on 2012-09-09
Thanks for that link jerrrys, 

I followed these instructions and the updates downloaded perfectly.
1. open a terminal
2. [FONT=Courier New]sudo apt-get update[/FONT]
3. [FONT=Courier New]sudo apt-get upgrade[/FONT]

---

### Post by jerrrys on 2012-09-09
Your welcome Gonda :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

