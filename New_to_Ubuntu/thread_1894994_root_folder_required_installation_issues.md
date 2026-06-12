---
title: "root folder required installation issues"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by garyhibdon on 2011-12-13
ok so ive been away from ubuntu for a while, though i cant necesarily that i was too familiar with it before.

im trying to install ventrillo, and the only software i can find requires copying the files for it to the /root/bin folder and i cant gain access to this folder to do it. 

so heres 2 questions:

1) is there an easier/better to install it?
---or
2) how can i gain access to this file to place the ventrillo files.


custom built pc running 11.10 ocelot

---

### Post by Mr. Shannon on 2011-12-13
I far as I know nothing should ever need to be installed to the root folder, and there is no /root/bin directory.

All, I could find was the server version for Linux.  Where did you download it from?

---

### Post by garyhibdon on 2011-12-13
[http://http://ventrilo.com/download.php]("http://http//ventrilo.com/download.php")

thats where i got it from.

the only version i could find had this in the readme:

> Ventrilo Script v2.1.0_02 written by Crypt Keeper
For ventrilo server v2.x

How to use these scripts:

1. Edit the ventrilo script and change VENPATH,
VENSRV, and VENUSER to match your setup (it is
currently setup for linux and the install path
and user account specified in the ventrilo_srv.htm)

2. Copy the ventrilo script to /root/bin
If you decide to put the ventrilo script somewhere
else there are two things to note: 1. Placing
the ventrilo script in the path makes life easier
and 2. You will need to change the VENSCRIPT
variable in S99ventrilo to the path where you
installed the ventrilo script if you use it to
start at ventrilo at boot/runlevel

3. Edit S99ventrilo to start or stop the servers
that you want and then copy it to the runlevel you
would like those actions to occur on (ie /etc/rc.d/rc3.d/
for startup at boot)

4. If you copied S99ventrilo to the rc3.d directory you 
can safely remove the ventrilo startup commands from your
rc.local

5. As long as root bin is in you path you can now type
ventrilo -h to get the usage of ventrilo script

Have Fun
  Crypt Keeper

---

### Post by MartijnNL on 2011-12-14
So why don't you skip the first line of item two and install it somewhere else? Like /usr/local/bin? You will need to do this using root privileges though. (Using sudo) By doing it this way it's in your PATH (which solves the issue mentioned in the first note in the same item).

---

### Post by garyhibdon on 2011-12-14
> **MartijnNL said:**
> So why don't you skip the first line of item two and install it somewhere else? Like /usr/local/bin? You will need to do this using root privileges though. (Using sudo) By doing it this way it's in your PATH (which solves the issue mentioned in the first note in the same item).


thanks man. ill give that a go. it listed in it  that in another location it may/may not work so i was kind of iffy. but ill try it tonight and let you know, thanks!

---

