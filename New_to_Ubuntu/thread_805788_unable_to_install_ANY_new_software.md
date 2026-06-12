---
title: "unable to install ANY new software"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by rockerphil on 2008-05-24
ok, here's the deal, i set up a minimalist install on my dinosaur of a computer yesterday using the minimal Ubuntu CD to install a command line interface and then instlaled the graphical elements. well things went fine for a while. well here's the problem, i go to try and install Synaptic and i get a string of errors, so i come here to the wonderful ubuntu forums and got the problem solved by editing my /etc/hosts file. well it worked fine afterwards for a bit untill i try to install the game Ltris through Synaptic (pretty simple right?) and get the same errors i got in the terminal, i'll post the terminal output now:


phil@phil:~$ sudo apt-get install ltris
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  libsdl-mixer1.2 libsmpeg0
The following NEW packages will be installed:
  libsdl-mixer1.2 libsmpeg0 ltris
0 upgraded, 3 newly installed, 0 to remove and 7 not upgraded.
Need to get 741kB of archives.
After unpacking 1843kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libsmpeg0 0.4.5+cvs20030824-2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libsdl-mixer1.2 1.2.6-3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe ltris 1.0.11-1ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/smpeg/libsmpeg0_0.4.5+cvs20030824-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/smpeg/libsmpeg0_0.4.5+cvs20030824-2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/l/ltris/ltris_1.0.11-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/l/ltris/ltris_1.0.11-1ubuntu1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
phil@phil:~$ 

i'll also post the contents of the /etc/hosts file here:


127.0.0.1       localhost
127.0.1.1       phil

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


and the contents of my /etc/apt/sources.list file here:


 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-security main restricted
# see [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.


can anyone please help me solve this problem? cus i really don't feel like reinstalling. thanx guys


ps. i've also tried running the command with aptitude in the place of apt-get, along with sudo apt-get update and sudo aptitude update along with running the command with --fix-missing

---

### Post by philinux on 2008-05-24
Choose a different server for your sources might help.

---

### Post by rockerphil on 2008-05-24
that's the thing though, i can ping the server just fine, so i know it's not the server

---

### Post by rockerphil on 2008-05-24
bump

could really use some help with this one guys. thanks :)

---

### Post by rockerphil on 2008-05-24
anyone?

---

### Post by philinux on 2008-05-24
Go to System>Admin>Software sources and change the server to Main

---

### Post by meindian523 on 2008-05-24
Please wait,if you don't get any replies means the people who can help are not present or nobody who's present knows anything about this.Frequent bumping is considered bad manners.
Also please post the link to the Ubuntu thread which solved your problem(temporarily).

---

