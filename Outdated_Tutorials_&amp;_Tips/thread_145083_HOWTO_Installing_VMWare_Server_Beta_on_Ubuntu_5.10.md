---
title: "HOWTO: Installing VMWare Server Beta on Ubuntu 5.10 (Breezy)"
date: 2006-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by GWhite on 2006-03-15
HOW-TO: Installing VMWare Server Beta on Ubuntu 5.10 (Breezy)
------------------------------------------------------------------------

Install Ubuntu 5.10 -- apply all security updates.

Open a Terminal from Applications / Accessories and enable the root account for login with this command: "sudo passwd root"
Allow graphical root login by going to System / Administration / Login Screen Setup / Security Tab / Check "Allow root to login with GDM"

Configure your network card to use a static IP address under System / Administration / Networking (not required but a good idea).

Reboot the machine.

Login as root

Start Add/Remove Programs and under Settings / Repositories -- Add Community maintained (Universe).
Close Add/Remove Programs.

Open a Terminal from Applications / Accessories and enter these commands:

(Do as two separate steps)
"apt-get install xinetd build-essential libdb2 gcc-3.4 g++-3.4 linux-headers-$(uname -r)"
"apt-get install apache" (you may need to run this one twice)

Run this command in the Terminal window: "export CC=/usr/bin/gcc-3.4"

Make a folder in /root call vmware

Get the VMware Server files and save them in /root/vmware folder:

VMware-server-e.x.p-XXXXX.tar.gz
VMware-mui-e.x.p-XXXXX.tar.gz

Extract the server and mui files (tar zxvf filename)

Run "./vmware-install.pl" from the /root/vmware/vmware-server-distrib directory.
Answer all the questions from the install script.

Run "./vmware-install.pl" from the /root/vmware/vmware-mui-distrib directory.
Answer all the questions from the install script.

Both install scripts should have run with no errors.

Restart the machine and log in as the regular Ubuntu user.

You should see an icon called "VMware Server" installed under "System Tools" for administering the server.

---

### Post by jbaloul on 2006-03-27
[http://ubuntuforums.org/showthread.php?t=148670](http://ubuntuforums.org/showthread.php?t=148670)

;-)

JB

---

