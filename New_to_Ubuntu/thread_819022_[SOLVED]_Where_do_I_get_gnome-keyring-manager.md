---
title: "[SOLVED] Where do I get gnome-keyring-manager"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-06-05
In what repository would I find gnome-keyring-manager?

---

### Post by ibutho on 2008-06-05
Its available in the main repository.

---

### Post by iaculallad on 2008-06-05
> **alienexplorers said:**
> In what repository would I find gnome-keyring-manager?

I don't know the repository but you could get the GNOME Keyring Manager-2.18.0 package in [here]("http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-keyring-manager.html").

---

### Post by wdaniels on 2008-06-05
Funny, it seems to have been [removed from Hardy]("https://launchpad.net/ubuntu/hardy/+source/gnome-keyring-manager/2.20.0-1ubuntu1") :confused:

---

### Post by ibutho on 2008-06-05
If you search at [http://packages.ubuntu.com](http://packages.ubuntu.com) for gnome-keyring, its listed as available in hardy.

---

### Post by wdaniels on 2008-06-05
> **ibutho said:**
> If you search at [http://packages.ubuntu.com](http://packages.ubuntu.com) for gnome-keyring, its listed as available in hardy.

Yes, but gnome-keyring-manager isn't.

---

### Post by ibutho on 2008-06-05
Oh, my apologies. I was confusing the two packages.

---

### Post by mintar on 2009-03-06
I know this thread is long dead, but just in case that somebody stumbles upon this by google (such as I did): gnome-keyring-manager got replaced by seahorse.

---

### Post by mahela007 on 2010-05-15
thanks mintar.. i'm one of those googlers who stumbled on this thread and found your post useful.. ;-)

---

### Post by Stryker777 on 2010-08-17
> **mintar said:**
> I know this thread is long dead, but just in case that somebody stumbles upon this by google (such as I did): gnome-keyring-manager got replaced by seahorse.

Thanks Mintar! I too am one of those who googles first and found your answer helpful!

---

### Post by ami7878 on 2010-08-29
> **mintar said:**
> I know this thread is long dead, but just in case that somebody stumbles upon this by google (such as I did): gnome-keyring-manager got replaced by seahorse.

mintar, you've saved me hours of searches.  Thanks mate. :D

---

### Post by garvinrick4 on 2010-08-29
```
rick@rick-laptop:~$ aptitude show seahorse
Package: seahorse
State: installed
Automatically installed: no
Version: 2.30.0-0ubuntu2
Priority: optional
Section: gnome
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 8,815k
Depends: libatk1.0-0 (>= 1.29.3), libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavahi-glib1 (>= 0.6.16), libc6 (>= 2.7), libcryptui0 (>= 2.27.5), libdbus-1-3 (>= 1.0.2),
         libdbus-glib-1-2 (>= 0.78), libgconf2-4 (>= 2.27.0), libglib2.0-0 (>= 2.23.5), libgnome-keyring0 (>= 2.25.5), libgpgme11 (>= 1.2.0), libgtk2.0-0 (>= 2.18.0), liblaunchpad-integration1 (>=
         0.1.17), libldap-2.4-2 (>= 2.4.7), libnotify1 (>= 0.4.5), libnotify1-gtk2.10, libsoup2.4-1 (>= 2.4.0), gconf2 (>= 2.10.1-2), gnupg (>= 1.4.7)
Recommends: openssh-client
Suggests: seahorse-plugins
Description: GNOME front end for GnuPG
 Seahorse is a front end for GnuPG - the Gnu Privacy Guard program - that integrates to the GNOME desktop. It is a tool for secure communications and data storage.  Data encryption and digital
 signature creation can easily be performed through a GUI and Key  Management operations can easily be carried out through an intuitive interface.

rick@rick-laptop:~$ aptitude show gnome-keyring
Package: gnome-keyring
State: installed
Automatically installed: no
Version: 2.92.92.is.2.30.3-0ubuntu1.1
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 5,243k
Depends: gconf2 (>= 2.10.1-2), libatk1.0-0 (>= 1.29.3), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.1.1), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgcr0 (>=
         2.29.90git20100216), libgcrypt11 (>= 1.4.2), libglib2.0-0 (>= 2.23.5), libgp11-0 (>= 2.29.90), libgtk2.0-0 (>= 2.20.0), libpango1.0-0 (>= 1.14.0), libtasn1-3 (>= 1.6-0), dbus-x11
Recommends: libpam-gnome-keyring
Breaks: libgnome-keyring0 (< 2.29)
Description: GNOME keyring services (daemon and tools)
 gnome-keyring is a daemon in the session, similar to ssh-agent, and other applications can use it to store passwords and other sensitive information. 
 
 The program can manage several keyrings, each with its own master password, and there is also a session keyring which is never stored to disk, but forgotten when the session ends.


```

---

### Post by momon on 2011-07-01
> **mintar said:**
> I know this thread is long dead, but just in case that somebody stumbles upon this by google (such as I did): gnome-keyring-manager got replaced by seahorse.
It might be dead but not buried !
thanks from me too ...

---

