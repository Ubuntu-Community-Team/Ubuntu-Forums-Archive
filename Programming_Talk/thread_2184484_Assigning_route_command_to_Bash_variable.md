---
title: "Assigning route command to Bash variable"
date: 2013-10-29
forum: Programming Talk
---

### Post by nahallac on 2013-10-29
Hello,

I'm trying to assign the results of three read commands to three separate variables, then feed those variables into a route command which I also store in a variable. I have explained that badly so here's what I mean:

```


echo "Enter the destination network for your environment-side static route - e.g. 10.5.0.0"
read _ROUTE_DEST_NET
 
echo "Enter the netmask for your destination network - e.g. 255.255.0.0"
read _ROUTE_DEST_MASK
 
echo "Enter the gateway for your destination network - e.g. 10.5.40.254"
read _ROUTE_DEST_GW
 
  
_ROUTE_ADD="route add -net $_ROUTE_DEST_NET netmask $_ROUTE_DEST_MASK gw $_ROUTE_DEST_GW dev eth1"
 
$_ROUTE_ADD
 
sed -i "0,/^$/s//$_ROUTE_ADD/1" /etc/rc.local

```

This is a portion of a bigger script but it's the only bit that's not working as it should. It chucks the route command into rc.local just fine but doesn't seem to run it interactively using the '$_ROUTE_ADD' line. I get a "siocaddrt network is unreachable" error; I thought it was the command failing but if I comment out the '$_ROUTE_ADD' line it still occurs.

I am running the script with the sudo command prefixed rather than elevating privileges for each of the necessary script lines. Does anyone have any ideas of how to debug this a bit further? My assumption is that storing the route command in _ROUTE_ADD is my problem but I'm unsure why.

Oh, I should also mention that the gateway I'm inputting is reachable from eth1 on the server I'm running this on.

---

### Post by nahallac on 2013-10-30
Anyone have any ideas?

---

### Post by steeldriver on 2013-10-30
Have you tried echoing the $_ROUTE_ADD command to see if it is malformed? Have you tried running the script with set -x (to output debug info)?

---

### Post by drmrgd on 2013-10-30
I actually looked at the code, and it seems the right string is passed:

Script results:
```

$ bash test.sh 
Enter the destination network for your environment-side static route: 
10.5.0.0
Enter the netmask for your destination network: 
255.255.0.0
Enter the gateway for your destination network: 
10.5.40.254
var1: 10.5.0.0
var2: 255.255.0.0
var3: 10.5.40.254
route add -new 10.5.0.0 netmask 255.255.0.0 gw 10.5.40.254 dev eth1

```

Contents of my dummy rc.local file:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
route add -new 10.5.0.0 netmask 255.255.0.0 gw 10.5.40.254 dev eth1
exit 0

```

 
 I actually think it's an issue with either calling that function from rc.local or something specific to the way the network is set up (i.e. the script is correct but doesn't make sense in the context of the OP's network). I don't know about how this network config works and what the actual route function does.  I would recommend checking to be sure that actual call is correct as I'm pretty sure the script you've written is doing what you think it is.

---

### Post by The Cog on 2013-10-30
I'm not clear on this: Is the problem that the interactive script fails to add the route, or that rc.local fails to add the route as the PC boots?

If the problem is that rc.local fails to add the route, your problem may be that networking has not reached a fully working state by the time the route add command is run. This could be especially true if you are using DHCP. You cannot add a route unless the network interface is up and on the same subnet as the gateway in the route command. 

I think that it is for this reason that route add commands are normally put into /etc/network/interfaces in an "up" clause for the interface, so the command will be run as and when the interface finally comes up. like this:
```
auto eth1
iface eth1 dhcp
up route add -net 10.5.0.0 netmask 255.255.0.0 gw 10.5.40.254 dev eth1
```

Note that it is **route add -net** and not **route add -new** as shown in your post.

---

### Post by drmrgd on 2013-10-30
> **The Cog said:**
> I'm not clear on this: Is the problem that the interactive script fails to add the route, or that rc.local fails to add the route as the PC boots?

If the problem is that rc.local fails to add the route, your problem may be that networking has not reached a fully working state by the time the route add command is run. This could be especially true if you are using DHCP. You cannot add a route unless the network interface is up and on the same subnet as the gateway in the route command. 

I think that it is for this reason that route add commands are normally put into /etc/network/interfaces in an "up" clause for the interface, so the command will be run as and when the interface finally comes up. like this:
```
auto eth1
iface eth1 dhcp
up route add -net 10.5.0.0 netmask 255.255.0.0 gw 10.5.40.254 dev eth1
```

Note that it is **route add -net** and not **route add -new** as shown in your post.

Don't follow me on that.  I'm just trying to help test the script, and it looks like I mistyped 'net'; the OP had it right.  I have a heck of a time figuring out the difference between the 't' and 'w' keys on my keyboard it seems, as I often type 'not' when I mean 'now' (which does get me in trouble!).  Anyway, back to the regularly scheduled program, already in progress...

Based on what you say, though, it may be that the bash script is OK, but the way it's called is not.  Very good info; thanks!

---

### Post by nahallac on 2013-10-31
Ah! I make the not/now mistake often too. I could understand if 't' and 'w' were next to each other...

Thank you both for your help so far. I'm not a regular Linux sysadmin so while I know the way to do certain things I don't necessarily know the preferred way always. As I said the route addition is part of a bigger script, at the start of which I'm changing IPs in /etc/network/interfaces and at the end of which I'm restarting each interface using ifdown && ifup. Commenting those lines out has shown that eth1 isn't actually up when the route command is run so obviously it's not going to know about the destination net! I will show the whole script shortly as the feedback I've had so far has been enlightening.

---

