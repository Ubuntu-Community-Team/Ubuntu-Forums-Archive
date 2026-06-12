---
title: "HOWTO: Connet to GPRS network using a mobile phone"
date: 2009-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by fwre01 on 2009-05-04
System Details and Equipment:
-----------------------------
Dell Inspiron 1501
Ubuntu 7.10 Gusty
kernel 2.6.22-14-generic 
pppd version 2.4.4
wvdial version 1.56
---------------
Nokia 6230i
Samsung D600
---------------

Prerequisites
-------------
Connect your phone using its USB cable and check that your laptop can see and use your phone as a modem, issue the command **lsusb**, and you should see a similar output

```
user@laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 04e8:663e Samsung Electronics Co., Ltd
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0421:0428 Nokia Mobile Phones 
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
user@laptop:~$
```

The two numbers that get returned for the Nokia (0421:0428) indicate the Vendor ID and Product ID respectivley, and indicates your computer regonises the devices. To identify the max speed of the modem, and /dev file, issue the command "wvdialconf" or look in System -> Preferences -> Hardware Information

```
user@laptop:~$ wvdialconf
Scanning your serial ports for a modem.

ttyACM0<*1>: Max speed is 460800; that should be safe.
Found an USB modem on /dev/ttyACM0

ttyACM1<*1>: Max speed is 460800; that should be safe.
Found an USB modem on /dev/ttyACM1
```

Configuration
--------------

Next you will have to create two files 

```
gksu gedit /etc/ppp/peers/gprs
```

This should be the contents of the gprs file, ensure you go through the options, i have commented the commands to make them more descriptive.

```
# This file contains all the parameters pppd will pass to the modem to establish the GPRS connection
#
# The user and password has been commented out becasue the "noauth" command is being used
#user web 						
#password web
#
# This places a default route in the routing table with the peer as the gateway
defaultroute
#
# This can also be used to replace existing default routes
#replacedefaultroute						
#
# Serial Modem to use
/dev/ttyACM0	
#
# Call this chat script to issue the modem commands				
connect "/usr/sbin/chat -v -f /etc/ppp/gprsmodem.chat"
#
# Enable debugging to /var/log/messages
debug
#
# Enable kernel debugging level 4
kdebug 4
#
#
ipcp-no-addresses
#
#
noipdefault
#
# Do not require the peer to use authentication
noauth
#
# Disable Van Jacobson style TCP/IP header compression in both TX and RX
novj
#
# Disable compression control protocol,if peer doesnt accept requests for CCP from pppd						 
noccp
#
# Use RTS/CTS hardware flow control						 	
crtscts
#
# I cant find what this means, but if its not included there is no output to the command prompt
modem -detach
#
# Use DNS given to peer and rewrite /etc/resolv.conf
usepeerdns	
#
# pppd will accept the peers idea of its remote ip address
ipcp-accept-remote					 	
#
# pppd will accept the peers idea of its local ip address			     
ipcp-accept-local
#
```


```
gksu gedit /etc/ppp/gprsmodem.chat
```

Contents of the gprsmodem.chat file

```
# GPRS Chat File, contains all parameters that /usr/sbin/chat will pass to the modem to create the GPRS connection
#
#
# Abort Strings
'ABORT' 'BUSY'
'ABORT' 'ERROR'
'ABORT' 'NO ANSWER'
'ABORT' 'NO CARRIER'
'ABORT' 'NO DIALTONE'
'ABORT' 'Invalid Login'
'ABORT' 'Login incorrect'
'TIMEOUT' '10'
#
# Modem Init
'' 'ATZ'
#
#
'OK' 'ATM1L1'
#
# "internet" represents Vodafone's APN, whereas "general.t-mobile.uk" is T-mobiles UK APN address
'OK' 'AT&f+cgdcont=1,"IP","internet","",0,0'
'OK' 'ATDT*99***1#'
'CONNECT' ''
```

Once these two files have been created and saved you can call the connection by issuing 

```
user@laptop:~$ pppd call gprs
```

I have tested two different phones on two different GSM networks, the concept should be the same for any phone with GPRS capabilities, the only setting i had to change was the UK APN address. Here is a good site for [UK APN Addresses]("http://www.filesaveas.com/gprs.html")

Enjoy!

fwre01

---

### Post by jpeddicord on 2009-05-11
I've made a couple of small edits to your tutorial, specifically changing 'sudo' to 'gksu' (see [this page]("http://www.psychocats.net/ubuntu/graphicalsudo") for more info) and few spacing inserts (because I'm a neat freak - no other explanation :P).

Thank you for your tutorial contribution! :)

---

