---
title: "klamav giving error messages cant work"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by squashpotato on 2011-10-17
Hi
Absolute newbie. Dont know command talk. 
While downloading upgrades for my 10.04 ubuntu dvd amd64, in aug/sept, was hit by your trojan episode; klamav found (something like) 2 copies of trojan ws.shatter.blast and it could only be from the linux packages I was downloading from this site. Klamav worked fine and found it, but since restoring system from disk twice now, cant get it to work and dont see why. 

Have read alot of threads on this site; useless stuff like "why do you want AV protection" which certainly is not relevant since Aug./Sept trojan hack episode on packages.  Nothing is impossible and with the pages notifying hackers in detail of all security flaws, perhaps that detailing should be rethought. (why give out directions? Ive had some hacking going on, telling me my back browser button is a "dll", and signing in to pages with endless "no data on page" windows that seem in-apropos. 

This is the errors klamav gives from command line: (Followed directions found on this site, did not fix)

1@1:~$ klamav
kbuildsycoca running...
Reusing existing ksycoca
QLayout "unnamed" added to Klamav "KlamAV ", which already has a layout

with sudo: 

:~$ sudo klamavQObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts:: Part * ) to KHTMLPart::slotActiveFrameChanged( KParts:: Part * )  [[<--no space here, read colon P as smiley****]]
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x4a00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x4a00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x4a00023

When trying to update from the frontend, it wont let me. Directions on this site say to change file location to /home/user/ etc, and it then tells me "cant change directories". 

sudo apt-get freshclam downloaded the whole update on command line, then told me "couldnt notify " klamav. 

Whats with the message of "changed layout?"
clamav and klamav are both on system; worked before, but now not. What am I doing wrong? 
Did the update for clamav on the update manager, didnt change. 
Thanks

---

### Post by KrazyKyngeKorny on 2012-07-01
I have Klamav scheduled. Slows the system, but, can live with that. But it keeps putting "can't access" messages over the tool bar at the bottom of the screen. Is there a silent mode, so I can access this too;bar while Klamav is running?

---

