---
title: "firefox password manager does not work"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by james.jadesword on 2014-07-18
History: I had some problems with firefox and thought it may be because of some esoteric parameter that was accidently changed. I did a complete uninstall followed by a clean install.

Problem: I am unable to set the master password. I am unable to save any passwords.

System: Ubuntu 12.04 64-bit, kernel linux 3.2.0-67-generic, gnome 3.4.2, 3.9 GiB RAM, AMD Phenom II x4 920 processor, 1.7 TiB available disk space, 149.0 GiB swap

Firefox: firefox 30.0, mozilla firefox for ubuntu canonical 1.0

Question: How may I enable the firefox password manager?

---

### Post by ajgreeny on 2014-07-18
You probably did not need to purge FF and reinstall it, (I presume you meant FF, not the whole OS?), as I imagine the problem stems from a setting in your FF profile, so try renaming the hidden **~/.mozilla** folder in your home, restart FF and see if you can now set both a master password and also separate web-site passwords to be remembered.

If that works you can start copying back some of the folders and files from the renamed .mozilla folder or importing bookmarks etc etc, from the old files.  If you don't know how, come back again and ask.

---

### Post by james.jadesword on 2014-07-18
Thank you for your help. I tried your suggestion and renamed the Firefox folder. The Firefox folder was reinstalled. I checked out the configuration and found that the configuration was completely different from the clean install Firefox folder. Since the problem seems to be from the profile data included with the clean install, I suspect that the package from the archive should not have included any profile data. I presume that since I was able to set the master password that the password manager will save and auto-fill passwords.

Thank you for your assistance as the convenience of using a password manager saves me a lot of time as my passwords are randomly generated printable ASCII.

---

