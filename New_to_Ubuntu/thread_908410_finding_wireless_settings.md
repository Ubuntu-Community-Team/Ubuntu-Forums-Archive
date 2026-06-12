---
title: "finding wireless settings????"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-09-02
where can i find the files for the setup of the wireless,i need  them as a reference to set up my wireless in slackware.im currently using ubuntu 8.04.1 as my main os.slack as a testing ground.so basically im looking for EESID settings,etc.im hoping to use ubuntu settings in slackware ,so ican have wireless in both.but i cant find the network or wireless settings?
in slack its something like /etc/rc.d/inet1.or wireless.conf,anyway can somebody help me with this project???????please
Rick:(

---

### Post by nitro_n2o on 2008-09-02
This page might help [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) and you can always click on NetworkManager icon and save the settings by hand!

---

### Post by bobnutfield on 2008-09-02
What kind of wireless chip do you have?  Are you using a native driver or something like ndiswrapper?  Post this information and we might be able to give you some ideas.

This link will also help:

[http://wiki.linuxquestions.org/wiki/Slackware-Links]("http://wiki.linuxquestions.org/wiki/Slackware-Links")

---

### Post by rixtr66 on 2008-09-02
DUH!!sorry i should have mentioned what chip im using.im using an atheros chip,ndiswrapper works well with ubuntu,but doesnt play nice with slack!
basically im looking for information on how to put information into the card configuration,like eesid?,ip address?stuff like that,heres an example of what my configuration looks like;

# Default gateway IP address:
GATEWAY=""

# Change this to "yes" for debugging output to stdout.  Unfortunately,
# /sbin/hotplug seems to disable stdout so you'll only see debugging output
# when rc.inet1 is called directly.
DEBUG_ETH_UP="no"

## Example config information for wlan0.  Uncomment the lines you need and fill
## in your info.  (You may not need all of these for your wireless network)
IFNAME[4]="wlan0"
IPADDR[4]="192.168.3.12"
NETMASK[4]="255.255.255.0"
USE_DHCP[4]="yes"
#DHCP_HOSTNAME[4]="slackwireless"
DHCP_KEEPRESOLV[4]="yes"
DHCP_KEEPNTP[4]="yes"
DHCP_KEEPGW[4]="yes"
#DHCP_IPADDR[4]=""
WLAN_ESSID[4]=(extended network name) : My Network, any
    ESSID=""
WLAN_MODE[4]=Managed
WLAN_RATE[4]="54M auto"
WLAN_CHANNEL[4]="any"
WLAN_KEY[4]=883e-aa67-21 
#WLAN_IWPRIV[4]="set AuthMode=WPAPSK | set EncrypType=TKIP | set 
WPAPSK=96389dc66eaf7e6efd5b5523ae43c7925ff4df2f8b7099495192d44a774fda16"
WLAN_WPA[4]="wpa_supplicant"
WLAN_WPADRIVER[4]="ndiswrapper"

## Some examples of additional network parameters that you can use.
## Config information for wlan0:
IFNAME[4]="wlan0"              # Use a different interface name nstead of
                                # the default 'eth4'
#HWADDR[4]="00:01:23:45:67:89"  # Overrule the card's hardware MAC 
address
MTU[4]="1500"                      # The default MTU is 1500, but you 
might need
                                # 1360 when you use NAT'ed IPSec traffic.
DHCP_KEEPRESOLV[4]="yes"       # If you dont want /etc/resolv.conf overwritten
DHCP_KEEPNTP[4]="yes"          # If you don't want ntp.conf overwritten
#DHCP_KEEPGW[4]="yes"           # If you don't want the DHCP server to 
change
                                # your default gateway
#DHCP_IPADDR[4]=""              # Request a specific IP address from the DHCP
                                # server
WLAN_ESSID[4]=default_m         # Here, you can override _any_ parameter
                                # defined in rc.wireless.conf, by prepending
                                # 'WLAN_' to the parameter's name. Useful for
                                # those with multiple wireless interfaces.
WLAN_IWPRIV[4]="set AuthMode=WPAPSK | set EncrypType=TKIP | set 
WPAPSK=thekey"
                                # Some drivers require a private ioctl to be
                                # set through the iwpriv command. If more than
                                # one is required, you can place them in the
                                # IWPRIV parameter (separated with the pipe (|)
                                # character, see the example).

i really dont know how to set this up,i was hoping to get alook at my ubuntu configuration and copy it,but i cant find it.any ideas?
Rick

---

### Post by bobnutfield on 2008-09-03
Basically, all I did was this, as root:

> ifconfig wlan0 mode managed
       ifconfig wlan0 essid <the name of your network or router>
       ifconfig wlan0 key <your WEP or WPA key
       dhcpd wlan0

Note that dhcpd is used in Slackware instead of dhclient which is used in Ubuntu.
I saved these commands to a script, made the script executable, and place it in /etc/init.d/local so that it would bring up my wireless at boot automatically.  I did not have to edit the inet config files.

You might want to head over to linuxquestions.org as the Slackware forum there is the official Slackware forum.  You will find people there very helpful, but most are rather advanced users so have your questions reasonably well thought out and they will be glad to help.

---

### Post by bobnutfield on 2008-09-03
Basically, all I did was this, as root:

> ifconfig wlan0 mode managed
       ifconfig wlan0 essid <the name of your network or router>
       ifconfig wlan0 key <your WEP or WPA key
       dhcpd wlan0

Note that dhcpd is used in Slackware instead of dhclient which is used in Ubuntu.
I saved these commands to a script, made the script executable, and place it in /etc/init.d/local so that it would bring up my wireless at boot automatically.  I did not have to edit the inet config files.

You might want to head over to linuxquestions.org as the Slackware forum there is the official Slackware forum.  You will find people there very helpful, but most are rather advanced users so have your questions reasonably well thought out and they will be glad to help.

---

