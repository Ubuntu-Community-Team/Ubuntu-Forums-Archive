---
title: "trying to install freecad get &quot;Unable to locate package&quot;"
date: 2016-09-07
forum: New to Ubuntu
---

### Post by imawesome on 2016-09-07
hi I'm Jeff i just installed ubuntu on one of my laptops that is from 07 im vary impressed with it so for i don't get how to install things yet it seems that the CCX package needs to be installed separately. i stop at that pont

so i tried instructions from here [https://www.youtube.com/watch?v=jWJ5IqB163w](https://www.youtube.com/watch?v=jWJ5IqB163w)
they did not work. here is the web page of freeCAD instructions [https://launchpad.net/~freecad-maintainers/+archive/ubuntu/freecad-stable](https://launchpad.net/~freecad-maintainers/+archive/ubuntu/freecad-stable)

> jeff@dell:~$ sudo add-apt-repository ppa:freecad-maintainers/freecad-stable
[sudo] password for jeff: 
 This PPA repository hosts stable releases of FreeCAD for all supported versions of Ubuntu in 32 and 64-Bit architecture. These packages are more up to date than those found on the Ubuntu repositories.

Note: the ccx package brings CalculiX support to the FEM workbench, and needs to be installed separately.
 More info: [https://launchpad.net/~freecad-maintainers/+archive/ubuntu/freecad-stable](https://launchpad.net/~freecad-maintainers/+archive/ubuntu/freecad-stable)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpcozdkzzq/secring.gpg' created
gpg: keyring `/tmp/tmpcozdkzzq/pubring.gpg' created
gpg: requesting key 19BB5BCA from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpcozdkzzq/trustdb.gpg: trustdb created
gpg: key 19BB5BCA: public key "Launchpad PPA for FreeCAD maintainers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
jeff@dell:~$ sudo apt-get update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease          
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Get:4 [http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu](http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu) xenial InRelease [17.6 kB]
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Get:6 [http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu](http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu) xenial/main i386 Packages [1,212 B]
Get:7 [http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu](http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu) xenial/main Translation-en [904 B]
Fetched 114 kB in 4s (23.1 kB/s)                                        
Reading package lists... Done
jeff@dell:~$ sudo apt-get install ccx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ccx


---

### Post by QIII on 2016-09-07
Hello!

It appears that the package you need is called *calculix-ccx*.

Give that a whirl.

Cheers!

---

### Post by imawesome on 2016-09-07
thanks it worked your the best[**[COLOR=#C61919][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=628170")

---

### Post by ajgreeny on 2016-09-07
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

