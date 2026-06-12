---
title: "Howto: Build GnuCash 2.0.1 with HBCI Support enabled for EDGY"
date: 2007-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by nonameruler on 2007-03-03
Hey,

I just finished building GnuCash 2.0.1 with HBCI Support enabled. More Information at gnucash.org.
HBCI is needed to do onlinebanking in Germany. Maybe also for other countries.

Maybe this guide is for advanced users, but i try to be simple.

Sorry, but I don't have webspace to upload the deb packages I created. So you have to follow my instructions to build it on your own.

1. You need to have "deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse" enabled in "/etc/apt/sources.list". if there's a "#" before, just remove it with your favourite editor, for example: "gksudo gedit /etc/apt/sources.list".
2. do a "sudo apt-get update"
3. make a directory, whatever you'll call it, and change into it.
4. run "sudo apt-get source gnucash". Wait till apt finished and change into the new directory "gnucash-2.0.1"
5. do a "sudo apt-get build-dep gnucash" to install needed dev packages
6. do a "sudo apt-get install libaqbanking16-dev"
7. So now you need to edit the "changelog" file in "debian/" to prevent apt to update your package. "gksudo gedit debian/changelog"
Just add to the first line "hbci" just after "2.0.1-3ubuntu3". Save the file.
8. "gksudo gedit debian/rules" and jump to line 24. Add right after "--disable-error-on-warning" this " --enable-hbci". To compare your edited files, I attached the files changelog, rules.
9. Be sure, you are in the gnucash-2.0.1/ directory. Just enter "sudo dpkg-buildpackage -uc -b" to compile gnucash.

To install the newly build package, go to the parent directory an issue the package install command "sudo dpkg -i gnucash*.deb"

The Howto is based on:
[http://howtoforge.org/repackage_deb_packages_debian_ubuntu](http://howtoforge.org/repackage_deb_packages_debian_ubuntu)

---

### Post by melvix on 2007-03-13
Thank you for your Howto!
It was no problem to compile and install. Anyway, when I start the aqhbci module in gnucash, I get the following error.

$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
6:2007/03/13 21-14-16:(null)(27728):qt3_wizard.cpp:   43: I18N available for your language
6:2007/03/13 21-14-16:(null)(27728):qbanking.cpp:  911: Registering cfg module plugin manager
on_aqhbci_button: Oops, aqhbci wizard return nonzero value: -8. The called program was "/usr/lib/aqbanking/plugins/16/wizards/qt3-wizard".

Can you help?

Thank you

melvix

---

