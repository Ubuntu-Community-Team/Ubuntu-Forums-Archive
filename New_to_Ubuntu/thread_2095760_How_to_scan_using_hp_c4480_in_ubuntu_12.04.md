---
title: "How to scan using hp c4480 in ubuntu 12.04"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by troubledboy on 2012-12-17
Guys can you teach me how to scan a document on a PC using HP c4480. Printing is working but i dont know how to scan to a PC. Im using ubuntu 12.04

Thank you in advance!!

[-o<

---

### Post by agillator on 2012-12-17
Since you are using an HP printer, install HPLIP directly from HP. In my experience the version installed by Ubuntu does not support scanning well. So . . . .

1. Download HPLIP for automatic installation from [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html).

2. Purge hplip using apt-get or whatever version of the package manager you are comfortable with. You want to purge, not just remove, so there will be no conflicts with the version you are about to install.

3. As a normal user (NOT AS ROOT) run the file you just downloaded. Note that it will ask your for your password at some point so it can do the necessarily installations as root. The defaults should work for most of the questions except those it is asking for information you know (like your password).

4. When installation is complete, run hp-setup to set up your printer. If you are using your printer on a wireless network select the network/ethernet/wireless option on the first screen, not thewireless/802.111 option. The program may not find your printer automatically in which case you will have to manually search and enter the ip address of your printer. After that there should be no problem.

That should do it. You may have to reboot your machine but you will now be able to scan using XSane or Simple Scanner. You control your printer, by the way, through CUPS by opening your browser and going to localhost:631.

Good luck and enjoy.

---

