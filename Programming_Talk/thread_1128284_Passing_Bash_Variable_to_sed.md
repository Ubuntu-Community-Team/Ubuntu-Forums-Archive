---
title: "Passing Bash Variable to sed"
date: 2009-04-17
forum: Programming Talk
---

### Post by Das Oracle on 2009-04-17
Hey guys,

I have a variable in my bash script that I am trying to pass to sed.

```
 sed 's/lease ${1} {/lease ${1} 0 {/g' /home/helpdesk/dhcpd.leases.mod > /home/helpdesk/dhcpd.leases.mod.tmp
```

however it does not seem to do the replacement.

---

### Post by Arndt on 2009-04-17
> **Das Oracle said:**
> Hey guys,

I have a variable in my bash script that I am trying to pass to sed.

```
 sed 's/lease ${1} {/lease ${1} 0 {/g' /home/helpdesk/dhcpd.leases.mod > /home/helpdesk/dhcpd.leases.mod.tmp
```

however it does not seem to do the replacement.

Variable expansion doesn't occur in single-quoted strings. Use double-quotes instead:

```
 sed "s/lease ${1} {/lease ${1} 0 {/g" /home/helpdesk/dhcpd.leases.mod > /home/helpdesk/dhcpd.leases.mod.tmp
```

---

### Post by Das Oracle on 2009-04-17
Thanks for the reply, although that doesn't seem to work. To give you an overview of what I am doing: I am using dhcpd as a dhcp server and I want to make a copy of the dhcpd.leases file for editing, ping all active ip leases, and modify the copied dhcpd.leases file if they are up or not. Here is my script:



```

#!/bin/bash

#pings IP addresses from a dhcpd.leases file
#and records it in each lease entry


function pinghost () {
 cp /home/helpdesk/dhcpd.leases.mod /home/helpdesk/dhcpd.leases.mod.tmp
 ping -c 1 -w 1 $1 &>/dev/null
 if [ $? -ne 0 ] ; then
  sed "s/lease ${1} {/lease ${1} 0 {/g" /home/helpdesk/dhcpd.leases.mod > /home/helpdesk/dhcpd.leases.mod.tmp
 else
  sed "s/lease ${1} {/lease ${1} 1 {/g" /home/helpdesk/dhcpd.leases.mod > /home/helpdesk/dhcpd.leases.mod.tmp
 fi
 mv /home/helpdesk/dhcpd.leases.mod.tmp /home/helpdesk/dhcpd.leases.mod
}

cp /var/lib/dhcp3/dhcpd.leases /home/helpdesk/dhcpd.leases.mod
cat /home/helpdesk/dhcpd.leases |
 while read line; do
  if [ "${line:0:5}" = "lease" ]; then
   ipaddress="${line:6:13}"
  fi

  if [ "${line:0:20}" = "binding state active" ]; then
   pinghost "$ipaddress"
  fi
 done

```

---

### Post by Arndt on 2009-04-17
> **Das Oracle said:**
> Thanks for the reply, although that doesn't seem to work. To give you an overview of what I am doing: I am using dhcpd as a dhcp server and I want to make a copy of the dhcpd.leases file for editing, ping all active ip leases, and modify the copied dhcpd.leases file if they are up or not. Here is my script:



```

#!/bin/bash

#pings IP addresses from a dhcpd.leases file
#and records it in each lease entry


function pinghost () {
 cp /home/helpdesk/dhcpd.leases.mod /home/helpdesk/dhcpd.leases.mod.tmp
 ping -c 1 -w 1 $1 &>/dev/null
 if [ $? -ne 0 ] ; then
  sed "s/lease ${1} {/lease ${1} 0 {/g" /home/helpdesk/dhcpd.leases.mod > /home/helpdesk/dhcpd.leases.mod.tmp
 else
  sed "s/lease ${1} {/lease ${1} 1 {/g" /home/helpdesk/dhcpd.leases.mod > /home/helpdesk/dhcpd.leases.mod.tmp
 fi
 mv /home/helpdesk/dhcpd.leases.mod.tmp /home/helpdesk/dhcpd.leases.mod
}

cp /var/lib/dhcp3/dhcpd.leases /home/helpdesk/dhcpd.leases.mod
cat /home/helpdesk/dhcpd.leases |
 while read line; do
  if [ "${line:0:5}" = "lease" ]; then
   ipaddress="${line:6:13}"
  fi

  if [ "${line:0:20}" = "binding state active" ]; then
   pinghost "$ipaddress"
  fi
 done

```

To see what happens, add an 'echo' line:
```
  echo "s/lease ${1} {/lease ${1} 0 {/g"
```
to see if the expanded string really is what it should be.

---

