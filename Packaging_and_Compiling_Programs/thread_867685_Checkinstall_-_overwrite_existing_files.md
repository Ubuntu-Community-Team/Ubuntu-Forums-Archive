---
title: "Checkinstall - overwrite existing files?"
date: 2008-07-23
forum: Packaging and Compiling Programs
---

### Post by Skerit on 2008-07-23
Hi everyone,

I've been wrestling with the multiproto drivers for a while. Because it's such a tedious task to constantly recompile different versions of the driver (and make clean, make distclean, make rminstall never really delete everything) I thought it would be much easier to just make a deb out of them using checkinstall. That would make the entire task a lot easier.

Making the deb is no problem.
Unfortunately, these drivers need to overwrite a certain file (ir-common.ko) which is already in another, important, package (linux-image-2.6.24-20-generic)

How is this fixable? 

root@HTPC-MYTH:/opt/dvb/multiproto# dpkg -i *.deb
(Database inlezen ... 137231 bestanden en mappen geïnstalleerd.)
Uitpakken van multiproto (uit multiproto_7207-1_i386.deb) ...
dpkg: fout bij afhandelen van multiproto_7207-1_i386.deb (--install):
 poging tot overschrijven van `/lib/modules/2.6.24-19-generic/kernel/drivers/media/common/ir-common.ko', wat ook in pakket linux-image-2.6.24-19-generic zit
dpkg-deb: subproces paste werd gedood door signaal (Gebroken pijp)
Fouten gevonden tijdens behandelen van:
 multiproto_7207-1_i386.deb

---

