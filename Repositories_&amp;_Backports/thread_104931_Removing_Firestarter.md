---
title: "Removing Firestarter"
date: 2005-12-17
forum: Repositories &amp; Backports
---

### Post by doboy007 on 2005-12-17
I'm trying to get rid of Firestarter from my config.

Trying synaptic to purge Firestarter and using dpkg for the same yields the following error message : 

dpkg: error processing firestarter (--purge):
 subprocess post-removal script returned error exit status 1

What does this mean?

---

### Post by mr_pouit on 2005-12-17
Same error here :( .. Perhaps is there a mistake in the "postrm" script ?

```
Package: firestarter
Status: install ok installed
Priority: optional
Section: universe/admin
Installed-Size: 1904
Maintainer: Yann Verley <yann.verley@free.fr>
Architecture: i386
Version: 1.0.3-1.1ubuntu1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libaudiofile0 (>= 0.2.3-4), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.4-1), libesd0 (>= 0.2.29-1) | libesd-alsa0 (>= 0.2.29-1), libgconf2-4 (>= 2.9), libgcrypt11, libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.6.0), libgnome-keyring0 (>= 0.4.0), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.10.0-0), libgnutls11 (>= 1.0.16), libgpg-error0 (>= 1.0), libgtk2.0-0 (>= 2.6.0), libice6 | xlibs (>> 4.1.0), libjpeg62, liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.8.1), libpopt0 (>= 1.7), libsm6 | xlibs (>> 4.1.0), libtasn1-2 (>= 0.2.8), libx11-6 | xlibs (>> 4.1.0), libxml2 (>= 2.6.17), zlib1g (>= 1:1.2.1), iptables (>= 1.2.11), gksu (>= 0.8.5)
Conffiles:
 /etc/firestarter/non-routables 9752838a203132f108c9113fc8bc6355
 /etc/init.d/firestarter 982f734975424d0ada15d06a014b46cc
Description: gtk program for managing and observing your firewall
 Firestarter is a complete firewall tool for Linux machines. It
 features an easy to use firewall wizard to quickly create a
 firewall. Using the program you can then open and close ports
 with a few clicks, or stealth your machine giving access only
 to a select few. The real-time hit monitor shows attackers
 probing your machine.

```

---

