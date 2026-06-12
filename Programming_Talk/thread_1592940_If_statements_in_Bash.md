---
title: "If statements in Bash"
date: 2010-10-11
forum: Programming Talk
---

### Post by ThatBum on 2010-10-11
Hey hey hey. I recently put PDAnet on my jailbroken iPhone, which is a psudo-tethering kind of thing that needs an Ad-Hoc network on the host machine and DHCP active for it to work. I got this working after awhile by [finding a script for it]("http://ubuntuforums.org/showpost.php?p=6253914&postcount=5") (because Network Manager was having a conniption fit over getting DHCP working right). However, this is an old script and doesn't work on 10.04, so I mutilated it a little and added some stuff..and this is what I have (it is run as root):

```
#!/bin/bash

case "$1" in
    start)
    ifconfig eth1 down
    service network-manager stop
    iwconfig eth1 mode ad-hoc channel 4 essid 'ModemNet' key 8887942284
    ifconfig eth1 up
    echo "Press Enter when PDAnet is connected to start DHCP..." && read foo
    dhclient eth1
    dig @8.8.8.8 www.google.com
    ;;
    stop)
    ifconfig eth1 down
    iwconfig eth1 mode managed
    service network-manager start
    ifconfig eth1 up
    ;;
    status)
    STATUS="$(sudo iwlist eth1 sc | grep Hoc)"
    ON="Mode:Ad-Hoc"
    OFF=""
    if [ $STATUS == $ON ]
    then
    echo "PDAnet is on; Network Manager is off."
    fi
    if [ $STATUS == $OFF ]
    then
    echo "PDAnet is off; Network Manager is on."
    fi
    ;;
    *)
    echo "Usage: /etc/init.d/pdanet {start|stop|status}"
    exit 1
    ;;
esac

exit 0
```The problem with this is, it only seems to work if I run "sudo pdanet start", "sudo pdanet stop", and "sudo pdanet start" again. If I only run it once, the Ad-Hoc network isn't there, although it reports it ran successfully and starts DHCP and all that. I know it's just not there because I can scan it from another computer and it's absent. The second time through it creates "ModemNet" perfectly fine. I can't really tell what's going on, because there's no useful output.

Also, I tried to make a status function, but I appear to be epically failing at it. I can't see what I'm doing wrong...can someone help out?

---

### Post by Reiger on 2010-10-11
I would do the status case differently:

```

status=`sudo iwlist eth1 sc | grep Mode:Ad-Hoc`
if [ -z $status ]
then
  echo "PDAnet is off; Network Manager is on."
else
  echo "PDAnet is on; Network Manager is off."
fi

```

---

### Post by ThatBum on 2010-10-11
> **Reiger said:**
> I would do the status case differently:

```

status=`sudo iwlist eth1 sc | grep Mode:Ad-Hoc`
if [ -z $status ]
then
  echo "PDAnet is off; Network Manager is on."
else
  echo "PDAnet is on; Network Manager is off."
fi

```

That doesn't seem to be doing anything, it doesn't produce any output if the network is on or off. At least there isn't any errors.

I found a better way than iwlist to find the status of the network, too. I used 'iwconfig eth1', so the result comes back faster, and also only the network it's connected to comes back, so there won't be a false positive on status if there's another Ad-Hoc network in range.

---

### Post by Reiger on 2010-10-11
Oh there could be an error in the `sudo iwlist... grep Mode:Ad-Hoc` command which prevents it from reaching the if.

Anyway the **if [ -z $status ]** construct simply tests whether or not the grep query produced any output (the status string will be empty if not output is produced, making the -z condition evaluate to true). So it's really a straightforward way to merge the two original if's and also make it more clear what you are actually testing for.

---

### Post by slakkie on 2010-10-11
You can use the exit code of grep to determine if status is set as well. if grep doesn't grep anything it returns 1 otherwise 0;


```

echo "test" | grep -q test
echo $?

```

This will echo 0

```

echo "t3st" | grep -q test
echo $?

```

This will echo 1

This said, I would do something like this:

```

#!/usr/bin/env bash
set -x

INT=wlan0

check_root() {
    if [ $UID -ne 0 ] ; then
        echo "Please run this as root" >&2
        exit 3
    fi
}


start() {
    # Stop everything first
    stop

    ifconfig $INT 0.0.0.0 down
    service network-manager stop

    iwconfig $INT mode ad-hoc channel 4 essid 'ModemNet' key 8887942284
    ifconfig $INT up

    echo "Press Enter when PDAnet is connected to start DHCP..." && read foo

    dhclient $INT
    dig @8.8.8.8 www.google.com

}

stop() {
    ifconfig $INT 0.0.0.0 down
    iwconfig $INT mode managed
    service network-manager start
    ifconfig $INT up
}

restart() {
    start
}

status() {
    iwlist $INT sc | grep -q "Mode:Ad-Hoc"
    PDANET=$?

    # Could be a different process, don't use NM myself.
    pgrep network-manager >/dev/null
    NM=$?

    if [ $PDANET -eq 0 ] ; then
        echo -n "PDAnet is on; "
    else 
        echo -n "PDAnet is off; "
    fi

    if [ $NM -eq 0 ] ; then
        echo "Network Manager is on."
    else
        echo "Network Manager is off."
    fi
}


case "$1" in
    start|stop|restart) check_root ; $1 ;;
    status) $1;;
    *)
        echo "Usage: /etc/init.d/pdanet {start|stop|restart|status}"
        exit 1
    ;;
esac

exit $?

```

The problem with your if statement for the status is seen by this (use of set -x helps when debuging shell scripts, set +x is to set debugging off btw :)).

```

$ sudo ./pdanet.sh status
+ INT=wlan0
+ '[' 0 -ne 0 ']'
+ case "$1" in
+ status
++ grep Mode:Ad-Hoc
++ iwlist wlan0 sc
+ STATUS='                    Mode:Ad-Hoc'
+ '[' 0 -eq 0 ']'
+ echo 'PDAnet is on; Network Manager is off.'
PDAnet is on; Network Manager is off.
+ exit 0

```

As you can see there are a lot of spaces, after your initial grep you should remove all of the leading spaces, eg:

```

STATUS=$(iwlist $INT sc | grep "Mode:Ad-Hoc"| sed -e 's/^[[:space:]]\+//g')

```

I would use 
```

iwlist $INT sc | grep -q "Mode:Ad-Hoc" 

```

and then check the exit code. If grep has it, then you have an adhoc mode, otherwise you don't, so there is no need to compare the output of the grep command.

---

### Post by ThatBum on 2010-10-11
Man, this is complicated...but I see what you're getting at.

Yeah, I used to not use NM too, I had WiCD, but that gave me too much guff when changing networks and things. I have WiCD on my desktop though, because it's quicker than NM.

I don't even know the NM process, I just killed it with 'service network-manager stop'. I can't find it, all I know is the client, nm-applet.

The root detection doesn't seem to be working, however. I get:
```
[: 70: -ne: unexpected operator
```for that part of the script.

EDIT: Nevermind, I figured it out:
```
uid=$(/usr/bin/id -u) && [ "$uid" = "0" ] ||
    { echo "must be root"; exit 3; }
```Oh and the process for NM is NetworkManager.

EDIT2: Alright, this is what I have, and it works:

```
#!/usr/bin/env bash
# This script creates an Ad-Hoc network with DHCP to use with PDAnet
# on the iPhone. This turns the iPhone into a router and its 3G
# connection into a modem. It is effectively unofficial tethering. 

INT=wlan0

check_root() {
uid=$(/usr/bin/id -u) && [ "$uid" = "0" ] ||
    { echo "You are not root, go away."; exit 3; }
}


start() {
# Shut everything down first
    echo "Putting $INT down..."
    ifconfig $INT 0.0.0.0 down
    echo "$INT is down."
    echo "Stopping NetworkManager..."
    service network-manager stop > /dev/null
    echo "NetworkManager stopped."
    echo "Creating ModemNet..."
    iwconfig $INT mode ad-hoc channel 4 essid 'ModemNet' key 8887942284
    echo "ModemNat created."
    echo "Putting $INT up..."
    ifconfig $INT up
    echo "$INT is up."
    echo "Press Enter when PDAnet is connected to start DHCP..." && read foo
# Start DHCP and make a DNS lookup to start DNS correctly.
    echo "Starting DHCP..."
    dhclient $INT > /dev/null
    echo "DHCP connected."
    echo "Initializing DNS..." 
    dig @8.8.8.8 www.google.com > /dev/null
    echo "DNS Initialized."
    echo "PDAnet connected!" && sleep 3

}

stop() {
    echo "Putting $INT down..."
    ifconfig $INT 0.0.0.0 down
    echo "Successful"
    echo "Setting $INT mode to managed..."
    iwconfig $INT mode managed
    echo "Successful"
    echo "Starting network-manager..."
    service network-manager start > /dev/null
    echo "Successful"
    echo "Putting $INT up"
    ifconfig $INT up
    echo "Successful"
    echo "PDAnet disconnected."
}

restart() {
    start
}

status() {
    iwconfig $INT | grep -q "Mode:Ad-Hoc"
    PDANET=$?
    pgrep NetworkManager >/dev/null
    NM=$?

    if [ $PDANET -eq 0 ] ; then
        echo -n "PDAnet is on; "
    else 
        echo -n "PDAnet is off; "
    fi

    if [ $NM -eq 0 ] ; then
        echo "Network Manager is on."
    else
        echo "Network Manager is off."
    fi
}


case "$1" in
    start|stop|restart) check_root ; $1 ;;
    status) $1;;
    *)
        echo "Usage: /etc/init.d/pdanet {start|stop|restart|status}"
        exit 1
    ;;
esac

exit $?
```The reason for all that output, is I'm giving it to some of my friends in addition to using it myself, and they are a bit less tech-savvy...thanks for all the help!

One thing though, how do I put a timeout kind of thing for dhclient?

---

### Post by slakkie on 2010-10-12
[http://linux.die.net/man/8/dhclient](http://linux.die.net/man/8/dhclient)

dhclient -T 30 

> 
The -T <timeout> option allows you to specify the time after which the dhclient will decide that no DHCP servers can be contacted when no responses have been received. It is equivalent to the
timeout <integer>;
dhclient.conf statement, and will override any such statements in dhclient.conf.
This option is provided as a Red Hat extension.


---

### Post by ThatBum on 2010-10-12
Thanks! Oh, and I figured out [how to get USB mode working with PDAnet]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1351548"), so I can bypass all this wireless stuff alltogether, although it's still useful if I want to connect more than one device, or I don't have Apple's proprietary cable on me or whatever. I made a script for that too, using this one as a template:

```
#!/usr/bin/env bash
# This script connects to PDAnet on iPhone via USB.

set +x
check_root() {
uid=$(/usr/bin/id -u) && [ "$uid" = "0" ] ||
{ echo "You are not root, go away."; exit 3; }
}
start() {
    ifconfig | grep ppp >/dev/null
    STATUS=$?
if [ $STATUS -eq 0 ] ; then
    zenity --info --text "PDAnet already running; doing nothing."
else
    echo "Connecting..."
    pon umux2007 > /dev/null
    sleep 3
    ifconfig | grep ppp > /dev/null
    STATUS=$?
if [ $STATUS -eq 1 ] ; then
    zenity --error --text "No PDAnet device detected. Is is plugged in and in USB mode?"
    exit 2
fi
    dig @8.8.8.8 www.google.com +time=1> /dev/null
    DNS=$?
if [ $DNS -eq 0 ] ; then
    zenity --info --text "PDAnet connected!"
else
    zenity --warning --text "PDAnet is connected, but DNS didn't resolve. Are you in an area with cell coverage?"
fi
fi
}
stop() {
    ifconfig | grep ppp > /dev/null
    STATUS=$?
if [ $STATUS -eq 0 ] ; then
    echo "Disconnecting..."
    poff umux2007 > /dev/null
    zenity --info --text "PDAnet disconnected."
else
    zenity --info --text "PDAnet not running; doing nothing."
    exit 3
fi
}
restart() {
    ifconfig | grep ppp > /dev/null
    STATUS=$?
if [ $STATUS -eq 0 ] ; then
    echo "Disconnecting..."
    poff umux2007 > /dev/null
    sleep 3
    start
else
    zenity --info --text "PDAnet not running; doing nothing."
    exit 4
fi
}
status() {
ifconfig | grep ppp >/dev/null
STATUS=$?
if [ $STATUS -eq 0 ] ; then
    echo "PDAnet is on"
else 
    echo "PDAnet is off"
fi
}

case "$1" in
    start|stop|restart) check_root ; $1 ;;
    status) $1;;
*)
    echo "Usage: $(basename $0) {start|stop|restart|status}"
    exit 1
    ;;
esac
exit 0
```And this is the new-original WiFi script:

```
#!/usr/bin/env bash
# This script creates an Ad-Hoc network with DHCP to use with PDAnet
# on the iPhone. This turns the iPhone into a router and its 3G
# connection into a modem. It is effectively unofficial tethering.
set +x

INT=wlan0

check_root() {
uid=$(/usr/bin/id -u) && [ "$uid" = "0" ] ||
{ echo "You are not root, go away."; exit 3; }
}

start() {
    iwconfig $INT | grep -q "PDAnet"
    PDANET=$?
if [ $PDANET -eq 0 ] ; then
    zenity --info --text "PDAnet is already running; doing nothing."
    exit 4
else
# Shut everything down first
    echo "Putting $INT down..."
    ifconfig $INT 0.0.0.0 down
    echo "$INT is down."
    echo "Stopping NetworkManager..."
    service network-manager stop
    echo "Creating PDAnet network..."
    iwconfig $INT mode ad-hoc channel 4 essid 'PDAnet' key 1234567890
    echo "PDAnet network created."
    echo "Putting $INT up..."
    ifconfig $INT up
    echo "$INT is up."
    zenity --info --text "Connect the PDAnet device to the network "PDAnet" using key 1234567890, and click OK to start DHCP."
# Start DHCP and make a DNS lookup to start DNS correctly.
    echo "Starting DHCP..."
    rm /tmp/dhclientpda 2> /dev/null
    dhclient $INT &>/tmp/dhclientpda
    grep DHCPOFFERS /tmp/dhclientpda -q
    DHCP=$?
    rm /tmp/dhclientpda 2> /dev/null
if [ $DHCP -eq 1 ] ; then 
    echo "DHCP connected."
    sleep 3
else
    echo "Problem with DHCP."
    zenity --error --text "DHCP timed out. Is PDAnet connected to the network?"
    exit 2
fi
    echo "Initializing DNS..." 
    dig @8.8.8.8 www.google.com +time=1 >/dev/null
    DNS=$?
if [ $DNS -eq 0 ] ; then
    echo "DNS Initialized."
    zenity --info --text "PDAnet connected!"
else
    echo "Problem with DNS."
    zenity --warning --text "PDAnet is connected, but DNS is not resolving. Are you in an area with data coverage?"
fi
fi
rm /tmp/dhclient 2> /dev/null
}

stop() {
    iwconfig $INT | grep -q "PDAnet"
    PDANET=$?
if [ $PDANET -eq 1 ] ; then
    zenity --info --text "PDAnet is not running; doing nothing."
    exit 3
else
    echo "Putting $INT down..."
    ifconfig $INT 0.0.0.0 down
    echo "$INT is down."
    echo "Setting $INT mode to managed..."
    iwconfig $INT mode managed
    echo "$INT set to managed."
    echo "Starting network-manager..."
    service network-manager start
    echo "Putting $INT up"
    ifconfig $INT up
    echo "$INT is up."
    zenity --info --text "PDAnet disconnected."
fi
}

restart() {
    start
}

status() {
    iwconfig $INT | grep -q "PDAnet"
    PDANET=$?
    pgrep NetworkManager > /dev/null
    NM=$?
if [ $PDANET -eq 0 ] ; then
    echo -n "PDAnet is on; "
else 
    echo -n "PDAnet is off; "
fi
if [ $NM -eq 0 ] ; then
    echo "Network Manager is on."
else
    echo "Network Manager is off."
fi
}


case "$1" in
    start|stop|restart|status) check_root ; $1 ;;
#    status) $1;;
# iwconfig needs root with some wireless drivers...
*)
    echo "Usage: $(basename $0) {start|stop|restart|status}"
    exit 1
;;
esac
exit 0
```Also, I upgraded to Maverick, and I've noticed that NetworkManager now has a checkbox when you're making a connection that says 'Require IPv4 addressing for this connection to complete.' So now NM won't have a fit about making an Ad-Hoc network with DHCP if I turn that off. Though, I still can't figure out how to start an Ad-Hoc network from a saved profile in NetworkManager, I can only start a new one and it ignores the saved one. if I can figure that out, this wireless script will be effectively depreciated.

Edit: Nope, just tried it, still is not stable...also, my dhclient doesn't have a -T option. Bah. It does have a timeout option in dhclient.conf, however.

Edit2: I made them a bit nicer with zenity and things. I think I'm about done working on it.

---

### Post by slakkie on 2010-10-12
btw, in stead of having to type in a name of the script in the Usage thingy, you can use the following:

echo "Usage: $(basename $0) .."

---

