---
title: "Is there a way to auto-answer &quot;yes&quot; to Java's license when installing restricted xtra"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by diablo75 on 2008-11-11
I am putting together a bash script that will automatically install and setup a lot of software for me and I'd like to get everything automated.  One of several pieces of software that this script installed is the ubuntu-restricted-extras package, via apt-get in the terminal.  I'd like to find a way to automate a "YES" answer to the license agreement (see attached screenshots).  Is this at all possible?  My ultimate goal is to be able to execute this script, walk away, and when I come back, it be completely finished with the script and not asking me if I agree to the license.

---

### Post by kansasnoob on 2008-11-11
No! In fact even Medibuntu is getting more difficult.

After only four years Ubuntu is approaching 8 million users, that creates a threat to the proprietary community!

They'll either play along (as with hplip and flash 10) or they'll fight like hell!

Canonical will win!

---

### Post by kansasnoob on 2008-11-11
After saying that though, it's been a while since I installed Linux Mint and I don't recall having to "tick" anything.

Maybe see if Husse over at Mint forums would clue you in.

---

### Post by Cypher2 on 2010-11-15
Did anyone get the answer for the Java query? It's the only thing missing to completely automate my install script... :(

here's the answer:

#!/bin/bash
echo "sun-java6-bin shared/accepted-sun-dlj-v1-1 boolean true" |debconf-set-selections
apt-get install sun-java6-bin
exit

---

### Post by waynefoutz on 2010-11-16
[http://hacktolive.org/wiki/Super_OS]("http://hacktolive.org/wiki/Super_OS")

SuperOS is a build of Ubuntu with all the extras, and a bunch of other useful software, installed out of the box. You get Flash, Java, Google Chrome, and a lot of other stuff you'd normally install anyway. It comes on a 1100-1200 mb .iso  for a DVD or USB thumb drive. It's a HUGE time saver if you are trying to do multiple installs. Another bonus is it has removed Computer Janitor, which causes a LOT of problems when used by newbies, and puts the less destructive Bleach Bit in it's place.

---

