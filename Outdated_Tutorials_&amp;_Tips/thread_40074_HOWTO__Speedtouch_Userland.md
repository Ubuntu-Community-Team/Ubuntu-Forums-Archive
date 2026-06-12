---
title: "HOWTO : Speedtouch Userland"
date: 2005-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Gouchi on 2005-06-07
How to configure aDSL connection with Speedtouch USB ?


_Requirements :_

[pppoe](http://packages.ubuntu.com/hoary/net/pppoe) (64,2 Ko)
[speedtouch](http://packages.ubuntu.com/hoary/net/speedtouch) (94,9 Ko) 

Download Thomson's Modem firmware
What you need to download is the modem's microcode provided with Thomson's drivers. You have two possibilities. It can be found in the form of two files:

    * mgmt.o from [Speedtouchdsl](http://www.speedtouchdsl.com/dvrreg_lx.htm) 
    *  alcaudsl.sys file found in the Windows package

(If your modem is already running under windows, you can avoid downloading it by taking the file in c:\windows\system or c:\windows\system32).

1) _Install Ubuntu Package_

```
dpkg -i pppoe_3.5-4ubuntu1_i386.deb
```
```
dpkg -i speedtouch_1.3.1-1_i386.deb
``` 

2)_ Copy Thomson's Modem firmware_

```
cp alcaudsl.sys /usr/share/speedtouch
```

3) _Disable Speedtouch Kernel Module_

```
rmmod speedtch
``` 
```
echo "speedtch" >> /etc/hotplug/blacklist
```

4) _Connection Configuration_

/etc/ppp/options
 (backup the old, mv /etc/ppp/options /etc/ppp/options.bak)

gedit /etc/ppp/options and add :
```
usepeerdns
noauth
lock
noipdefault

``` 


/etc/ppp/peers/adsl 
(create /etc/ppp/peers/adsl) and add :

gedit /etc/ppp/peers/adsl 
```

#
#
# This file could be rename but its place is under /etc/ppp/peers
# To connect to Internet using this configuration file
# pppd call adsl, where "adsl" stands for the name of this file
#

debug
kdebug 1
noipdefault
defaultroute
pty "/usr/sbin/pppoa3 -m 1 -c -vpi **X** -vci **Y**"
sync
user "**login**"
noauth
noaccomp
nopcomp
noccp
novj
holdoff 4
persist
maxfail 25
usepeerdns

```

add your login and [VPI/VCI values](http://damien.bergamini.free.fr/ueagle/vpivci.html)  for X and Y


/etc/ppp/chap-secrets 
(Modify /etc/ppp/chap-secrets ) and add :
```

# client server secret IP addresses
"**your_login_here**" "*" "**your_password_here**" "*"

```
 

5) _Boot connection_

Create a script to launch the connection at boot time.

gedit /etc/init.d/net.sh
```

#!/bin/sh
echo "Loading some modules"
modprobe ppp_generic
modprobe ppp_synctty
modprobe n_hdlc
echo "Starting ADSL Connection"
modem_run -m -f /usr/share/speedtouch/alcaudsl.sys && pppd call adsl&

``` 

```
cd /etc/init.d
ln -s net.sh ../rc2.d/S99net

``` 
```
chmod +x net.sh
``` 

To check if connection works, try :
```
ifconfig -a
``` 
for ppp0.

More information [here](http://speedtouch.sourceforge.net/index.php?/docs.en.html)

---

