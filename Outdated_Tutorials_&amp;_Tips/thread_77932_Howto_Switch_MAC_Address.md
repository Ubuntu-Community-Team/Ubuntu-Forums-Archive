---
title: "Howto Switch MAC Address"
date: 2005-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by anthro398 on 2005-10-17
I often have to masquerade on the network for troubleshooting and wrote this simple script this morning to automate the process.  It should probably ping the target host prior to trying to assume its MAC address, but I didn't feel like fooling with that as it's only necessary to use this when someone asks me to.  
```

#!/bin/bash

# Switch MAC address to that of machine indicated by passed argument.


# Possible target MAC address
DESK="xx:xx:43:0B:d2:xx"	# my desktop	
DAVE="00-xx-xx-E7-4D-xx"	# Dave's desk
DMZ="00-11-xx-0C-xx-3D"		# DMZ 
TABLET="00:xx:3F:BD:79:xx"  	# tablet
LAPTOP="00:xx:43:70:xx:xx"	# my laptop

# Check argument passed to script
if [ "$1" == desk ]; then
  MAC=$DESK
elif [ "$1" == dave ]; then
  MAC=$DAVE
elif [ "$1" == dmz ]; then
  MAC=$DMZ
elif [ "$1" == tablet ]; then
  MAC=$TABLET
elif [ "$1" == laptop ]; then
  MAC=$DESK
else
  echo "No target by that name."
  MAC="not assigned"
fi

# Execute commands with proper MAC address
ifdown eth0
ifconfig eth0 hw ether $MAC
ifup eth0 
ifconfig eth0

```

---

### Post by Pig Monkey on 2005-10-17
Also,
*sudo apt-get install macchanger*

---

### Post by anthro398 on 2005-10-18
Oh, now you tell me.  Sheesh.  Should have known someone else had already done this.

---

### Post by elixirofLIFE on 2007-07-11
Yup, where to download macchanger?

---

### Post by slavik on 2007-07-12
IMO, save the script ... but I would've written it in perl, since you can use the hash data structure. :)

```

#!/usr/bin/perl

$arg =shift; #get first arguement

%maclist = { "bob" => 1, "jane" => 2 }

if ($maclist{$arg} eq "") { print "error\n"; exit 1; }

#change mac :) 
```

---

