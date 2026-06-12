---
title: "How to install Mentor PCBBrowser"
date: 2005-11-11
forum: Outdated Tutorials &amp; Tips
---

### Post by smsmith050 on 2005-11-11
Mentor PCBBrowser is used by engineers to review the layout for Board Station RE and Expedition PCB projects.


Download PCBBrowser
[http://www.mentor.com/products/pcb/browsers.cfm]("http://www.mentor.com/products/pcb/browsers.cfm")

Extract the zip file to your home directory 
In the /home/username/pcb_browser/linux/ directory make install.ixl executable 
chmod o+x install.ixl
run the install.ixl see manage_sw_pcb.pdf
I installed in /home/username so the installer created a directory 2004 for the installation.

setup environment 
SDD_HOME=/home/username/2004/
export SDD_HOME
MGC_HOME=/home/username/2004/common/linux/
export MGC_HOME
WDIR=/home/username
export WDIR
PATH=$MGC_HOME/bin:$PATH
export PATH

Ubuntu does not have libstdc++-libc6.1-1.so.2
Install the following packages:
libstdc++2.10-glibc2.2
I used Synaptic
make a link to the lib in /usr/lib
/usr/lib$ sudo ln -s libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.1-1.so.2

run PCBBrowser

---

