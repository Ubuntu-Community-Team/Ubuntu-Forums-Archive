---
title: "Help with internet connection script"
date: 2004-12-29
forum: Programming Talk
---

### Post by Programmer on 2004-12-29
Hello all :-)
As you know, the cable internet in Israel is a little bit more complicated so i have written a script that do the job for me :-)
Here is the script:

------------------------------------------------------------------------------------------------

#! /bin/tcsh
#
# This script was written by Alexander Sirotin
# email: [email]sirotin@gmail.com[/email]
#

# The path to pptp and route commands
set PPTP = "/root/bin/pptp"
set ROUTE = "/sbin/route"

# Some settings
set HOST = "192.117.122.13" # pns3.actcom.net.il
set USER = "sprog@CActcom"
set IFACE = "eth0"

# Configure the firewall options
/root/bin/net-firewall.sh

# Configure the internet sharing
/root/bin/net-share.sh

# Get the cables gateway
set CABLEGW = `ifconfig $IFACE | grep "inet addr:" | cut -c21-36 | cut -d" " -f1`

# Configure the routing table
$ROUTE del -net 0.0.0
$ROUTE add $HOST gw $CABLEGW

# Open pptp tunnel
$PPTP $HOST debug user $USER defaultroute noauth

# Save DNS information
cp -f /root/resolv.conf /etc/

# Wait until we'll have a public ip address
sleep 7

# Get the ip address and print it
set IP = `ifconfig ppp0 | grep "inet addr:" | cut -c21-36` | cut -d" " -f1`
echo "Connection Established. Your IP is $IP"

------------------------------------------------------------------------------------------------

My question is how can i convert this script from tcsh to bash (i don't know bash) ?
Thanks.

---

### Post by wtd on 2004-12-29
I'm not a shell scrip expert, but I think in this case you really need only elide the "set" for variables, and of course alter the #!/bin/tcsh line.

---

### Post by Programmer on 2004-12-30
I know about the "set" but do i need to change the lines with the pipelines ?
for example this one:

set CABLEGW = `ifconfig $IFACE | grep "inet addr:" | cut -c21-36 | cut -d" " -f1`

Thanks, Alexander.

---

### Post by zeroK on 2004-12-30
[QUOTE=Programmer]I know about the "set" but do i need to change the lines with the pipelines ?
for example this one:

set CABLEGW = `ifconfig $IFACE | grep "inet addr:" | cut -c21-36 | cut -d" " -f1`

Thanks, Alexander.[/QUOTE]
 Looks ok to me :-) First I thought that perhaps some spaces between -c and the list are necessary but it seems to work also without these spaces :-)

---

### Post by Programmer on 2005-01-04
ok thanks to all of you :-)

---

### Post by 3david on 2005-10-23
does this script work?
i'm also in israel, trying to connect to my cable internet isp,
what else did u need to install for it to work?

---

### Post by LordHunter317 on 2005-10-23
You know, PPTP can do all of that for you, no script required.

---

### Post by 3david on 2005-10-23
how do I make pptp do all that?

---

### Post by zinc00 on 2007-09-26
Hi,
I have a cable connection 2 the Internet, (works fine with XP) I'm using ubuntu live cd 7.04. I can't connect 2 the Internet,my ISP gave me this, but i get errors with no avail, pls help. 
(I was told 2 copy this 2 a file on my Desktop,named "cablestart". Help would be appreciated!! 

# This is a script used for connecting to Bezeq International through cable
# connection using the point to point tunnel protocol (PPTP) protocol.
# This script assumes the presence of a ppp daemon with MPPE support, and
# is written to correspond to pptp-linux 1.70, though it should work with
# any version above 1.5.
#
# Before using the script you should change the USERNAME variable to the
# user name you recieved from Bezeq International, and the IF variable to
# the name of the network interface card you will be using for the connection.
#
# Unless you've set the permissions in accordance, this script will only work
# when run as root.
#
# The script assumes that a PAP-secrets file already exists and that it
# contains an accurate password.
#
# This script runs a basic dialing procedure and does not support any error
# handling, therefor it's not recommended to make modifications any parts of
# the script other then the USERNAME and IF variables unless you know what you
# are doing.
#
# Bezeq International is not responsible for any demage that might result from
# running this script.
#
# Script by Shai Wyborski.

#!/bin/bash

#dialing properties
USERNAME=temp1
IF=eth0
ROUTE=`which route`

#reset the interface
/sbin/ifdown $IF
/sbin/ifup $IF

#inner routing
CABLEGW=`/sbin/route -n | grep ^0.0.0.0 | awk '{print$2}'`
PNS=`host tevelbi.bezeqint.net 192.168.101.101| awk '{print $4}' | grep .| head -1`
$ROUTE add -host $PNS gw $CABLEGW

#establish connection
/usr/sbin/pptp $PNS user $USERNAME mtu 1410 mru 1460 noauth usepeerdns &

echo Please standby...
sleep 10

#rerouting
NEWGW=`cat /var/log/messages | grep -i remote | tail -1 | awk '{print $9}'`
$ROUTE add default gw $NEWGW
OLDROUTE=`route -n | grep ^0.0.0.0 | awk '{print $2}' | tail -1`
$ROUTE del default gw $OLDROUTE
echo "nameserver 192.115.106.35" > /etc/resolv.conf
echo "nameserver 62.219.186.7" >> /etc/resolv.conf

---

