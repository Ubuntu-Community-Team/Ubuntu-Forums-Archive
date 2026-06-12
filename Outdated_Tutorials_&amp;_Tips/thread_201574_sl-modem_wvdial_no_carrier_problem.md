---
title: "sl-modem wvdial no carrier problem"
date: 2006-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by gfwp on 2006-06-22
Hello

I got my smartlink compatible modem running following the instructions in this link, dued to kernel vs driver incompatibility:

[https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/31640](https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/31640)

Please take care of the following things

1) download your specific kernel header
2) download the source tarball slmodem-2.9.11
3) extract your tarball and move to that directoy within a shell
4) compile (make)
5) install (sudo make install)
6 an environment variable to point to the kernel header is not necessary
7 avoid the use of checkinstall to create a .deb package. I tried it and the installation failed, no idea why!
8) READ carefully the README file inside the tarball and follow the instruction for the configuration. You'll find startup scrips to modify and install in /etc/init.d/
9) run the scrip for starting the slmoemd daemon like described in the README
10) run the wvdial setup (sudo wvdialconf)
11) in /etc/wvdial.conf file add the line "Carrier Check =no" !!!!! this solves most of the problems I think!!!!
12) Enjoy wvdial working, in several cases is better to shut down the ethernet card before starting with dialing (sudo ifdown eth0)

gfwp

---

