---
title: "Traceroute and print queues scripting"
date: 2009-11-12
forum: Programming Talk
---

### Post by smurphy_it on 2009-11-12
Good day.  I am doing an enq -WA, to get a list of the print queues, I then compare that to the /etc/hosts file to 'match' the IP address associated with the print queues.  What I want to do is to run a traceroute with up to 5 hops, and perform an output to a file with some "specific items".  Here is what I have so far...

#!/bin/ksh
# -- Variables --
HOSTS=/etc/hosts
CFG=/tmp/pqueue.cfg.$$
TROUTE=/tmp/troute.log.$$

for i in `/usr/bin/enq -WA | grep -v ^Queue | grep -v -- ^----- | cut -f 1 -d \ ` ;  do grep $i $HOSTS ; done  | grep -v ^\# | awk {'print "define host{\n \tuse\t\tgeneric-printer\n\thost_name\t"$2"\n\taddress \t"$1"\n\thostgroups\tdi-printers\n}\n"'} > CFG

for j in `cat $CFG | grep address | cut -f 2 -d \ ` ; do echo "\n" "$j" && traceroute -q2 -m5 $j | awk '{print $3}' | grep "(" | tr -d "(" | tr -d ")" | tr "\n" "," ; done | sed s/\,//2 > $TROUTE



Does anyone have a better way of doing this.  What I want to do is get a list of all of the Print Queues and their IP addresses, as well as the Parents (from the Traceroute hops) and output it all into a text file which would be acceptable for nagios.

Any help would be appreciated, and yes as you have probably gathered I am quite a Newb when it comes to shell scripting.

---

