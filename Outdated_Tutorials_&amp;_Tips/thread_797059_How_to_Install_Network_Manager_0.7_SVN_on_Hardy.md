---
title: "How to: Install Network Manager 0.7 SVN on Hardy"
date: 2008-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Darrena on 2008-05-16
Alexander Sack is creating packages for Hardy of Network Manager 0.7 SVN Snapshots.   To install them add the following lines to your /etc/apt/sources.list:
```

deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main

```

Update the your local repositories with:
```
sudo apt-get update
```

Then update the system:
```
sudo apt-get upgrade
```

This will pull in an updated wpa_supplicant package along with the updated Network-Manager package.  


Notes:
1) Make sure you can configure your network by hand if this breaks your networking so you can recover it.   If you can't afford to be without network connectivity do not try this!
2) The VPN plugins can be downloaded from SVN.   VPNC and OpenVPN work but PPTP does not.   Instructions for building these plugins are later on in this thread.
3) Some important new features are: GSM/CDMA aircard support, static IP address support, multiple interface support, profiles, etc...
4) If you get an error that the applet cannot start since some resources are not available enter the following command from a terminal:
```
sudo update-icon-caches 
```


If you would like to see a preview of NetworkManager 0.7 see:
[http://www.darrenalbers.net/blog/?p=9](http://www.darrenalbers.net/blog/?p=9)

VPN Plugins:  See Page 2 for VPNC and OpenVPN Plugin installation instructions, note that the PPTP plugin does not work in SVN yet.

Post any issues here and I will help with what I can.

Updated on July 3rd to use Alexander Sack's PPA, instructions for upgrading from my packages to Alexander's packages are available at:
[http://ubuntuforums.org/showpost.php?p=5305278&postcount=82](http://ubuntuforums.org/showpost.php?p=5305278&postcount=82)

---

### Post by nightfrost on 2008-05-18
Thanks a lot for this! It's really appreciated. I've been running NM-svn for a while now, but without proper packaging. I've been simply 'make install'ing it, and that's sort of been bugging me for a while.

I will try to use Biebl's packages to build 64-bit packages as well. Perhaps you'd be interested to host them as well, if I find the time to build them?

Thanks again!

---

### Post by Darrena on 2008-05-18
> **nightfrost said:**
> Thanks a lot for this! It's really appreciated. I've been running NM-svn for a while now, but without proper packaging. I've been simply 'make install'ing it, and that's sort of been bugging me for a while.

I will try to use Biebl's packages to build 64-bit packages as well. Perhaps you'd be interested to host them as well, if I find the time to build them?

Thanks again!

Sure, if you need me to host them I can.

Thanks!

---

### Post by atlas95 on 2008-05-19
Good howto but it doesn't work yet, dbus problem yet I think, it can acquire dhcp information.

---

### Post by nightfrost on 2008-05-19
> **atlas95 said:**
> Good howto but it doesn't work yet, dbus problem yet I think, it can acquire dhcp information.

If you want to make sure it's not a permission problem, edit /etc/dbus-1/system.d/nm-* and NetworkManager.conf in the same dir and replace every instance of deny with allow. Needless to say, this is a security risk. 

@Darrena: I'll try to attach a tar.bz2 of the amd64 debs here, do as you please with them.

Also, with regards to your howto, are you sure the -dev packages are needed? I know they're needed while building, but if one is not planning to build anything I wouldn't think they are necessary.

---

### Post by Darrena on 2008-05-19
> **atlas95 said:**
> Good howto but it doesn't work yet, dbus problem yet I think, it can acquire dhcp information.

Did you modify nm-dhcp-client.conf as shown in the How to?

---

### Post by Darrena on 2008-05-19
> **nightfrost said:**
> If you want to make sure it's not a permission problem, edit /etc/dbus-1/system.d/nm-* and NetworkManager.conf in the same dir and replace every instance of deny with allow. Needless to say, this is a security risk. 

@Darrena: I'll try to attach a tar.bz2 of the amd64 debs here, do as you please with them.

Also, with regards to your howto, are you sure the -dev packages are needed? I know they're needed while building, but if one is not planning to build anything I wouldn't think they are necessary.

You are correct, I left them in by accident. I originally wanted to include how to build the VPN plugins.

---

### Post by atlas95 on 2008-05-19
Yes I have correct it like in the howto, I will retry later.

---

### Post by atlas95 on 2008-05-21
Is this working correctly for you??

---

### Post by Darrena on 2008-05-21
> **atlas95 said:**
> Is this working correctly for you??

It is for me and a number of others.   What exactly is not working for you?

---

### Post by atlas95 on 2008-05-21
After the dhcp operation, the icon turn,turn and turn yet ... the operation never terminate... do you understand?

I have do the dbus modification.

---

### Post by atlas95 on 2008-05-21
If this can help you:
cyril@cyril-laptop:~$ sudo NetworkManager --no-daemon 
NetworkManager: <info>  starting...
/sbin/ifup: interface lo already configured
NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch
NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'.
NetworkManager: <info>  Found new Ethernet device 'eth0'.
NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_15_c5_85_89_54
NetworkManager: <info>  wlan0: Device is fully-supported using driver 'iwl4965'.
NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00).
NetworkManager: <info>  Found new wireless (802.11) device 'wlan0'.
NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1d_e0_45_dc_5d
NetworkManager: <info>  (eth0): device state change: 1 -> 2
NetworkManager: <info>  (eth0): bringing up device.
NetworkManager: <info>  (eth0): preparing device.
NetworkManager: <info>  (eth0): deactivating device.
NetworkManager: <info>  (wlan0): device state change: 1 -> 2
NetworkManager: <info>  (wlan0): bringing up device.
NetworkManager: <info>  (wlan0): preparing device.
NetworkManager: <info>  (wlan0): deactivating device.
Nothing to flush.
Nothing to flush.
NetworkManager: <info>  (wlan0): device state change: 2 -> 3
NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2.
NetworkManager: <info>  (eth0): carrier now ON (device state 2)
NetworkManager: <info>  (eth0): device state change: 2 -> 3
NetworkManager: <info>  Activation (eth0) starting connection 'Ethernet automatique'
NetworkManager: <info>  (eth0): device state change: 3 -> 4
NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (eth0): device state change: 4 -> 5
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  (eth0): device state change: 5 -> 7
NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction.
NetworkManager: <info>  dhclient started with pid 8771
NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:15:c5:85:89:54
Sending on   LPF/eth0/00:15:c5:85:89:54
Sending on   Socket/fallback
DHCPREQUEST of 192.168.10.11 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.10.11 from 192.168.10.254
bound to 192.168.10.11 -- renewal in 383287 seconds.

---

### Post by atlas95 on 2008-05-21
I Have modify somes other dbus conf files and it is good, but where can I get the openvpn plugin please? Openvpn plugin in hardy doesn't work with 0.7

Thx

---

### Post by Darrena on 2008-05-21
> **atlas95 said:**
> I Have modify somes other dbus conf files and it is good, but where can I get the openvpn plugin please? Openvpn plugin in hardy doesn't work with 0.7

Thx

You need to grab it from gnome SVN and build it.   I will be posting those instructions soon.

---

### Post by Spin84 on 2008-05-23
If you could also post instructions for getting the VPNC plugin working that would be great. Thx

Also the Add button on the Mobile Broadband tab doesn't work for me. Is this broken?

---

### Post by Darrena on 2008-05-24
> **Spin84 said:**
> If you could also post instructions for getting the VPNC plugin working that would be great. Thx

Also the Add button on the Mobile Broadband tab doesn't work for me. Is this broken?

No, I don't think it does anything since it should detect the card automatically.   What kind of card do you have?

I will post instructions for OpenVPN but they should be close to VPNC.

---

### Post by Darrena on 2008-05-24
Here is a rough rundown on installing the OpenVPN Plugin:
Download and install the development packages from:
[http://www.darrenalbers.com/networkmanager/0.7/dev/](http://www.darrenalbers.com/networkmanager/0.7/dev/)

Install build-essential and subversion
```
sudo apt-get install build-essential subversion
```
Install Build Dependencies 
```
sudo apt-get build-dep network-manager-openvpn
```


Checkout NM Trunk
```
svn co -r 3727 svn://svn.gnome.org/svn/NetworkManager/trunk NetworkManager
cd NetworkManager/vpn-daemons/openvpn/
./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
```

If you have problems connecting check the following:
Restart your PC or restart Network Manager (/etc/dbus-1/event.d/25NetworkManager restart)

Make sure that nm-openvpn-service.conf is in /etc/dbus-1/system.d

Validate that nm-openvpn-service.name is located in /etc/NetworkManager/VPN/

Change nm-open-vpn-service.conf to permit your user to own it as follows:
```
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
	<policy user="root">
		<allow own="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_interface="org.freedesktop.NetworkManager.openvpn"/>
	</policy>
	<policy user="yourusername">
		<allow own="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_interface="org.freedesktop.NetworkManager.openvpn"/>
	</policy>
	<policy context="default">
		<deny own="org.freedesktop.NetworkManager.openvpn"/>
		<deny send_destination="org.freedesktop.NetworkManager.openvpn"/>
		<deny send_interface="org.freedesktop.NetworkManager.openvpn"/>
	</policy>
</busconfig>
```

Change the default context above from deny to allow.

---

### Post by Darrena on 2008-05-24
Here is a rough rundown on installing the VPNC Plugin (I only validated that NM can see the plugin, I do not have a Cisco concentrator to test with):

Install the development packages from:
[http://www.darrenalbers.com/networkmanager/0.7/dev/](http://www.darrenalbers.com/networkmanager/0.7/dev/)

Install build-essential and subversion
```
sudo apt-get install build-essential subversion vpnc
```
Install Build Dependencies 
```
sudo apt-get build-dep network-manager-vpnc
```


Checkout revsion 3727 NM Trunk
```
svn co -r 3727 svn://svn.gnome.org/svn/NetworkManager/trunk NetworkManager
cd NetworkManager/vpn-daemons/vpnc/
./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
```

You should then see the VPNC option.   

If it fails to connect try the following:
1) Restart Network Manager

2) Modify /etc/dbus-1/system.d/nm-vpnc-service.conf and change the deny's below to permit or copy the allow user section and add your username

---

### Post by plun on 2008-06-03
Just FYI....:)

It was a new thread started within Intrepids dev forum and NM 0.7
looks nice after little problems with my wireless.

[http://ubuntuforums.org/showthread.php?t=814787](http://ubuntuforums.org/showthread.php?t=814787) 

UMTS connections would be really nice also.

wvdial just runs a bluetooth connected cellphone after a little
"fiddeling" with parameters.

Thanks for your work !

---

### Post by damoxc on 2008-06-04
If you can get a working source package then can just stick it on launchpad.

---

### Post by Darrena on 2008-06-07
> **damoxc said:**
> If you can get a working source package then can just stick it on launchpad.

Do you mean to publish it via a PPA?

---

### Post by Darrena on 2008-06-07
Packages updated to a SVN snapshot from June 5th.

---

### Post by mobiler on 2008-06-09
What about the PPTP plugin? It would be great to have it working...

I also noticed that when I select "Add" under "Wireless" in connection manager, it causes the window to close.

---

### Post by androme on 2008-06-09
Hello, i tried and it's okay for wired connection, but now i cannot connect to wireless connection, NM does not see any access point.

If i do a :

sudo iwlist scan, it returns all acces point surrounding me.

---

### Post by Darrena on 2008-06-09
> **mobiler said:**
> What about the PPTP plugin? It would be great to have it working...

I also noticed that when I select "Add" under "Wireless" in connection manager, it causes the window to close.

Unfortunately the PPTP plugin is not working at this time.

I will check on the window closing to see if I can recreate it.

---

### Post by Darrena on 2008-06-09
> **androme said:**
> Hello, i tried and it's okay for wired connection, but now i cannot connect to wireless connection, NM does not see any access point.

If i do a :

sudo iwlist scan, it returns all acces point surrounding me.

Can you post a snippet of your /var/log/syslog from around a minute or two after you click the icon?

---

### Post by Darrena on 2008-06-09
I can confirm the error with editing wireless networks from Connection Manager and will report a bug.

---

### Post by heruan on 2008-06-14
> **Darrena said:**
> I can confirm the error with editing wireless networks from Connection Manager and will report a bug.

Yeah, running nm-connection-editor from a terminal segfaults when adding new wireless network:
```

$ nm-connection-editor 

** (nm-connection-editor:7900): WARNING **: verify_tls: client certificate invalid

** (nm-connection-editor:7900): WARNING **: <WARN>  constructor(): Invalid connection read from GConf at /system/networking/connections/1.

Segmentation fault

```

---

### Post by Darrena on 2008-06-14
> **heruan said:**
> Yeah, running nm-connection-editor from a terminal segfaults when adding new wireless network:
```

$ nm-connection-editor 

** (nm-connection-editor:7900): WARNING **: verify_tls: client certificate invalid

** (nm-connection-editor:7900): WARNING **: <WARN>  constructor(): Invalid connection read from GConf at /system/networking/connections/1.

Segmentation fault

```

I should hopefully have fixed packages uploaded this afternoon or tonight.

---

### Post by heruan on 2008-06-14
> **Darrena said:**
> I should hopefully have fixed packages uploaded this afternoon or tonight.

Thanks!
How about create your PPA? :)

---

### Post by joske on 2008-06-14
Hi,

Until Darren has his own PPA, all necessary packages can be found in my PPA. If you have any of the VPN packages installed, you will need to uninstall them before upgrading to these versions. 

```
https://launchpad.net/~jos-dehaes/+archive
```

---

### Post by priegog on 2008-06-14
> **joske said:**
> Hi,

Until Darren has his own PPA, all necessary packages can be found in my PPA. If you have any of the VPN packages installed, you will need to uninstall them before upgrading to these versions. 

```
https://launchpad.net/~jos-dehaes/+archive
```

So just to be sure, If I add you repo, will I be able to get nm0.7 without having to compile or any weird stuff? Does it "Just Work®"?

---

### Post by plun on 2008-06-15
> **joske said:**
> Hi,

Until Darren has his own PPA, all necessary packages can be found in my PPA. If you have any of the VPN packages installed, you will need to uninstall them before upgrading to these versions. 

```
https://launchpad.net/~jos-dehaes/+archive
```

Hi joske  and Darrena

Just a proposal... I proposed the same to "asac".

Is it possible to coordinate all testing  ?
Ubuntu needs stronger testing procedures

Please see this thread
[http://ubuntuforums.org/showthread.php?t=676992&page=18](http://ubuntuforums.org/showthread.php?t=676992&page=18)

So maybe you, darrena and "asac" can coordinate this ?

:)

---

### Post by joske on 2008-06-15
> **priegog said:**
> So just to be sure, If I add you repo, will I be able to get nm0.7 without having to compile or any weird stuff? Does it "Just Work®"?

Yes. If you have any of the network-manager VPN plugins (pptp, openvpn, vpnc) installed, you will need to uninstall them beforehand, as they conflict with these packages. Hmm, and you will need to edit the config file as described in step 4 of the manual procedure, it appears to still be necessary.

---

### Post by Darrena on 2008-06-15
I just haven't had the time to look into setting up a PPA but I would like to.    If my Daughter gets to bed at a reasonable time (Never guaranteed with a 2 yr old!) I will take a look at what it takes to setup a PPA.

---

### Post by heruan on 2008-06-16
> **Darrena said:**
> I just haven't had the time to look into setting up a PPA but I would like to.    If my Daughter gets to bed at a reasonable time (Never guaranteed with a 2 yr old!) I will take a look at what it takes to setup a PPA.

Could you make source-package available? So we could try to build the package ourselves ;)

---

### Post by ForksHolder on 2008-06-16
Thanks, Nice howto.

Although after the restart no internet worked so i've tried in terminal:

> kill -9 -1 witch restarted X (and everything else), Then it worked great.

Thanks

---

### Post by Darrena on 2008-06-16
> **heruan said:**
> Could you make source-package available? So we could try to build the package ourselves ;)

It is, if you go to the link there is a source subfolder.

---

### Post by joske on 2008-06-16
> **Darrena said:**
> It is, if you go to the link there is a source subfolder.

but not all sources are available on your website (dbus-glib and wpasupplicant). In my ppa the sources of all necessary packages are there. You can just add the deb-src repository and you are good to go (with apt-get source).

---

### Post by heruan on 2008-06-16
> **joske said:**
> but not all sources are available on your website (dbus-glib and wpasupplicant). In my ppa the sources of all necessary packages are there. You can just add the deb-src repository and you are good to go (with apt-get source).

There's a tool to merge svn trunk and then rebuild the package?

---

### Post by joske on 2008-06-16
> **heruan said:**
> There's a tool to merge svn trunk and then rebuild the package?

I'm sorry, I don't understand your question.

When you add source repositories, you can then use the debian scripts to rebuild. Typically one does ```
apt-get source network-manager
```, followed by ```
sudo apt-get build-dep network-manager
``` and ```
fakeroot dpkg-buildpackage
``` this generates the .deb files.

---

### Post by heruan on 2008-06-16
> **joske said:**
> I'm sorry, I don't understand your question.

When you add source repositories, you can then use the debian scripts to rebuild. Typically one does ```
apt-get source network-manager
```, followed by ```
sudo apt-get build-dep network-manager
``` and ```
fakeroot dpkg-buildpackage
``` this generates the .deb files.

Ok, but suppose I want to build the latest svn version... How to update the source tree?

---

### Post by joske on 2008-06-16
> **heruan said:**
> Ok, but suppose I want to build the latest svn version... How to update the source tree?

this is harder, and out of scope for this guide, sorry. You would need to fetch the latest version from subversion, copy the debian directory in it, see if all patches still apply, if it all compiles cleanly, ...

---

### Post by Darrena on 2008-06-16
> **joske said:**
> but not all sources are available on your website (dbus-glib and wpasupplicant). In my ppa the sources of all necessary packages are there. You can just add the deb-src repository and you are good to go (with apt-get source).

Oh sorry, I grabbed wpa_supplicant and my Howto has it linked there so I didn't realize I had uploaded that as well.  dbus-glib I grabbed from Alexander Sack's PPA and is only needed if you rebuild the package.

Take a look at his PPA, he has a version of WPA_Supplicant for Hardy that will work and the proper version of dbus-glib.

So how do I sign up for a PPA?   I can't seem to find a sign-up.

---

### Post by Darrena on 2008-06-16
Ok I figured out how to setup the PPA, I will put together some source packages for a newer release and upload them and see how this goes!

---

### Post by Darrena on 2008-06-16
The PPA process is VERY slick...  I have a bunch of other packages I need to publish there now!

So the packages are building now, assuming no errors I will test them on my system and then publish the PPA information.

---

### Post by Darrena on 2008-06-16
The packages are now published at:

deb [http://ppa.launchpad.net/dalbers/ubuntu](http://ppa.launchpad.net/dalbers/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/dalbers/ubuntu](http://ppa.launchpad.net/dalbers/ubuntu) hardy main

A newer version is published there than what is on my website, so please test it out and let me know if it works ok and I will update the Howto to reflect using the PPA instead.

The PPA should have all the required dependencies including wpa_supplicant.

---

### Post by soro2005 on 2008-06-17
Installed and reconnected. Seems to work fine, although I haven't rebooted the computer or any of that.

It's great that you've taken the initiative here. I will leave your ppa live in my sources list, hoping you update conservatively and try to spare us some of the breakage that's likely to occur. :lolflag:

---

### Post by heruan on 2008-06-17
Great work Darren! It seems to work, except when creating a new Mobile Broadband connection... When clicking on the "Add" button:

** (nm-connection-editor:29773): WARNING **: create_new_connection_for_type: unhandled connection type 'NMSettingCdma'

** (nm-connection-editor:29773): WARNING **: Can't add new connection of type 'cdma'

Then (maybe it's just not yet implemented) when trying to publish a wireless connection on system settings, it says: Adding connection failed: Invalid connection.

Last thing, do you think packaging openvpn plugin should be possible at this time?

---

### Post by Darrena on 2008-06-17
> **heruan said:**
> Great work Darren! It seems to work, except when creating a new Mobile Broadband connection... When clicking on the "Add" button:

** (nm-connection-editor:29773): WARNING **: create_new_connection_for_type: unhandled connection type 'NMSettingCdma'

** (nm-connection-editor:29773): WARNING **: Can't add new connection of type 'cdma'

Then (maybe it's just not yet implemented) when trying to publish a wireless connection on system settings, it says: Adding connection failed: Invalid connection.

Last thing, do you think packaging openvpn plugin should be possible at this time?

I see that issue, it looks like it was fixed a day or two ago in SVN so I will need to pull another SVN snapshot.   In the meantime unless you have an unusual config it should detect you card and work without any changes.

Did you upgrade from 0.6.6?

As for the openvpn plugin, I can take a look.   I am just grabbing Michael Biebl's Debian packages, modifying the patches to work with Ubuntu and he doesn't have any of the VPN plugins packaged yet so I will have to do that myself.   I have done packaging before though so that shouldn't be hard, it will just take time.

---

### Post by Darrena on 2008-06-17
> **soro2005 said:**
> Installed and reconnected. Seems to work fine, although I haven't rebooted the computer or any of that.

It's great that you've taken the initiative here. I will leave your ppa live in my sources list, hoping you update conservatively and try to spare us some of the breakage that's likely to occur. :lolflag:


No Guarantees  ;-)

---

### Post by Darrena on 2008-06-17
Sorry one more item, publishing a connection as a system-wide setting does not work yet.   I will poke at it and see why not this week.

---

### Post by kpkeerthi on 2008-06-17
Thanks for this HOWTO. Really looking forward to 0.7 release.

---

### Post by altonbr on 2008-06-19
Just letting you know that 0.7.0~svn3747-2 broke my system. I rebooted and it was still broken. I set the network by hand and everything was fine.

I still have 0.7.0~svn3747-2 installed but it appears 0.6.6-0ubuntu5 is more stable (of course).

```
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Dell Unknown device 01a9
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at ecef0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

```

---

### Post by apedraza on 2008-06-20
Any news on the pptp plugin for nm 0.7? Thanks

---

### Post by Darrena on 2008-06-21
> **altonbr said:**
> Just letting you know that 0.7.0~svn3747-2 broke my system. I rebooted and it was still broken. I set the network by hand and everything was fine.

I still have 0.7.0~svn3747-2 installed but it appears 0.6.6-0ubuntu5 is more stable (of course).

```
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Dell Unknown device 01a9
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at ecef0000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

```

Can you give me more background?   What do you mean by broken?

---

### Post by Darrena on 2008-06-21
> **apedraza said:**
> Any news on the pptp plugin for nm 0.7? Thanks

According to the NM Dev's it has a good bit of work still remaining.   Looking at the changelog it hasn't been touched in awhile.   Right now NM has native PPP support for modems/Aircards so it looks like the biggest change will be moving it to the new PPP manager backend

---

### Post by ShirishAg75 on 2008-06-22
right, one of the things they want to settle into is the UI I'm guessing. Look at [http://blogs.gnome.org/dcbw/](http://blogs.gnome.org/dcbw/) ;)

---

### Post by lord_alan on 2008-06-22
> **Darrena said:**
> Can you give me more background?   What do you mean by broken?

I had what sounds like a similar problem just yesterday.

Fresh install of Hardy Heron. Do the updates. All works O.K. via eth0.

Once I installed the nm-0.7 and restarted the network was unavailable. ifconfig showed no eth0 (my LAN port) and I was unable to revert to 0.6. I tried forcing Synaptic to use version 0.6 but with no network it wouldn't play ball. For some reason it wouldn't use the CD to get the 0.6 version. No LAN, no dice.

I am just re-installing Hardy and going through the first update. If I can be sure I can revert (I'll probably make some copies of the 0.6 libs before upgrading) then I'll try again.

I see that OpenSuse 11 is shipping with nm-0.7 - have they done their own version or are they working on the same code?

Cheers

Alan

---

### Post by makaroni on 2008-06-22
Nm 0.7 works fine and Í use the huawei e220 hdspa modem. although I have one problem. In nm 0.66 I set up the connection manually in nm. So it seems that hardy still forces that manual connection.

Not quite sure how to remove this. But if I plug in the modem after I have logged in then it works like a charm. In the mobile broadband tab I still can't add networks. But if i autoconnect then I will see one network in the tab which I can edit.

Sometimes it shows the network times three in the connect menu but sometimes not...

---

### Post by sarah.fauzia on 2008-06-24
> **Darrena said:**
> ***_*This step should not be needed, please post on this thread if it is.   If you cannot obtain a DHCP address make the changes below_***

After installing the 0.7 version of Network Manager, I restarted my computer, and *yes*, I did need to use the modification you mentioned. After that my internet connected flawlessly ...Before that, it wouldn't even connect to my entirely unprotected home wireless network! Or the wired ethernet. I hope this information helps in the development of the official 0.7 version of network manager :)

---

### Post by edsena on 2008-06-25
> **Darrena said:**
> I see that issue, it looks like it was fixed a day or two ago in SVN so I will need to pull another SVN snapshot.   In the meantime unless you have an unusual config it should detect you card and work without any changes.

Did you upgrade from 0.6.6?



Hi Darren, how you're doing ? First of all, thanks for your great job on this thread; I've just upgraded NV from v0.6.6 to v0.7 using the repository you've provided just to let NM to take care of my HSDPA connection, but I'm facing the very same issue (Clicking on the "Add" button of the "Mobile Broadband" does nothing)... Well, do you know when will you have some "spare" time to create an publish a new SVN snapshot into your repo ?

Best regards,
Ed.

---

### Post by sarah.fauzia on 2008-06-25
I can happily report that the upgrade fixed my problem with connecting to my college's hidden network--before, with 0.6.6 Hardy, it'd see it, but not connect. Thank you so much! I'm truly overjoyed (after having been told by the IT people that they don't support Ubuntu/too busy, and struggling for a solid week on my own to figure this out. So again, thanks!

---

### Post by heruan on 2008-06-25
Darren,
 do you think it would be possible to make the package to install automatically an updated version of /etc/dbus-1/system.d/nm-dhcp-client.conf with the correct policies?

---

### Post by apedraza on 2008-06-25
Hi to all. Cannot connect to a WPA Enterprise access point with TLS and certificate authentication using nm 0.7. This is on a T43p Thinkpad running ubuntu 8.04. NM 0.66 works fine with AP. Hope this helps the developers. 

Thanks.

---

### Post by heruan on 2008-06-25
> **apedraza said:**
> Hi to all. Cannot connect to a WPA Enterprise access point with TLS and certificate authentication using nm 0.7. This is on a T43p Thinkpad running ubuntu 8.04. NM 0.66 works fine with AP. Hope this helps the developers.

After an unsuccessful attempt to connect to your network, do this:

$ grep 'NetworkManager' /var/log/syslog > nm.log

Then remove sensible informations from nm.log and copy contents to [http://pastebin.com](http://pastebin.com), then post here the link.

---

### Post by apedraza on 2008-06-25
Here is the link: [http://pastebin.com/m5266fcd](http://pastebin.com/m5266fcd)

Thanks.

---

### Post by mexlinux on 2008-06-26
> 
*This step should not be needed, please post on this thread if it is. If you cannot obtain a DHCP address make the changes below Modify /etc/dbus-1/system.d/nm-dhcp-client.conf to add a policy to allow the user dhcp to own the dbus interface as shown below.


Yes it's needed... It works great!

It solves this bug:
[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108344]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108344")

---

### Post by Darrena on 2008-06-28
I am building packages now on the PPA, they should be done in a couple of hours.   This one really should have the fixed nm-dhcp-client.conf file.   Please check and report back if it doesn't but I checked on my systems and it was correct.

Thanks!

---

### Post by Darrena on 2008-06-28
> **mexlinux said:**
> Yes it's needed... It works great!

It solves this bug:
[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108344]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/108344")

Thank you!  You opened the bug on Knetworkmanager, did you intend that?    I marked your bug as a duplicate since a request for static addresses and matching the IP Address to BSSID is already planned for 0.7 and was part of the list linked in the bug I marked it as a dup of.

---

### Post by heruan on 2008-06-28
> **Darrena said:**
> I am building packages now on the PPA, they should be done in a couple of hours.   This one really should have the fixed nm-dhcp-client.conf file.   Please check and report back if it doesn't but I checked on my systems and it was correct.

Great, nm-dhcp-client.conf now is automatically fixed! Some problems therefore persist, I can't publish system-wide connections (at least wireless) and I can't create mobile broadband connections. Maybe that release was not for these purposes, but I report that for reference.

---

### Post by zebulon M on 2008-06-29
Will Network Manager 0.7 compile and work on Gutsy? Are binaries availible somewhere? The bugs in 0.6.5 are annoying :(

---

### Post by Darrena on 2008-06-29
> **heruan said:**
> Great, nm-dhcp-client.conf now is automatically fixed! Some problems therefore persist, I can't publish system-wide connections (at least wireless) and I can't create mobile broadband connections. Maybe that release was not for these purposes, but I report that for reference.

I noticed the same thing but once it detected my card it allowed me to edit it.   So I think you need to get your card detected first.   What type of card do you have?

---

### Post by Darrena on 2008-06-29
> **zebulon M said:**
> Will Network Manager 0.7 compile and work on Gutsy? Are binaries availible somewhere? The bugs in 0.6.5 are annoying :(

You can try rebuilding my packages but I suspect that there are too many dependencies missing though...

---

### Post by heruan on 2008-06-29
> **Darrena said:**
> I noticed the same thing but once it detected my card it allowed me to edit it.   So I think you need to get your card detected first.   What type of card do you have?

What do you mean for card detection? I'm able to connect to my wireless network so I think my card is correctly detected. BTW, the model is:

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Thank you!

---

### Post by Darrena on 2008-06-29
> **heruan said:**
> What do you mean for card detection? I'm able to connect to my wireless network so I think my card is correctly detected. BTW, the model is:

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Thank you!

Sorry I was talking about Mobile Broadband, I haven't had much luck getting the published settings to work either.

---

### Post by edsena on 2008-06-30
> **Darrena said:**
> Sorry I was talking about Mobile Broadband, I haven't had much luck getting the published settings to work either.

Hi Darren, I've just downloaded and installed the new snapshot that you took from the SVN repo, and I still have that "Add Button" issue; But, your last post make me think a little bit about it;

When you say that the "Broadband card" should be already detected, it comes to my attention that I actually don't have one; Instead, I'm connecting through my cellphone, using the bluetooth capability of it... Isn't this feature intended for this kind of situation ?!

Well, actually, I'm not sure if here in this forum is the best place for this kind of discussion, but the problem is that is very tough to find information about NetworkManager over the internet... 

Are you aware of any forum or discussion list that this subject would fit better ?

Best Regards,
Ed.

---

### Post by HomerE on 2008-06-30
Hi, since I can't get static IP to wotk with NM 0.6, I followed your upgrade procedure to 0.7 and rebooted, but the old version is still there, accessed through the Network icon under Administration. How do I get rid of NM 0.6?

---

### Post by HomerE on 2008-06-30
I just noted the little network icon on the top-right sid of the panel. Ricght-clicking aloowed to configure the connection, and amazingly it worked!

Thanks!

---

### Post by apedraza on 2008-06-30
Hi everyone. When I click configure a vpn, nothing happens. Any news on PPTP VPN?

Thanks.

---

### Post by werries on 2008-07-02
i used this because i wanted the snapshot for the wireless key index. that didnt even work, and then it also broke wired connection, and adding one doesnt seem to do anything. so im not sure what to do here.

how would i go about reverting?

---

### Post by Darrena on 2008-07-02
Alexander Sack the official Network Manager Maintainer for Ubuntu is now publishing packages here:

[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

Add the following to your /etc/apt/sources.list and **REMOVE** the lines for my PPA:
deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

Do an apt-get update and then use the following command to switch to this version:
```
sudo apt-get install network-manager=0.7~~svn20080628t003601+eni2-0ubuntu0~pre1 libnm-glib0=0.7~~svn20080628t003601+eni2-0ubuntu0~pre1 libnm-util0=0.7~~svn20080628t003601+eni2-0ubuntu0~pre1 network-manager-gnome=0.7~~svn20080626t183232-0ubuntu0~pre1 
```

Once that is done you can do updates as normal to use this version

---

### Post by Darrena on 2008-07-02
> **werries said:**
> i used this because i wanted the snapshot for the wireless key index. that didnt even work, and then it also broke wired connection, and adding one doesnt seem to do anything. so im not sure what to do here.

how would i go about reverting?

If you can get online you can remove my PPA, do an apt-get update and do:
```
sudo apt-get install network-manager=0.6.6-0ubuntu5 libnm-glib0=0.6.6-0ubuntu5 libnm-util0=0.6.6-0ubuntu5 network-manager-gnome=0.6.6-0ubuntu5
```

---

### Post by mexlinux on 2008-07-02
> **Darrena said:**
> Alexander Sack the official Network Manager Maintainer for Ubuntu is now publishing packages here:

[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)


I have installed this new version, now I have a a problem, that I guess is related to permissions:
I can not edit the connections properties.

If I go to (mines is in spanish)
>Edit Conections>WiFi>(select one)>Edit>
The accept buttons is grayed out, no matter what modification I made, I can not save them

See screenshot.

---

### Post by heruan on 2008-07-02
> **mexlinux said:**
> I have installed this new version, now I have a a problem, that I guess is related to permissions:
I can not edit the connections properties.

If I go to (mines is in spanish)
>Edit Conections>WiFi>(select one)>Edit>
The accept buttons is grayed out, no matter what modification I made, I can not save them.

I can confirm this, OK button is grayed. I think this thread is no more the right place to discuss, unless Alexander Sack begins participate...

---

### Post by asac on 2008-07-02
> **mexlinux said:**
> I have installed this new version, now I have a a problem, that I guess is related to permissions:
I can not edit the connections properties.

If I go to (mines is in spanish)
>Edit Conections>WiFi>(select one)>Edit>
The accept buttons is grayed out, no matter what modification I made, I can not save them

See screenshot.

For me the button stays grey until you set the SSID to something valid. Did you do that?

---

### Post by heruan on 2008-07-02
> **asac said:**
> For me the button stays grey until you set the SSID to something valid. Did you do that?

Whatever I write as SSID, button stays greyed...

---

### Post by heruan on 2008-07-02
I found the matter: upgrading to new packages emptied certificate settings on Wireless Security tab. Now the button isn't more greyed, but clicking on it gives an error: ```
 ** (nm-connection-editor:19168): WARNING **: <WARN>  update(): update: Invalid connection: 'NMSetting8021x' / 'client-cert' invalid: 2 
```

---

### Post by asac on 2008-07-02
> **heruan said:**
> I found the matter: upgrading to new packages emptied certificate settings on Wireless Security tab. Now the button isn't more greyed, but clicking on it gives an error: ```
 ** (nm-connection-editor:19168): WARNING **: <WARN>  update(): update: Invalid connection: 'NMSetting8021x' / 'client-cert' invalid: 2 
```

This sounds a bit like a setting-migration issue which I dont want to rule out at this point. have you tried to create a new connection?

---

### Post by mexlinux on 2008-07-02
> **asac said:**
> This sounds a bit like a setting-migration issue which I dont want to rule out at this point. have you tried to create a new connection?

It works on new connections.
Ir's grayed out on previouse ones.

---

### Post by heruan on 2008-07-03
It's definitely a problem with certificates settings:
nm-connection-editor tries to set certificates using for example `client-cert' attribute, but gconf schema seems to expect `nma-path-client-cert'. May this be the issue?

---

### Post by asac on 2008-07-03
> **mexlinux said:**
> It works on new connections.
Ir's grayed out on previouse ones.

What type of connection is the one that broke? Anything special?

---

### Post by asac on 2008-07-03
> **heruan said:**
> It's definitely a problem with certificates settings:
nm-connection-editor tries to set certificates using for example `client-cert' attribute, but gconf schema seems to expect `nma-path-client-cert'. May this be the issue?

Double check that you are using the right network-manager-gnome package from the ~network-manager PPA. If you are sure thats the case then its a bug. Do other authentication issues work? e.g. WPA-PSK, etc.?

---

### Post by heruan on 2008-07-03
> **asac said:**
> Double check that you are using the right network-manager-gnome package from the ~network-manager PPA. If you are sure thats the case then its a bug. Do other authentication issues work? e.g. WPA-PSK, etc.?

My versions:
```

$ dpkg -l | grep network-manager
ii  network-manager                            0.7~~svn20080628t003601+eni2-0ubuntu0~pre1
ii  network-manager-gnome                      0.7~~svn20080626t183232-0ubuntu0~pre1

```

I try to elaborate a bit more on this problem: I removed all connections, then clicked on the wireless network on the applet; it asked me to select protection (I use TLS) and choose certificates. I did it and it connected successfully.
 On gconf I see:

```

$ gconftool-2 -R /system/networking
 /system/networking/connections:
  /system/networking/connections/1:
   /system/networking/connections/1/802-11-wireless:
    mode = infrastructure
    seen-bssids = [00:19:5b:3a:8d:8a,00:19:5b:3a:8d:87]
    ssid = [84,101,108,112,101,114,105,111,110]
    security = 802-11-wireless-security
    name = 802-11-wireless
   /system/networking/connections/1/802-11-wireless-security:
    pairwise = [tkip,ccmp,tkip,ccmp]
    group = [wep40,wep104,tkip,ccmp,wep40,wep104,tkip,ccmp]
    proto = [wpa,rsn,wpa,rsn]
    name = 802-11-wireless-security
    key-mgmt = wpa-eap
   /system/networking/connections/1/connection:
    id = Auto Telperion
    timestamp = 1215068924
    type = 802-11-wireless
    name = connection
    autoconnect = true
   /system/networking/connections/1/802-1x:
    nma-path-private-key = /home/giovanni/ssl/GiovanniLovato.pem
    eap = [tls]
    nma-path-ca-cert = /home/giovanni/ssl/AlduNetworkCA.crt
    name = 802-1x
    nma-path-client-cert = /home/giovanni/ssl/GiovanniLovato.pem
    identity = Giovanni Lovato

```

It seems correct to me, it connects after all :)
 Now if I run nm-connection-editor from a terminal and edit this connection, from Security tab I see no certificates set:

[IMG]http://img371.imageshack.us/img371/5049/screenshoteditingautotedn1.png[/IMG]

So, let's try to input the certificates. Once selected, immediately the button OK return active, but I get

[IMG]http://img20.imageshack.us/img20/5015/screenshotnmconnectioneay8.png[/IMG]

and the terminal says:

```

$ nm-connection-editor 

(nm-connection-editor:24259): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed
** Message: nm_connection_list_new: failed to load VPN plugins: Couldn't read VPN .name files directory /etc/NetworkManager/VPN.

** (nm-connection-editor:24259): WARNING **: <WARN>  update(): update: Invalid connection: 'NMSetting8021x' / 'client-cert' invalid: 2


```

---

### Post by asac on 2008-07-03
> **heruan said:**
> My versions:
```

$ dpkg -l | grep network-manager
ii  network-manager                            0.7~~svn20080628t003601+eni2-0ubuntu0~pre1
ii  network-manager-gnome                      0.7~~svn20080626t183232-0ubuntu0~pre1

```


Thanks for the detailed informatoin. I syched my bzr branches with latest upstream tree and pushed new packages to the [network-manager team ppa](https://edge.launchpad.net/~network-manager/+archive). They should be available in an hour latest.

The version of concern are:

network-manager 0.7~~svn20080703t022721+eni1-0ubuntu0~pre0
network-manager-gnome 0.7~~svn20080702t085614-0ubuntu0~pre1

If you still experience the same bug, please open a bug against network-manager in launchpad and post the bug id here. I will then triage it properly.

Thanks for testing!

---

### Post by heruan on 2008-07-03
Thanks for the updated packages, they resolved some other minor bugs... Unluckily this issue persists, so I fired bug #245184.

---

### Post by altonbr on 2008-07-03
@asac:
I got a pretty odd error:
> E: /var/cache/apt/archives/network-manager_0.7~~svn20080703t022721+eni1-0ubuntu0~pre0_i386.deb: trying to overwrite `/usr/lib/pppd/2.4.4/nm-pppd-plugin.so', which is also in package network-manager-pptp

Just letting you know. I'm working on a solution.

---

### Post by asac on 2008-07-03
> **altonbr said:**
> @asac:
I got a pretty odd error:


Just letting you know. I'm working on a solution.

remove network-manager-pptp before upgrading. I will explicitly conflict with the 0.6 package of the pptp package in order to prevent this upgrade error. Thanks!

---

### Post by heruan on 2008-07-03
Alexander, when the issue with nm-connection-manager will be resolved, do you think will be possible to have the package for OpenVPN plugin? :)

---

### Post by altonbr on 2008-07-03
> **asac said:**
> remove network-manager-pptp before upgrading. I will explicitly conflict with the 0.6 package of the pptp package in order to prevent this upgrade error. Thanks!

Excellent, seem to be working well over here (Hardy/Broadcom Corporation NetXtreme BCM5751)!

```
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Dell Unknown device 01a9
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at ecef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
		Address: 2248404008c72478  Data: 0e1b
	Capabilities: [d0] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <4us, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 4096 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0
		Link: Latency L0s <4us, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x1

```

---

### Post by altonbr on 2008-07-03
nm-applet 0.7 seems to fail when I right-click, select 'Edit Connections...' and try and edit 'Auto Ethernet' and 'Auto eth0' under the 'Wired' tab.

I tried editing three times, hence the repetition.

```
$ nm-applet

(nm-applet:31019): Gtk-CRITICAL **: gtk_notebook_set_tab_label: assertion `GTK_IS_WIDGET (child)' failed

** (nm-applet:31019): WARNING **: Error in sleep: Already awake
/usr/bin/nm-connection-editor: symbol lookup error: /usr/bin/nm-connection-editor: undefined symbol: nm_connection_duplicate
/usr/bin/nm-connection-editor: symbol lookup error: /usr/bin/nm-connection-editor: undefined symbol: nm_connection_duplicate
/usr/bin/nm-connection-editor: symbol lookup error: /usr/bin/nm-connection-editor: undefined symbol: nm_connection_duplicate
```

---

### Post by motin on 2008-07-06
> **asac said:**
> remove network-manager-pptp before upgrading. I will explicitly conflict with the 0.6 package of the pptp package in order to prevent this upgrade error. Thanks!

I got the same error and was also stuck in an evil loop where I tried to sudo apt-get remove network-manager-pptp but couldn't because of broken packages. I was recommended to do an sudo apt-get -f install but that in cause wanted to upgrade network-manager-gnome to 0.7 which would make apt spit out the original error...

The solution: Use aptitude to remove the package instead:
sudo aptitude remove network-manager-pptp

Aptitude will first prompt you if you want to upgrade network-manager-gnome, but also let you answer "No", and then suggest to instead downgrade the rest. Then aptitude will automatically remove network-manager-pptp. After that, you simply install network-manager-gnome again:
sudo aptitude install network-manager-gnome

Cheers

---

### Post by motin on 2008-07-10
Hmm... I really need network-manager-pptp but since there is a conflict, I cannot install it. Any ideas?

```
trying to overwrite `/usr/lib/pppd/2.4.4/nm-pppd-plugin.so', which is also in package network-manager
```

---

### Post by edsena on 2008-07-10
> **asac said:**
> Thanks for testing!

Hi Alexander, how you're doing ?

One the most exciting things for me about the 0.7 version of NM-Applet is the ability to configure/control HSDPA connection; But, the main issue is that I usually (when I say usually I mean more than once per day) use a bluetooth device (my cellphone) to connect to the internet, but NM doesn't support it;

A few days ago I borrowed from a friend a Huawey e226 for testing purposes, and despite the fact that NM detected it correctly and updated its context menu to show the ability to connect thru an "Mobile Broadband" device, the connection didn't succeeded (I'm sorry, I forgot to collect the logs, and I just kept the modem with me for less than 5 minutes, therefore I couldn't do any more "detailed testing").

But, the main question on this post, for me, is: Will NM-Applet support "Mobile Broadband" connections thru a Bluetooth device?

Best Regards,
Ed.

---

### Post by len1x on 2008-07-11
I installed it and everything is fine, I set up an adsl connection ( adsl tab ).. but each time I want to connect it asks for the password to be written, I don't see a "save password" feature, any idea?

---

### Post by hfdragon on 2008-07-11
I installed NM 0.7 and evrything seems to be working perfectly... everything but two things :

1 - VPN connection through openvpn (I don't know about other VPN standards). I think the packages are not released yet. Does anyone know if they will be ?

2 - Now I can see my UMTS Modem (USB) when it is plugged, but I can't connect... I'm ready to help debug this, how could I help ?

Thanks for your wonderful work !!

---

### Post by stringkarma on 2008-07-14
I have tried this a number of times and when I can even get my wired to work I still cannot get it to see my wireless card. I have tried the b43 kernel mod and the b43-fwcutter driver methods and I can even see the device wlan0 in the network tools. 0.7 just doesn't see my wireless card!
(ie when I right click it does not have an option to enable wireless under enable networking and no networks are detected or usable under manual addition)

Any thoughts?

---

### Post by apedraza on 2008-07-15
New update trashes nm-applet. Can't get dhcp address anymore from eth0.

This is on a HP 8710w. The previous update from july 3 was working great.

---

### Post by phaed on 2008-07-15
I had the same problem.  Can't get dhcp address.  

Couldn't downgrade it, of course, because I had no internet connection.  So I put in the Live CD hoping to use it as a repo, but network manager isn't listed there (even though it must be on the disk since it's loaded on the Live version of Ubuntu).

Luckily I had two optical drives.  So I booted my Live CD and downloaded the following packages from packages.ubuntu.com:

dhcdbd_3.0-1ubuntu1_i386.deb
libnl1_1.1-1_i386.deb
libnm-util0_0.6.6-0ubuntu5_i386.deb
network-manager_0.6.6-0ubuntu5_i386.deb
network-manager-gnome_0.6.6-0ubuntu3_i386.deb

Burned them to a CD, rebooted and installed them manually.  The first three are dependencies.  You have to uninstall network-manager, network-manager-gnome AND libnm-util0 as it's the 0.7 version, before you install the debs.

Then log out / log in.  That should get you back to a working Network Manager 0.6.6

---

### Post by zombiepig on 2008-07-15
I had the same problem with today's update, and like others, had to downgrade to hardy's version..

---

### Post by darnielng on 2008-07-16
Install Ubuntu Hardy on IBM T43p. After following the instructions on this thread to update the network manager to 0.7. After reboot the T43p just can't seem to access the network or obtain a DHCP address.

My setup:
The T43p is connected to a Linksys AG041 Router / DSL modem and with a Linksys WAP54G connected to the router.

I have managed to get an upgrade on Sunday (15/Jul/08) to 0.7 and also my network connect without any problem. Until I messed up my kernel and I had to do a fresh image restore from the "post" security and all relevant updates packages since 11 July 2008, backed up from "Partimage".

I have done the same process and somehow, I cannot get to connect to the internet and also my T43p failed to obtain a simple DHCP from my router.

It worked with static IP, it shows connected status. The problem here is, I get no internet access even it shows "connected status" from the 0.7 network manager.

Please help.

Thank's in advance!

---

### Post by asac on 2008-07-16
> **darnielng said:**
> Install Ubuntu Hardy on IBM T43p. After following the instructions on this thread to update the network manager to 0.7. After reboot the T43p just can't seem to access the network or obtain a DHCP address.

My setup:
The T43p is connected to a Linksys AG041 Router / DSL modem and with a Linksys WAP54G connected to the router.

I have managed to get an upgrade on Sunday (15/Jul/08) to 0.7 and also my network connect without any problem. Until I messed up my kernel and I had to do a fresh image restore from the "post" security and all relevant updates packages since 11 July 2008, backed up from "Partimage".

I have done the same process and somehow, I cannot get to connect to the internet and also my T43p failed to obtain a simple DHCP from my router.

It worked with static IP, it shows connected status. The problem here is, I get no internet access even it shows "connected status" from the 0.7 network manager.

Please help.

Thank's in advance!


There was bustage this morning in the network-manager PPA. The latest packages should fix most.

We also added new wpasupplicant packages, please upgrade and test them as well.

Thanks!

---

### Post by heruan on 2008-07-16
When I try to set up an EAP-TLS connection in nm-connection-editor, it doesn't accept certificates:
```

WARNING **: <WARN>  update(): update: Invalid connection: 'NMSetting8021x' / 'client-cert' invalid: 2

```

---

### Post by AikenDrum on 2008-07-16
Hi Alexander,  

thanks for all your work on this - the new version is making life much easier on my Hardy laptop while I bounce it around all the different networks I work with.

I've tried to compile the vpnc and openvpn modules per the instructions on pg 2 of this forum,  and I'm hitting an issue with missing source file at the 'make' step of both vpnc and openvpn - ala:

nm-vpnc.c:36:33: error: nm-vpn-ui-interface.h: No such file or directory

Am I going about this completely the wrong way ?  or is this nm-vpn-ui-interface.h file missing from the current svn ?

Cheers !

Scott

---

### Post by hfdragon on 2008-07-17
Here is an exctract of my syslog :

```
Jul 17 11:15:58 christophe-laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Orange 3G+' 
Jul 17 11:15:58 christophe-laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Jul 17 11:15:58 christophe-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 17 11:15:58 christophe-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Jul 17 11:15:58 christophe-laptop NetworkManager: <debug> [1216286158.487334] nm_serial_device_open(): (ttyUSB0) opening device... 
Jul 17 11:15:58 christophe-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Jul 17 11:16:13 christophe-laptop NetworkManager: [COLOR="Red"]<WARN>  manual_registration_done(): Manual registration failed[/COLOR] 
Jul 17 11:16:13 christophe-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 
Jul 17 11:16:13 christophe-laptop NetworkManager: <debug> [1216286173.781108] nm_serial_device_close(): Closing device 'ttyUSB0' 
Jul 17 11:16:13 christophe-laptop NetworkManager: <info>  Marking connection 'Orange 3G+' invalid. 
Jul 17 11:16:13 christophe-laptop NetworkManager: <info>  Activation (ttyUSB0) failed. 
Jul 17 11:16:13 christophe-laptop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Jul 17 11:16:13 christophe-laptop NetworkManager: <info>  (ttyUSB0): deactivating device. 
Jul 17 11:16:13 christophe-laptop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jul 17 11:16:13 christophe-laptop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed

```

Where can the "manual registration" problem come from ?
Did I misconfigured it ?

---

### Post by hfdragon on 2008-07-17
> **AikenDrum said:**
> 
nm-vpnc.c:36:33: error: nm-vpn-ui-interface.h: No such file or directory


I get the same error...

---

### Post by Darrena on 2008-07-19
> **hfdragon said:**
> I get the same error...

You probably need to checkout a SVN revision that matches what Alexander used to build NM.

Browsing through the SVN repo I would try revisions 3799 to 3805 that matches the date.   3803 had some specific changes to VPNC

---

### Post by asac on 2008-07-20
> **Darrena said:**
> You probably need to checkout a SVN revision that matches what Alexander used to build NM.

Browsing through the SVN repo I would try revisions 3799 to 3805 that matches the date.   3803 had some specific changes to VPNC

The source tree of the NM package has the vpn-daemons in it. we currently just dont build them. So just use apt-get source network-manager and then go to the vpn-daemons/ directories or even better use the bzr branches.

Doing so will give you the matching versions.

---

### Post by asac on 2008-07-20
> **asac said:**
> The source tree of the NM package has the vpn-daemons in it. we currently just dont build them. So just use apt-get source network-manager and then go to the vpn-daemons/ directories or even better use the bzr branches.

Doing so will give you the matching versions.

To get bzr branch do:
```
bzr branch https://code.edge.launchpad.net/~ubuntu-core-dev/network-manager/ubuntu.0.7
```

---

### Post by Darrena on 2008-07-20
Alexander,

When I try using the version checked out from bzr I get the following:
"nm-openvpn.c:36:33: error: nm-vpn-ui-interface.h: No such file or directory"

If it matters revision 3804 seems to build but it doesn't allow me to modify the settings since that snapshot was part of the transition to the newer GUI.   

Is it possible to go to a newer SVN snapshot?

Thanks!

---

### Post by asac on 2008-07-21
> **Darrena said:**
> Alexander,

When I try using the version checked out from bzr I get the following:
"nm-openvpn.c:36:33: error: nm-vpn-ui-interface.h: No such file or directory"

If it matters revision 3804 seems to build but it doesn't allow me to modify the settings since that snapshot was part of the transition to the newer GUI.   

Is it possible to go to a newer SVN snapshot?

Thanks!

Yes, today Dan fixed PPTP in svn so its probably is a good time to start doing this. However, the settings API changed a bit, and I see crashes with gconf database created in our previous  builds. i have to fix that first. Hopefully I will get a new build up soon.

If you want to help merging the latest trunk development more frequently feel free to ping me in irc ;).

Thank you!

---

### Post by stringkarma on 2008-07-24
I don't know if anyone cares but I have my 0.7 wireless working now.

I had to remove and the reload my b43 module with ```
sudo modprobe -r b43
sudo modprobe b43
```

It works now. Looks good. Can't wait to try it out with my university's horrible EAP-TTLS PAP Dynamic-WEP certificate based networking mess.

I'll let you all know.

---

### Post by fly3rman on 2008-07-25
> **Darrena said:**
> Alexander,

When I try using the version checked out from bzr I get the following:
"nm-openvpn.c:36:33: error: nm-vpn-ui-interface.h: No such file or directory"

If it matters revision 3804 seems to build but it doesn't allow me to modify the settings since that snapshot was part of the transition to the newer GUI.   

Is it possible to go to a newer SVN snapshot?

Thanks!
Same Problem!!

---

### Post by stringkarma on 2008-07-25
UPDATE: An I would love some feedback from you guys on this. Before I wrote:

> **stringkarma said:**
> I don't know if anyone cares but I have my 0.7 wireless working now.

I had to remove and the reload my b43 module with ```
sudo modprobe -r b43
sudo modprobe b43
```

It works now. Looks good. Can't wait to try it out with my university's horrible EAP-TTLS PAP Dynamic-WEP certificate based networking mess.

I'll let you all know.

But the truth is I actually have to do the remove and modprobe every time I reboot.
Is there something that I can do to make my system work on startup, besides putting these lines in rc.local?
(I should add that currently b43 is in my /etc/modules so that it loads on startup - could this be a problem somehow?)


Thanks for any help you can offer

PS the university network finally works for me thanks!

---

### Post by stringkarma on 2008-07-25
It seems that it is a boot order thing. As a work-around I have found that commenting out b43 in /etc/modules and then adding modprobe b43 in rc.local causes the network to come right up after boot.

That said is there a more elegant way to do this?

(Linux fans were ooh-ing and aah-ing at my wireless on campus)

---

### Post by asac on 2008-07-26
> **Darrena said:**
> Alexander,

When I try using the version checked out from bzr I get the following:
"nm-openvpn.c:36:33: error: nm-vpn-ui-interface.h: No such file or directory"

If it matters revision 3804 seems to build but it doesn't allow me to modify the settings since that snapshot was part of the transition to the newer GUI.   

Is it possible to go to a newer SVN snapshot?

Thanks!

OK, uploaded a new snapshot to [https://edge.launchpad.net/~network-manager/+archive](https://edge.launchpad.net/~network-manager/+archive). Its taken on Jul 20 and should contain most pptp fixes. Its on the same branches. Let me know which vpn daemons works and which are still broken please.

---

### Post by apedraza on 2008-07-26
I get a strange error when updating:

E: network-manager: subprocess post-installation script returned error exit status 1
E: network-manager-gnome: dependency problems - leaving unconfigured

I actually got this error on the last snapshot as well. I also get two wired ethernet ports instead of one. The first is named Auto Ehternet and the other is Auto eth0. I have tried to delete Auto eth0 but it comes back at reboot.

My pptp vpn is not working with this update either. There is no option to connect. 

Everything else works fine.

Thank you to all for your hard work.

---

### Post by asac on 2008-07-26
> **apedraza said:**
> I get a strange error when updating:

E: network-manager: subprocess post-installation script returned error exit status 1
E: network-manager-gnome: dependency problems - leaving unconfigured

I actually got this error on the last snapshot as well. I also get two wired ethernet ports instead of one. The first is named Auto Ehternet and the other is Auto eth0. I have tried to delete Auto eth0 but it comes back at reboot.

My pptp vpn is not working with this update either. There is no option to connect. 

Everything else works fine.

Thank you to all for your hard work.

please post the complete output you get when the upgrade fails.

---

### Post by apedraza on 2008-07-26
> **asac said:**
> please post the complete output you get when the upgrade fails.

This is what I get:

The following packages will be REINSTALLED:
  network-manager network-manager-gnome 
0 packages upgraded, 0 newly installed, 2 reinstalled, 1 to remove and 0 not upgraded.
Need to get 0B/904kB of archives. After unpacking 385kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 193528 files and directories currently installed.)
Removing libdbus-glib-1-dev ...
(Reading database ... 193514 files and directories currently installed.)
Preparing to replace network-manager 0.7~~svn20080720t224551+eni1-0ubuntu1~hardy1~nm2 (using .../network-manager_0.7~~svn20080720t224551+eni1-0ubuntu1~hardy1~nm2_i386.deb) ...
Unpacking replacement network-manager ...
Preparing to replace network-manager-gnome 0.7~~svn20080721t051503-0ubuntu1~hardy~nm1 (using .../network-manager-gnome_0.7~~svn20080721t051503-0ubuntu1~hardy~nm1_i386.deb) ...
Unpacking replacement network-manager-gnome ...
Setting up network-manager (0.7~~svn20080720t224551+eni1-0ubuntu1~hardy1~nm2) ...
 System startup links for /etc/init.d/NetworkManager already exist.
Restarting Network connection manager daemon: NetworkManagerinvoke-rc.d: initscript NetworkManager, action "restart" failed.
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.7~~svn20080720t224551); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up network-manager (0.7~~svn20080720t224551+eni1-0ubuntu1~hardy1~nm2) ...
 System startup links for /etc/init.d/NetworkManager already exist.
Restarting Network connection manager daemon: NetworkManager.
 * Reloading system message bus config...                                [ OK ] 

Setting up network-manager-gnome (0.7~~svn20080721t051503-0ubuntu1~hardy~nm1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by Darrena on 2008-07-27
> **asac said:**
> OK, uploaded a new snapshot to [https://edge.launchpad.net/~network-manager/+archive](https://edge.launchpad.net/~network-manager/+archive). Its taken on Jul 20 and should contain most pptp fixes. Its on the same branches. Let me know which vpn daemons works and which are still broken please.

Alexander, thank you for merging this.   I do plan on catching you on IRC soon, I want to read up on how to use BZR first since I have never used it beyond checking things out.

Specific to this update I installed it and built the openvpn plugin from bzr and I get the following error when I try and connect:
Jul 27 18:42:48 dpalap NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.254 (nma_vpn_request_password): couldn't run VPN auth dialog.. 

And this message comes up from nm-applet:
There was a problem launching the authentication dialog for VPN connection type 'org.freedesktop.NetworkManager.pptp'. Contact your system administrator.

This happens with both the PPTP and OpenVPN plugin.

---

### Post by hfdragon on 2008-07-29
I have build the openvpn plugin doing this :
```

bzr branch lp:network-manager
cd network-manager/vpn-daemons/openvpn
./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install

```

Everything seems to be working fine, I have no error message.

I do have the "VPN connections" menu in my nm applet

But I can't Add/Edit/Import any VPN connection (all buttons are greyed out) :confused::confused:

What did I do wrong ?
There is no error message in the syslog and I have the latest nm version in the ppa..
And I almost forgot, I also did modify /etc/dbus-1/system.d/nm-openvpn-service.conf as specified earlier in this thread.

---

### Post by mikkelrobin on 2008-07-31
I have the excat same problem

If im runnig /vat/libexec/nm-openvpn-service im getting this:

```

** (process:16566): WARNING **: <WARN>  constructor(): Connection ":1.2553" is not allowed to own the service "org.freedesktop.NetworkManager.openvpn" due to security policies in the configuration file

```

UPDATE:
If im running "sudo NetworkManager --no-daemon" i can't see anything about the VPN plugin:

```

NetworkManager: <info>  starting...
/sbin/ifup: interface lo already configured
NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ipw_wlan_switch
NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'.
NetworkManager: <info>  Found new Ethernet device 'eth0'.
NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_16_d3_22_71_b0
NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2200'.
NetworkManager: <info>  eth1: driver supports SSID scans (scan_capa 0x21).
NetworkManager: <info>  Found new wireless (802.11) device 'eth1'.
NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_13_ce_e5_dd_c5
NetworkManager: <info>  (eth0): device state change: 1 -> 2
NetworkManager: <info>  (eth0): bringing up device.
NetworkManager: <info>  (eth0): preparing device.
NetworkManager: <info>  (eth0): deactivating device.
NetworkManager: <info>  (eth1): device state change: 1 -> 2
NetworkManager: <info>  (eth1): bringing up device.
NetworkManager: <info>  (eth1): preparing device.
NetworkManager: <info>  (eth1): deactivating device.
NetworkManager: <info>  (eth1): device state change: 2 -> 3
NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2.
NetworkManager: <info>  Activation (eth1) starting connection 'Auto Gbg17-2TH'
NetworkManager: <info>  (eth1): device state change: 3 -> 4
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (eth1): device state change: 4 -> 5

```

---

### Post by asac on 2008-08-07
[QUOTE=mikkelrobin;5494586]I have the excat same problem

If im runnig /vat/libexec/nm-openvpn-service im getting this:

```

** (process:16566): WARNING **: <WARN>  constructor(): Connection ":1.2553" is not allowed to own the service "org.freedesktop.NetworkManager.openvpn" due to security policies in the configuration file

```

this means that a dbus policy file is missing. where is the nm-*service.conf file you find in vpn sources installed?

if its not in the default location you can enable the directory you use for that install by adding <includedir>/path/to/dbus/events.d/</includedir> in /etc/dbus-1/system.conf

remember to reload your dbus configuration after that. (to be safe, restart).

---

### Post by mikkelrobin on 2008-08-07
Hmmm my nm-openvpn-serive.conf is here:
/etc/dbus-1/system.d/nm-openvpn-service.conf

And the include in system.conf is set to system.d, so everything looks right....

---

### Post by Remanifest on 2008-08-08
Thank you SO much!  I was having one hell of a time getting my wireless configuration to work the way I wanted it to (without a bunch of ridiculous hiccups).  wicd just wasn't cutting it for me (too limited), and Network Manager 0.6 was a downright joke that was extremely frustrating to operate.  0.7 works as it should, and is quite simple to understand and configure the way I wanted things done.

THANK YOU.  Now I can finally use my wireless router -- wirelessly!

---

### Post by Darrena on 2008-08-08
> **mikkelrobin said:**
> Hmmm my nm-openvpn-serive.conf is here:
/etc/dbus-1/system.d/nm-openvpn-service.conf

And the include in system.conf is set to system.d, so everything looks right....

Check that file and see if changing the default from deny to allow helps.

---

### Post by Darrena on 2008-08-08
Here is the error I get with the VPN Plugins:
> There was a problem launching the authentication dialog for VPN connection type 'org.freedesktop.NetworkManager.openvpn'. Contact your system administrator.

When I run NetworkManager --no-daemon I see this message:

> NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.254 (nma_vpn_request_password): couldn't run VPN auth dialog..



If I compare the source from Gnome SVN to what is in Bazaar only the version in Bazaar has this file and it does not seem to exist in SVN.

Installing the OpenVPN plugin from SVN does not seem to help.   I will try and do more digging tonight.

---

### Post by mikkelrobin on 2008-08-09
I already done that, nothing helps :-(

---

### Post by asac on 2008-08-10
> **Darrena said:**
> Here is the error I get with the VPN Plugins:


When I run NetworkManager --no-daemon I see this message:



If I compare the source from Gnome SVN to what is in Bazaar only the version in Bazaar has this file and it does not seem to exist in SVN.

Installing the OpenVPN plugin from SVN does not seem to help.   I will try and do more digging tonight.

I updated everything in network-manager PPA (for intrepid) and also packaged a openvpn snapshot based on the same source line. please test.

---

### Post by IntuitiveNipple on 2008-08-11
The PPA build of network-manager-applet (and network-manager-openvpn) failed. I fixed the bug (uninitialised pointer)  and built network-manager-applet for Hardy successfully.

I've attached the debdiff containing the patch.

---

### Post by IntuitiveNipple on 2008-08-11
The build of network-manager-openvpn fails because of a missing build-depends on libnm-glib-dev (>= 0.7~~).

debdiff with fix attached.

---

### Post by asac on 2008-08-11
> **IntuitiveNipple said:**
> The build of network-manager-openvpn fails because of a missing build-depends on libnm-util-dev (>= 0.7~~).

debdiff with fix attached.

OK, reuploaded ~nm2 (btw, libnm-glib-dev was what was missing)

---

### Post by IntuitiveNipple on 2008-08-11
> **asac said:**
> (btw, libnm-glib-dev was what was missing)
Yes... silly cut-n-paste error by me for the forum post :)

---

### Post by asac on 2008-08-12
fwiw, vpnc and pptp packages built in network-manager PPA as well now. everything should be available for hardy and intrepid in that PPA. Please test.

---

### Post by thund3rman on 2008-08-12
Hy ASAC,

First of all let me thank you for all your hardwork! 
I just upgraded from your ppa and intalled pptp and openvpn plugins and they work great until I try to connect. When I connect to one of the defined networks I get the following message in the logs: 
"Aug 12 15:38:10 luis-lpt NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.254 (nma_vpn_request_password): couldn't run VPN auth dialog.."
What can I do to work around this problem?

---

### Post by motin on 2008-08-12
> **asac said:**
> fwiw, vpnc and pptp packages built in network-manager PPA as well now. everything should be available for hardy and intrepid in that PPA. Please test.

Thanks! Now network-manager-pptp installs fine!

---

### Post by hfdragon on 2008-08-12
openvpn plugin installs fine.

No more problem to configure an openvpn VPN.

But I also have this message when trying to connect to a vpn :
```
Aug 12 23:41:10 christophe-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.254 (nma_vpn_request_password): couldn't run VPN auth dialog..
```

---

### Post by heruan on 2008-08-13
> **asac said:**
> I updated everything in network-manager PPA (for intrepid) and also packaged a openvpn snapshot based on the same source line. please test.

Thank you very much Alexander! I'm trying the openvpn plugin and I can't find a textfield to put the passphrase to decrypt the private key file... So when I try to connect the applet tells me it can't find a usable secret to decrypt the key!

```

NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.254 (nma_vpn_request_password): couldn't run VPN auth dialog..

```

---

### Post by apedraza on 2008-08-13
Same error as above but with pptp plugin. "There was a problem launching the authentication dialog for VPN connection type"

Thank you for your help.

---

### Post by nightfrost on 2008-08-14
Firstly, I want to thank you for building NM-0.7 packages. I used to rebuild Michael Biebl's packages until quite recently. Now, I'm using the networkmanager ppa, and have as of the most recent packages (I'm on hardy by the way) not been managed to get a connection with my GSM USB modem. The Huawei e220 I'm using has been working perfectly fine up until now.
This is the output of NetworkManager --no-daemon:
```
NetworkManager: <info>  starting...
/sbin/ifup: interface lo already configured
NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ipw_wlan_switch
NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'.
NetworkManager: <info>  Found new Ethernet device 'eth0'.
NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_0b_5d_7f_17_89
NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2200'.
NetworkManager: <info>  eth1: driver supports SSID scans (scan_capa 0x21).
NetworkManager: <info>  Found new wireless (802.11) device 'eth1'.
NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_12_f0_0f_5b_15
NetworkManager: <info>  ttyUSB0: Device is fully-supported using driver 'option'.
NetworkManager: <debug> [1218741398.298822] setup_monitor_device(): No monitoring udi provided
NetworkManager: <info>  Found new Modem device 'ttyUSB0'.
NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/Hal/devices/usb_device_12d1_1003_noserial_if0_serial_usb_0
NetworkManager: <WARN>  connection_get_settings_cb(): connection_get_settings_cb: Invalid connection: 'NMSettingIP4Config' / 'method' invalid: 1
NetworkManager: <info>  Wireless now disabled by radio killswitch
NetworkManager: <info>  (eth0): device state change: 1 -> 2
NetworkManager: <info>  (eth0): bringing up device.
NetworkManager: <info>  (eth0): preparing device.
NetworkManager: <info>  (eth0): deactivating device.
NetworkManager: <info>  (eth1): device state change: 1 -> 2
NetworkManager: <info>  (eth1): bringing up device.
NetworkManager: <info>  (eth1): preparing device.
NetworkManager: <info>  (eth1): deactivating device.
NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2
NetworkManager: <info>  (ttyUSB0): deactivating device.
NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3
NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Automatisk anslutning till GSM-nätverk'
NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <debug> [1218741414.552945] nm_serial_device_open(): (ttyUSB0) opening device...
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Registered on Home network
NetworkManager: <info>  Associated with network: +COPS: 0,0,"3",2
NetworkManager: <info>  Connected, Woo!
NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5
NetworkManager: <info>  Starting pppd connection
NetworkManager: <debug> [1218741414.943730] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock ttyUSB0 noipdefault usepeerdns ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
NetworkManager: <debug> [1218741415.032899] nm_ppp_manager_start(): ppp started with pid 8906
NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 6
NetworkManager: nm_ppp_manager_update_secrets: assertion `device != NULL' failed

```

Is anyone else seeing this?

---

### Post by asac on 2008-08-14
> **thund3rman said:**
> Hy ASAC,

First of all let me thank you for all your hardwork! 
I just upgraded from your ppa and intalled pptp and openvpn plugins and they work great until I try to connect. When I connect to one of the defined networks I get the following message in the logs: 
"Aug 12 15:38:10 luis-lpt NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.254 (nma_vpn_request_password): couldn't run VPN auth dialog.."
What can I do to work around this problem?

I bumped to a new upstream release (12th Aug) and uploaded that together with a probable fix for the vpn password dialog issue to the network-manager PPA.

I hope the builds will finish without failure in the next few hours.

Remember that you need to upgrade everything (daemon, libs, applet and vpn plugins) and then reboot to get the latest.

---

### Post by hfdragon on 2008-08-15
Now I get these error message (3 tries I think):

```
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'... 
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 8210 
Aug 15 09:04:32 christophe-laptop kernel: [  224.478724] tun: Universal TUN/TAP device driver, 1.6
Aug 15 09:04:32 christophe-laptop kernel: [  224.478728] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Aug 15 09:04:32 christophe-laptop NetworkManager: nm_vpn_connection_activate: assertion `nm_vpn_connection_get_vpn_state (connection) == NM_VPN_CONNECTION_STATE_PREPARE' failed
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  VPN plugin state changed: 1 
Aug 15 09:04:32 christophe-laptop kernel: [  224.608303] printk: 1 messages suppressed.
Aug 15 09:04:32 christophe-laptop kernel: [  224.608309] nm-openvpn-auth[8217]: segfault at 00000001 eip b7710791 esp bfdbcc60 error 4
Aug 15 09:04:32 christophe-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.301 (nma_vpn_request_password): canceled.
Aug 15 09:05:44 christophe-laptop kernel: [  296.574506] nm-openvpn-auth[8366]: segfault at 00000001 eip b77bf791 esp bf9d1230 error 4
Aug 15 09:05:44 christophe-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.301 (nma_vpn_request_password): canceled. 
Aug 15 09:06:16 christophe-laptop kernel: [  328.476989] nm-openvpn-auth[8410]: segfault at 00000001 eip b7711791 esp bfa5d2c0 error 4
Aug 15 09:06:16 christophe-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.301 (nma_vpn_request_password): canceled. 
```

---

### Post by asac on 2008-08-15
> **hfdragon said:**
> Now I get these error message (3 tries I think):

```
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'... 
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 8210 
Aug 15 09:04:32 christophe-laptop kernel: [  224.478724] tun: Universal TUN/TAP device driver, 1.6
Aug 15 09:04:32 christophe-laptop kernel: [  224.478728] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Aug 15 09:04:32 christophe-laptop NetworkManager: nm_vpn_connection_activate: assertion `nm_vpn_connection_get_vpn_state (connection) == NM_VPN_CONNECTION_STATE_PREPARE' failed
Aug 15 09:04:32 christophe-laptop NetworkManager: <info>  VPN plugin state changed: 1 
Aug 15 09:04:32 christophe-laptop kernel: [  224.608303] printk: 1 messages suppressed.
Aug 15 09:04:32 christophe-laptop kernel: [  224.608309] nm-openvpn-auth[8217]: segfault at 00000001 eip b7710791 esp bfdbcc60 error 4
Aug 15 09:04:32 christophe-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.301 (nma_vpn_request_password): canceled.
Aug 15 09:05:44 christophe-laptop kernel: [  296.574506] nm-openvpnauth[8366]: segfault at 00000001 eip b77bf791 esp bf9d1230 error 4
Aug 15 09:05:44 christophe-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.301 (nma_vpn_request_password): canceled. 
Aug 15 09:06:16 christophe-laptop kernel: [  328.476989] nm-openvpn-auth[8410]: segfault at 00000001 eip b7711791 esp bfa5d2c0 error 4
Aug 15 09:06:16 christophe-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.301 (nma_vpn_request_password): canceled. 
```


You sure you upgraded everything?

Please paste the output of the following commands:
```

 COLUMNS=200 dpkg -l network-manager
 COLUMNS=200 dpkg -l network-manager-gnome
 COLUMNS=200 dpkg -l libnm-util0
 COLUMNS=200 dpkg -l libnm-glib0
 COLUMNS=200 dpkg -l network-manager-openvpn

```

---

### Post by hfdragon on 2008-08-15
I think I upgraded everything... 

```
christophe@christophe-laptop:~$ COLUMNS=200 dpkg -l network-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nom                                          Version                                      Description
+++-============================================-============================================-========================================================================================================
ii  network-manager                              0.7~~svn20080812t224027+eni0-0ubuntu1~nm2~ha network management framework daemon
christophe@christophe-laptop:~$ 
christophe@christophe-laptop:~$ COLUMNS=200 dpkg -l network-manager-gnome
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nom                                          Version                                      Description
+++-============================================-============================================-========================================================================================================
ii  network-manager-gnome                        0.7~~svn20080812t174537-0ubuntu1~nm1~hardy1  network management framework (GNOME frontend)
christophe@christophe-laptop:~$ COLUMNS=200 dpkg -l libnm-util0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nom                                          Version                                      Description
+++-============================================-============================================-========================================================================================================
ii  libnm-util0                                  0.7~~svn20080812t224027+eni0-0ubuntu1~nm2~ha network management framework (shared library)
christophe@christophe-laptop:~$ COLUMNS=200 dpkg -l libnm-glib0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nom                                          Version                                      Description
+++-============================================-============================================-========================================================================================================
ii  libnm-glib0                                  0.7~~svn20080812t224027+eni0-0ubuntu1~nm2~ha network management framework (GLib shared library)
christophe@christophe-laptop:~$ COLUMNS=200 dpkg -l network-manager-openvpn
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nom                                          Version                                      Description
+++-============================================-============================================-========================================================================================================
ii  network-manager-openvpn                      0.7~~svn20080812t224027-0ubuntu1~nm1~hardy1  network management framework (OpenVPN plugin)

```

Everything is from Aug 12th...:confused:
The only difference I see is that the openvpn plugin and networkmanager-gnome are nm1~hardy1

---

### Post by asac on 2008-08-15
> **hfdragon said:**
> I think I upgraded everything... 


Everything is from Aug 12th...:confused:
The only difference I see is that the openvpn plugin and networkmanager-gnome are nm1~hardy1


please paste the output of

```

cat /etc/NetworkManager/VPN/nm-openvpn-service.name

```

---

### Post by hfdragon on 2008-08-15
Here it is :
```
christophe@christophe-laptop:~$ cat /etc/NetworkManager/VPN/nm-openvpn-service.name

[VPN Connection]
name=openvpn
service=org.freedesktop.NetworkManager.openvpn
program=/usr/lib/network-manager-openvpn/nm-openvpn-service

[GNOME]
auth-dialog=/usr/lib/network-manager-openvpn/nm-openvpn-auth-dialog
properties=libnm-openvpn-properties


```

---

### Post by asac on 2008-08-15
> **hfdragon said:**
> Here it is :
```
christophe@christophe-laptop:~$ cat /etc/NetworkManager/VPN/nm-openvpn-service.name

[VPN Connection]
name=openvpn
service=org.freedesktop.NetworkManager.openvpn
program=/usr/lib/network-manager-openvpn/nm-openvpn-service

[GNOME]
auth-dialog=/usr/lib/network-manager-openvpn/nm-openvpn-auth-dialog
properties=libnm-openvpn-properties


```

That looks good. not sure whats going on. have you restarted your system? if not, please do.

If all that doesnt help, I'll look in the code.

---

### Post by hfdragon on 2008-08-15
> **asac said:**
> That looks good. not sure whats going on. have you restarted your system? if not, please do.

If all that doesnt help, I'll look in the code.

Yes I restarted my computer (twice) and still have this error.

Can it be because i did modify the nm-openvpn-service.conf when trying to install the openvpn plugin as explained earlier in this thread ?

Maybe I should try with the 'original' one ?

Here is my /etc/dbus-1/system.d/nm-openvpn-service.conf

```
christophe@christophe-laptop:/etc/dbus-1/system.d$ cat nm-openvpn-service.conf 
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
	<policy user="root">
		<allow own="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_interface="org.freedesktop.NetworkManager.openvpn"/>
	</policy>
        <policy user="christophe">
		<allow own="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_interface="org.freedesktop.NetworkManager.openvpn"/>
	</policy>
	<policy context="default">
		<allow own="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_interface="org.freedesktop.NetworkManager.openvpn"/>
	</policy>
</busconfig>

```

---

### Post by polardesign on 2008-08-16
I have just purchased a T-mobile USB Stick III (The latest) I was having problems until I dowmloaded the network tools.

I now a t-mobile connection with Linux

Superb

My Windows to Linux transition is nearly complete.

---

### Post by legolas_w on 2008-08-17
Hi
Can you please let me know how I can revert back to old version of network manager?

Thanks

---

### Post by asac on 2008-08-18
> **hfdragon said:**
> Yes I restarted my computer (twice) and still have this error.

Can it be because i did modify the nm-openvpn-service.conf when trying to install the openvpn plugin as explained earlier in this thread ?

Maybe I should try with the 'original' one ?


Yes, please sudo apt-get remove --purge network-manager-openvpn then remove that config file and install network-manager-openvpn again.

---

### Post by asac on 2008-08-18
> **polardesign said:**
> I have just purchased a T-mobile USB Stick III (The latest) I was having problems until I dowmloaded the network tools.

I now a t-mobile connection with Linux

Superb

My Windows to Linux transition is nearly complete.

Cool. Thanks for testing. Please remember to add your hardware to [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

---

### Post by Darrena on 2008-08-18
Alexander,

I purged the package and then installed it again and this is what I get:
```

Aug 18 10:06:20 GV002462 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Aug 18 10:06:20 GV002462 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Aug 18 10:06:20 GV002462 NetworkManager: nm_vpn_connection_activate: assertion `nm_vpn_connection_get_vpn_state (connection) == NM_VPN_CONNECTION_STATE_PREPARE' failed
Aug 18 10:06:20 GV002462 NetworkManager: <info>  VPN plugin state changed: 1 
Aug 18 10:06:21 GV002462 kernel: [  135.224282] printk: 3 messages suppressed.
Aug 18 10:06:21 GV002462 kernel: [  135.224289] nm-openvpn-auth[6406]: segfault at 00000001 eip b77b4791 esp bfd31e60 error 4
Aug 18 10:06:21 GV002462 NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.301 (nma_vpn_request_password): canceled. 
```

Would it help to get a backtrace using gdb?

Thanks!

---

### Post by asac on 2008-08-18
FYI, i uploaded a new snapshot from today for everything to network-manager PPA. please test and report any regressions here.

I'll upload this to intrepid if I dont get any regressions reported within a few hours ;)

---

### Post by Darrena on 2008-08-18
> **asac said:**
> FYI, i uploaded a new snapshot from today for everything to network-manager PPA. please test and report any regressions here.

I'll upload this to intrepid if I dont get any regressions reported within a few hours ;)

That worked!   There is still an issue with routing but I posted that to the NM list yesterday.

---

### Post by scarhill on 2008-08-18
Hi, I installed NM 0.7 last night and upgraded to the latest version today. First of all, great work! The CDMA coonection code seems to work flawlessly with a Verizon AC 595.

I haven't had any luck making a PPTP VPN connection to my employer's Windows network, which works with 0.6 over a wired or wireless connection, but not using the aircard. I've tried various combinations of options, but always get the same error. Here's the relevant section of /var/log/syslog:

```

Aug 18 12:18:05 jim-d620 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Aug 18 12:18:05 jim-d620 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 7115 
Aug 18 12:18:05 jim-d620 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Aug 18 12:18:05 jim-d620 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Aug 18 12:18:05 jim-d620 NetworkManager: nm_vpn_connection_activate: assertion `nm_vpn_connection_get_vpn_state (connection) == NM_VPN_CONNECTION_STATE_PREPARE' failed
Aug 18 12:18:08 jim-d620 NetworkManager: <info>  VPN plugin state changed: 3 
Aug 18 12:18:08 jim-d620 NetworkManager: <info>  VPN connection 'VPN Connection' (Connect) reply received. 
Aug 18 12:18:08 jim-d620 pppd[7118]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Aug 18 12:18:08 jim-d620 pppd[7118]: pppd 2.4.4 started by root, uid 0
Aug 18 12:18:08 jim-d620 pptp[7119]: nm-pptp-service-7115 log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Aug 18 12:18:08 jim-d620 pppd[7118]: Using interface ppp1
Aug 18 12:18:08 jim-d620 pppd[7118]: Connect: ppp1 <--> /dev/pts/1
Aug 18 12:18:08 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Aug 18 12:18:09 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Aug 18 12:18:09 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Aug 18 12:18:09 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Aug 18 12:18:10 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Aug 18 12:18:10 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 23929). 
Aug 18 12:18:11 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Aug 18 12:18:11 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is 00000000, recv_accm is FFFFFFFF
Aug 18 12:18:11 jim-d620 pptp[7122]: nm-pptp-service-7115 warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Aug 18 12:18:11 jim-d620 pppd[7118]: LCP terminated by peer (kEg6^@<M-Mt^@^@^BM-3)
Aug 18 12:18:11 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Aug 18 12:18:11 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Aug 18 12:18:11 jim-d620 pptp[7122]: nm-pptp-service-7115 warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Aug 18 12:18:12 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_disp:pptp_ctrl.c:911]: Received Call Clear Request.
Aug 18 12:18:14 jim-d620 pppd[7118]: Connection terminated.
Aug 18 12:18:14 jim-d620 pppd[7118]: Modem hangup
Aug 18 12:18:14 jim-d620 pptp[7119]: nm-pptp-service-7115 warn[decaps_hdlc:pptp_gre.c:197]: short read (-1): Input/output error
Aug 18 12:18:14 jim-d620 pptp[7119]: nm-pptp-service-7115 warn[decaps_hdlc:pptp_gre.c:209]: pppd may have shutdown, see pppd log
Aug 18 12:18:14 jim-d620 pptp[7122]: nm-pptp-service-7115 log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Aug 18 12:18:14 jim-d620 pptp[7122]: nm-pptp-service-7115 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Aug 18 12:18:14 jim-d620 pptp[7122]: nm-pptp-service-7115 log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Aug 18 12:18:14 jim-d620 pppd[7118]: Exit.
Aug 18 12:18:14 jim-d620 NetworkManager: <info>  VPN plugin state changed: 6 
Aug 18 12:18:14 jim-d620 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 

```

Any suggestions of things to try?

Thanks,

Jim

---

### Post by asac on 2008-08-18
> **scarhill said:**
> Hi, I installed NM 0.7 last night and upgraded to the latest version today. First of all, great work! The CDMA coonection code seems to work flawlessly with a Verizon AC 595. 

Thanks for testing. Please remember to add your findings (hardware + provider) to [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

> **scarhill said:**
> 
I haven't had any luck making a PPTP VPN connection to my employer's Windows network, which works with 0.6 over a wired or wireless connection, but not using the aircard. I've tried various combinations of options, but always get the same error. Here's the relevant section of /var/log/syslog:


Unforunately, I dont have any pptp setup where I can test this VPN type. Please open a bug against network-manager-pptp, and post the bug id here. We can then do the detailed evaluation in bug.

---

### Post by timcredible on 2008-08-18
> **scarhill said:**
> 
I haven't had any luck making a PPTP VPN connection to my employer's Windows network, which works with 0.6 over a wired or wireless connection, 

vpn connections sometimes require 2 ip addresses, and wireless broadband connection usually don't allow that.  if it works over wired and wireless, but not wireless broadband, that's probably why.

---

### Post by scarhill on 2008-08-18
> **timcredible said:**
> vpn connections sometimes require 2 ip addresses, and wireless broadband connection usually don't allow that.  if it works over wired and wireless, but not wireless broadband, that's probably why.
VPN using the Aircard works fine in Windows, so I don't think that's the problem. Instead I think it's an instance of this issue:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/145107]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/145107")

Jim

---

### Post by asac on 2008-08-18
> **scarhill said:**
> VPN using the Aircard works fine in Windows, so I don't think that's the problem. Instead I think it's an instance of this issue:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/145107]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/145107")

Jim

NetworkManager allows you to configure IPv4 settings manually since 0.7 ... for that go to the connection editor and select the IPv4 tab. use Manual and configure your static IP address and your DNS servers manually.

---

### Post by scarhill on 2008-08-18
> **asac said:**
> Thanks for testing. Please remember to add your findings (hardware + provider) to [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

Unforunately, I dont have any pptp setup where I can test this VPN type. Please open a bug against network-manager-pptp, and post the bug id here. We can then do the detailed evaluation in bug.

I updated the wiki and reported the VPN error as bug [259168]("https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/259168").

Jim

---

### Post by charles.figura on 2008-08-18
I just tried installing (as per page 1 w/ updated repository) on my kubuntu hardy system.  No problems installing, but some weird behavior.

1.  Wired network works fine, although on bootup (after connect) tray icon is green world rather than wired icon.  If I go offline, I get the greyed-out world.  If I go online, THEN I get the wired icon.

2.  I've been trying to set up a wireless connection.  It sees the wireless network and identifies if it's secured or not (I've reconfigured it to test) and it lets me set up the connection, but won't connect, and doesn't even look like it's trying (according to the icon).  If I run knetworkmanager from the command line it gives me the following message everytime I mouseover the tray icon:

knetworkmanager: WARNING: [AccessPoint* WirelessDevice::getActiveAccessPoint()] No object for active access point found!
knetworkmanager: WARNING: [AccessPoint* WirelessDevice::getActiveAccessPoint()] No object for active access point found!

Any ideas?  It didn't give me any problems installing or other error messages, so I'm a little at a loss.

Thanks!

-C

---

### Post by asac on 2008-08-18
> **charles.figura said:**
> I just tried installing (as per page 1 w/ updated repository) on my kubuntu hardy system.  No problems installing, but some weird behavior.

1.  Wired network works fine, although on bootup (after connect) tray icon is green world rather than wired icon.  If I go offline, I get the greyed-out world.  If I go online, THEN I get the wired icon.

2.  I've been trying to set up a wireless connection.  It sees the wireless network and identifies if it's secured or not (I've reconfigured it to test) and it lets me set up the connection, but won't connect, and doesn't even look like it's trying (according to the icon).  If I run knetworkmanager from the command line it gives me the following message everytime I mouseover the tray icon:

knetworkmanager: WARNING: [AccessPoint* WirelessDevice::getActiveAccessPoint()] No object for active access point found!
knetworkmanager: WARNING: [AccessPoint* WirelessDevice::getActiveAccessPoint()] No object for active access point found!

Any ideas?  It didn't give me any problems installing or other error messages, so I'm a little at a loss.

Thanks!

-C

knetworkmanager is probably outdated. Ill try to update that soon.

---

### Post by diverse_izzue on 2008-08-19
Connecting to an OpenVPN has been working for me since this morning. Thanks!

---

### Post by trumpcouptimmy on 2008-08-19
Perhaps I'm not advanced enough to try this out, but under nm-six the security settings were remembered as I wished but at every boot-up, nm-seven keeps asking me the security questions again. I've tried to make it remember but it's like me-older than yesterday and forgets!

No problem with either version detecting my wireless and working, just remembering the security settings. On this up-to-date Hardy desktop, I have both a wired connection and wireless.

---

### Post by scarhill on 2008-08-20
Is there a way to set debug logging for the PPTP VPN plugin? I'm not seeing it in the UI, but perhaps I'm missing something.

Thanks,

Jim

---

### Post by charles.figura on 2008-08-23
Is there a changelog that I can watch to see if knetworkmanager has been updated?  It's not usable in it's current state (can't connect to wireless networks), so I installed wicd in the meantime rather than trying to roll back networkmanager.  Thanks!

---

### Post by apedraza on 2008-08-23
As of the last update, nm-applet keeps crashing with a segfault. This happens when I try to connect to a wpa2 tls cert network. It was working extremely well before.   

I don't know if the update broke it or the fact that I had to install new certificates.. due that the old ones expired.  This however, should not cause the nm-applet to crash.

I'll keep trying...

---

### Post by apedraza on 2008-08-24
Yesterdsy's update, definitely broke the wpa2 TLS certificates.

Looking at the updates, nm-applet was not updated. It usually is udated at the same time that networkanager. Here is the log:

Commit Log for Fri Aug 22 08:52:25 2008


Upgraded the following packages:
libnm-glib0 (0.7~~svn20080818t061112+eni0-0ubuntu1~nm1~hardy1) to 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1
libnm-util0 (0.7~~svn20080818t061112+eni0-0ubuntu1~nm1~hardy1) to 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1
network-manager (0.7~~svn20080818t061112+eni0-0ubuntu1~nm1~hardy1) to 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1

On syslog I get the following when trying to connect:

Aug 23 23:00:08 alberto-HP8710w kernel: [ 2128.617714] nm-applet[12294]: segfault at 34706577 eip b754e1d0 esp bffc6010 error 4

I also get this if I run nm-applet from the terminal:

** (nm-applet:12294): WARNING **: Invalid connection: 'NMSetting8021x' / 'identity' invalid: 2

** (nm-applet:12294): WARNING **: <WARN>  applet_menu_item_activate_helper(): Invalid connection; asking for more information.

---

### Post by charles.figura on 2008-08-24
> **charles.figura said:**
> If I run knetworkmanager from the command line it gives me the following message everytime I mouseover the tray icon:

knetworkmanager: WARNING: [AccessPoint* WirelessDevice::getActiveAccessPoint()] No object for active access point found!
knetworkmanager: WARNING: [AccessPoint* WirelessDevice::getActiveAccessPoint()] No object for active access point found!



One other note - when I right-click on the access point, I get the command-line error message:
Activate Connection /org/freedesktop/NetworkManagerSettings/Connection/1 on Device /org/freedesktop/Hal/devices/net_00_13_02_5b_6b_af

For what it's worth....

---

### Post by apedraza on 2008-08-24
> **apedraza said:**
> Yesterdsy's update, definitely broke the wpa2 TLS certificates.

Looking at the updates, nm-applet was not updated. It usually is udated at the same time that networkanager. Here is the log:

Commit Log for Fri Aug 22 08:52:25 2008


Upgraded the following packages:
libnm-glib0 (0.7~~svn20080818t061112+eni0-0ubuntu1~nm1~hardy1) to 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1
libnm-util0 (0.7~~svn20080818t061112+eni0-0ubuntu1~nm1~hardy1) to 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1
network-manager (0.7~~svn20080818t061112+eni0-0ubuntu1~nm1~hardy1) to 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1

On syslog I get the following when trying to connect:

Aug 23 23:00:08 alberto-HP8710w kernel: [ 2128.617714] nm-applet[12294]: segfault at 34706577 eip b754e1d0 esp bffc6010 error 4

I also get this if I run nm-applet from the terminal:

** (nm-applet:12294): WARNING **: Invalid connection: 'NMSetting8021x' / 'identity' invalid: 2

** (nm-applet:12294): WARNING **: <WARN>  applet_menu_item_activate_helper(): Invalid connection; asking for more information.

Upon further investigation, It seems like nm-applet cannot write the wpa certificate key secret to the keyring. After it tries to write to it, it crashes.  This bug might be coming from earlier updates.  The reason I encountered it last night is becuase my certificates expired and I had to provide the new ones to the network.  This is were all the trouble started.  Apparently, nm-applet can't save the certificate paths and the key secret to the keyring.

---

### Post by Hudy on 2008-08-28
```
0 root chubby / > apt-show-versions | egrep -i 'nm-|network-man'
network-manager/hardy uptodate 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1
network-manager-gnome/hardy uptodate 0.7~~svn20080817t183748-0ubuntu1~nm1~hardy1
libnm-util0/hardy uptodate 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1
libnm-glib-dev/hardy uptodate 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1
libnm-glib0/hardy uptodate 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1

```
I'm seeing nm-applet crash too: 

kernel: [  309.296800] nm-applet[17788]: segfault at 3470657b eip b75c4df2 esp bf805278 error 4

Since nm-applet is in network-manager-gnome, I thought it might be important to point out that said package is older than the others in the set.... 

BTW, on my 32-bit T60p with Atheros ("AR5212 802.11abg NIC (rev 01)"), I can't get a wifi connection *or* a LEAP connection to come up.  I'm wired only.  It was problematic in base Hardy too (0.6.6-0ubuntu5), which is why I'm here trying this...

Atached find grepped out networkmanager & nm-applet syslog entries from today.

Please let me know how else I might be able to help.

Thanks

/Bill

---

### Post by heruan on 2008-08-28
> **apedraza said:**
> Upon further investigation, It seems like nm-applet cannot write the wpa certificate key secret to the keyring. After it tries to write to it, it crashes.  This bug might be coming from earlier updates.  The reason I encountered it last night is becuase my certificates expired and I had to provide the new ones to the network.  This is were all the trouble started.  Apparently, nm-applet can't save the certificate paths and the key secret to the keyring.

I confirm this. I've just installed Ubuntu Intrepid and nm-applet crashes upon saving EAP-TLS certificate infos.
```

gnome-keyring 2.23.90-0ubuntu1
network-manager 0.7~~svn20080818t061112+eni1-0ubuntu1~nm1
network-manager-gnome 0.7~~svn20080817t183748-0ubuntu1

```

And launching nm-connection-editor from cli:
```

** (nm-connection-editor:12136): WARNING **: Invalid setting Wireless Security: Invalid wireless security
... same message repeated many times ...
** (nm-connection-editor:12136): WARNING **: Invalid setting Wireless Security: Invalid wireless security
Segmentation fault (core dumped)

```

---

### Post by Infra on 2008-08-28
I updated today and now my wireless doesn't want to connect to my network. It just keeps asking for the wpa/wpa2 password.

---

### Post by Polygon on 2008-08-29
yeah, this is annoying. i cant connect to my campus's wpa network cause network manager now crashes whenever i try.

and when i try to connect to said network:

[[IMG]http://img154.imageshack.us/img154/975/screenshotwirelessnetwooa5.th.png[/IMG]](http://img154.imageshack.us/my.php?image=screenshotwirelessnetwooa5.png)

i get this in terminal:

[[IMG]http://img361.imageshack.us/img361/8882/screenshotmi5.th.png[/IMG]](http://img361.imageshack.us/my.php?image=screenshotmi5.png)

---

### Post by charles.figura on 2008-08-29
Okay, since knetworkmanager 0.7 doesn't work for wireless at all, is there a way to roll back to the stock knetworkmanager?  Or hope that knetworkmanager 0.7 will be fixed soon?

---

### Post by Polygon on 2008-08-29
you can force the version in synaptic to the standard hardy one, and do this for every package that the PPA installed

---

### Post by asac on 2008-09-01
@crash reporting for intrepid:

If you are on intrepid and nm-applet crashes, you should be able to find a crash report in the /var/crash directory.

You can then submit that crash report (if apport doesnt pop-up automatically) by double clicking on it in nautilus.

Without such a crash report its quite hard to guess whats going on.

---

### Post by apedraza on 2008-09-01
> **asac said:**
> @crash reporting for intrepid:

If you are on intrepid and nm-applet crashes, you should be able to find a crash report in the /var/crash directory.

You can then submit that crash report (if apport doesnt pop-up automatically) by double clicking on it in nautilus.

Without such a crash report its quite hard to guess whats going on.

Alexander, nm-applet segfaults whenever you try to configure and save a wpa2 tls network. It does not appear to happen with other network types. In fact, when you try to configure the network, as soon as you type the last charachter of the certificate key, it segfaults. It does not even give you a chance to press the ok key.

I am running hardy on an HP 8710w.

Thank you for all your help.

---

### Post by Gourgi on 2008-09-02
```
route add -net 192.168.0.0 netmask 255.255.240.0 gw 192.168.6.2 dev eth0 
```
i want to do this through the Network manager Gui options but i'm a little confused about how to add routes.
i edit eth0 through NM 0.7 , i go to 'Ipv4  Settings' Tab and i click on 'routes' .
Then i see this 
```

      Address  |  Prefix  | Gateway  |  Metric 

```
but where i have to put the netmask ???
in 'prefix' maybe ? if yes in what format?

anyone can help me ?

---

### Post by Polygon on 2008-09-03
i have reported a bug here about nm-7.0 crashing on wpa tls networks:

[https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/264263](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/264263)

---

### Post by Polygon on 2008-09-05
does anyone have any previous packages of network manager? **i need wpa tls to work D: ** my laptop only gets internet with network manager 0.7 and wpa used to work before, but my laptop is a nice brick since i cant connect to my campus's wifi network.

---

### Post by heruan on 2008-09-05
> **Polygon said:**
> does anyone have any previous packages of network manager? **i need wpa tls to work D: ** my laptop only gets internet with network manager 0.7 and wpa used to work before, but my laptop is a nice brick since i cant connect to my campus's wifi network.

Unfortunately the issue seems not to be related to the latest versions of NM, but with something else. In fact, I experience the same problem with both version from Intrepid repository and PPA.

---

### Post by 1985xr200 on 2008-09-05
this is my first posting and I am brand new to this world and seem to not know enough to get NM installed...or even finding it. I am working fro my windows laptop while trying to get 3G modem to work on PC with Ubuntu OS. It appears my machien doesn't detect the modem....

thanks
Paul

---

### Post by jpeach on 2008-09-05
The command listed in comment #82 is outdated.  As of this posting, this is the correct command.
```
sudo apt-get install  network-manager=0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1 libnm-glib0=0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1 libnm-util0=0.7~~svn20080818t061112+eni1-0ubuntu1~nm1~hardy1 network-manager-gnome=0.7~~svn20080817t183748-0ubuntu1~nm1~hardy1

```

---

### Post by apedraza on 2008-09-05
> **Polygon said:**
> does anyone have any previous packages of network manager? **i need wpa tls to work D: ** my laptop only gets internet with network manager 0.7 and wpa used to work before, but my laptop is a nice brick since i cant connect to my campus's wifi network.

Polygon,  Check your /var/cache/apt/archives the old packages should be there. 

sudo su

cd /var/cache/apt/archives
 
dpkg --install --force-downgrade libnm-glib0_0.7~~svn20080818t061112+eni0-0ubuntu1~nm1~hardy1_i386.deb libnm-util0_0.7~~svn20080818t061112+eni0-0ubuntu1~nm1~hardy1_i386.deb network-manager_0.7~~svn20080818t061112+eni0-0ubuntu1~nm1~hardy1_i386.deb  network-manager-gnome_0.7~~svn20080812t174537-0ubuntu1~nm1~hardy1_i386.deb

The dpkg statement is in one line....  

Also you might try to just downgrade the nm-applet package first. I first downgraded the three packages from the last update but that did not solve the issue, I had to downgrade nm-applet as well to the previous one.  After the downgrade, re-boot and try to auto connect to your network.. It should allow you to save the certificate path and the certificate key.  You should be able to connect after that...

Good luck... remember all this is experimental and is subject to bomb. Please make a backup of your important stuff before just in case....

---

### Post by Soarer on 2008-09-06
I installed 0.7 from the added repositories as suggested on Hardy 64. Plugged in my T-Mobile 3G dongle, unplugged my wired network, hit 'Connect Automatically' and it just worked.

This is excellent! Thanks very much to everyone involved. :)

---

### Post by Polygon on 2008-09-07
i cant install it from the cache as i installed network-manager.07 starting from the latest version (the one with problems) so i never had the previous version installed, (because i had vista on this comp and i reinstalled ubuntu)

---

### Post by IntuitiveNipple on 2008-09-07
Use the [PPA superseded list](https://edge.launchpad.net/~network-manager/+archive?field.name_filter=network-manager&field.status_filter=superseded) to find the version you require, expand the entry and scroll down to the list of files, download those you require.


Once downloaded, use dpkg to install them:
```

sudo dpkg -i ...

```
Install the support libraries and optional packages such as *-applet, *-openvpn at the same time... the 'deb files can be listed one after another on the command-line.

---

### Post by apedraza on 2008-09-07
> **Polygon said:**
> i cant install it from the cache as i installed network-manager.07 starting from the latest version (the one with problems) so i never had the previous version installed, (because i had vista on this comp and i reinstalled ubuntu)

Here they are:

I would try first to install the nm-applet. I think that is the only package that its needed.

---

### Post by Polygon on 2008-09-08
doesn't work, either it tries to connect to the wpa network and just sits there trying to connect or nm-applet crashes. Figures.

---

### Post by apedraza on 2008-09-08
> **Polygon said:**
> doesn't work, either it tries to connect to the wpa network and just sits there trying to connect or nm-applet crashes. Figures.

Don't save the configuration from the edit connections menu, this version crashes too.  Try instead to connect to the AP and once the certificate dialog comes up, then input all your information.  For WPA2 TLS you need to have 3 separate certificates. (Your user certificate, the Certificate Authority Certificate and your private key certificate.) + you need to put in your password that protects your private key certificate. You also need to fill out the identity field. Once you click 'ok', nm-applet should save the connection in the configuration registry and the private key to the keyring.

Let me know if it works.

---

### Post by apedraza on 2008-09-08
Forgot to mention that the current wifi drivers for intel are very iffy. I was having so many problems connecting before and I thought that it was nm 0.7 fault. Out of sheer desperation, I downloaded and compiled a new driver  from LinuxWireless.org. That made all the difference. I am now able to connect reliably.

Hope this helps.

---

### Post by apedraza on 2008-09-09
The latest update sees to take care of the WPA/TLS problem.

...PPTP still does not work...  no secrets available....

---

### Post by Darrena on 2008-09-10
I am getting this error with the OpenVPN plugin:

nm-openvpn[7614]: Options error: Unrecognized option or missing parameter(s) in [CMD-LINE]:1: script-security (2.1_rc7)

Is this the result of that script that checks the keys from the OpenSSL vulnerability?

---

### Post by frediE on 2008-09-10
I just did the update network-manager-vpnc 0.7~~svn20080908 and it gets a  little further...  now i am getting a balloon pop-up shown by nm-applet that states....  "The VPN connection 'My VPN Connection' failed because the VPN service stopped unexpectedly".

Any thoughts on this?  Trying to connect to a cisco vpn.

---

### Post by apedraza on 2008-09-10
> **frediE said:**
> I just did the update network-manager-vpnc 0.7~~svn20080908 and it gets a  little further...  now i am getting a balloon pop-up shown by nm-applet that states....  "The VPN connection 'My VPN Connection' failed because the VPN service stopped unexpectedly".

Any thoughts on this?  Trying to connect to a cisco vpn.

Same thing with PPTP VPN.  No connection.  Also, the newest nm-applet still cannot save wireless info from the editor. (When you press edit connections)

The error is: UPDATIG CONNECTION FAILED -- CLIENT CERT

---

### Post by RobotJox on 2008-09-11
> **frediE said:**
> I just did the update network-manager-vpnc 0.7~~svn20080908 and it gets a  little further...  now i am getting a balloon pop-up shown by nm-applet that states....  "The VPN connection 'My VPN Connection' failed because the VPN service stopped unexpectedly".

Any thoughts on this?  Trying to connect to a cisco vpn.

exactly the same problem for me in intrepid - only I am trying to connect to pptp vpn

---

### Post by asac on 2008-09-12
ok. a new gem has landed in the network-manager PPA: the mobile broadband wizard which is ment to ease the setup of 3g connections.

the packages that have this are:

network-manager-gnome 0.7~~svn20080907t033843-0ubuntu3~mbca1 (intrepid)
network-manager-gnome 0.7~~svn20080907t033843-0ubuntu3~mbca1~nm1 (hardy)

once you have installed them ensure that you also have libmbca0 installed.

next time you plug in a 3g card or phone which is recognized and you dont have a suitable connection setup you should see the wizard pop up.

alternatively it should show up when you go create "New" connection in the connection-editor "Mobile Broadband" tab.

Please test and report back.

---

### Post by [Psyduck] on 2008-09-13
I still have issues with the latest PPA.
After disabling and enabling wifi on my Eeee PC 1000H, the nm-applet dissapears and I get this message in syslog
"NetworkManager: Failed to register GObject with DBusConnection"

---

### Post by asac on 2008-09-16
> **'[Psyduck] said:**
> I still have issues with the latest PPA.
After disabling and enabling wifi on my Eeee PC 1000H, the nm-applet dissapears and I get this message in syslog
"NetworkManager: Failed to register GObject with DBusConnection"

could you attach your complete syslog _after_ reproducing this? (maybe as a file and not as a paste)

---

### Post by asac on 2008-09-16
> **Darrena said:**
> I am getting this error with the OpenVPN plugin:

nm-openvpn[7614]: Options error: Unrecognized option or missing parameter(s) in [CMD-LINE]:1: script-security (2.1_rc7)

Is this the result of that script that checks the keys from the OpenSSL vulnerability?

is that on hardy or intrepid? Can you attach the complete syslog after reproducing this to a network-manager-openvpn bug and give us the bug id?

Thanks.

---

### Post by [Psyduck] on 2008-09-16
Here's my syslog. Made som marks in the file so you easily can see where I enabled/disabled wifi.

I'm using Hardy with the Eee PC customized kernel found at [www.array.org](www.array.org).

---

### Post by asac on 2008-09-16
> **'[Psyduck] said:**
> Here's my syslog. Made som marks in the file so you easily can see where I enabled/disabled wifi.

I'm using Hardy with the Eee PC customized kernel found at [www.array.org](www.array.org).


Just uploaded a new round of packages which fix a resume crashes that look related to what you see. please test. The versions are:

Uploading to ppa-nm (via ftp to ppa.launchpad.net):
network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1.dsc: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1.diff.gz: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1_source.changes: done.
Successfully uploaded packages.

Uploading to ppa-nm (via ftp to ppa.launchpad.net):
network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2.dsc: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2.diff.gz: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2_source.changes: done.

---

### Post by JGJones on 2008-09-18
The NetworkManager works utterly fantastic for me.

One of the key issue for me is the ease of using a 3G connection.

I have a Vodafone Mobile Connect (model- Huawei E172) this is recognised by the Network Manager with no problem.

When the latest update included an easy to add script for different plans, I decided to make use of this and test.

So I selected - UK - Vodafone (Contact)

This fails completely and I was never able to connect.

My fix is quite simple:

The script put the dialup number as *99***1#

I changed this to: *99#

It now connect successfully...however it then prompts for a password (which is web) - saving this by editing the connection and adding the password made no difference.

I will search for any bug report that does this already and if not then add it.

Cheers

---

### Post by nightfrost on 2008-09-19
> **asac said:**
> Just uploaded a new round of packages which fix a resume crashes that look related to what you see. please test. The versions are:

Uploading to ppa-nm (via ftp to ppa.launchpad.net):
network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1.dsc: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1.diff.gz: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2~hardy1_source.changes: done.
Successfully uploaded packages.

Uploading to ppa-nm (via ftp to ppa.launchpad.net):
network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2.dsc: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2.diff.gz: done. network-manager_0.7~~svn20080908t183521+eni0-0ubuntu3~nm2_source.changes: done.


The updated packages solve this obnoxious problem on my hardy machine. Thanks!

---

### Post by JGJones on 2008-09-19
> **nightfrost said:**
> The updated packages solve this obnoxious problem on my hardy machine. Thanks!

Confirming the same thing on my machine thanks!

---

### Post by asac on 2008-09-19
> **JGJones said:**
> The NetworkManager works utterly fantastic for me.

One of the key issue for me is the ease of using a 3G connection.

I have a Vodafone Mobile Connect (model- Huawei E172) this is recognised by the Network Manager with no problem.

When the latest update included an easy to add script for different plans, I decided to make use of this and test.

So I selected - UK - Vodafone (Contact)

This fails completely and I was never able to connect.

My fix is quite simple:

The script put the dialup number as *99***1#

I changed this to: *99#

It now connect successfully...however it then prompts for a password (which is web) - saving this by editing the connection and adding the password made no difference.

I will search for any bug report that does this already and if not then add it.

Cheers

The dialup number problem is a known bug. I don't have the bug number at hand though and launchpad is currently down. Maybe post the bug id here when you find it.

For the other thing, please open _new_ bugs instead of attaching to other bugs that sound related (unless you are really sure you are seeing the same problem).

Its always better to mark bugs as a dupe later on. Thanks!

---

### Post by leandir on 2008-09-19
Well, I have a rather annoying problem with nm-0.7, up-to-date thanks to the repository. Actually, two.

1- It is bug #209602 on Launchpad. Although it started (and remained) a driver-related bug for months, after it was finally solved some weeks ago I discovered that using nm-0.7 I am unable to connect to the network. This is purely due to some bug in the NetworkManager; as I have found that NM is able to connect using another driver (ipw3945), while wpa_supplicant is able to connect to the network using the new driver (going from the cli, of course). I am unsure if I have to file a new bug about this.

2- NM is unable to store network passwords inside the gnome-keyring, thus forcing me to re-enter the information every time I disconnect from a network (because of reboot, suspend, etc.). Quite annoying, really, but as I connect to a limited number of networks, I can live with this. Which I happily do because ...

As JGJones I own a Vodafone Huawei modem, and connection to 3G has never been easier. With NM 0.6.x it was and is a disaster. The technology behind it is marvelous :-)

So keep it on with the good work and let us know how to help in testing :-)

---

### Post by lazorde on 2008-09-20
Hello 

I have  3G Mobile Connect (model- ZTE MF628 )

Network Manager 0.7 Not supported 

can you plaz help me ?

i want driver for ubuntu 8.04


thank you

---

### Post by Darrena on 2008-09-20
Alexander,

It looks like the OpenVPN plugin is broken on Hardy:

Sep 20 14:04:23 GV002462 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Sep 20 14:04:23 GV002462 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Sep 20 14:04:23 GV002462 NetworkManager: nm_vpn_connection_activate: assertion `nm_vpn_connection_get_vpn_state (connection) == NM_VPN_CONNECTION_STATE_PREPARE' failed
Sep 20 14:04:23 GV002462 NetworkManager: <info>  VPN plugin state changed: 1 
Sep 20 14:04:23 GV002462 NetworkManager: <info>  VPN plugin state changed: 3 
Sep 20 14:04:23 GV002462 NetworkManager: <info>  VPN connection 'Remote8080' (Connect) reply received. 
Sep 20 14:04:23 GV002462 nm-openvpn[19576]: Options error: Unrecognized option or missing parameter(s) in [CMD-LINE]:1: script-security (2.1_rc7)
Sep 20 14:04:23 GV002462 nm-openvpn[19576]: Use --help for more information.
Sep 20 14:04:23 GV002462 NetworkManager: <info>  VPN plugin state changed: 6 
Sep 20 14:04:23 GV002462 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Sep 20 14:04:35 GV002462 NetworkManager: <debug> [1221933875.259346] ensure_killed(): waiting for vpn service pid 19572 to exit 
Sep 20 14:04:35 GV002462 NetworkManager: <debug> [1221933875.259499] ensure_killed(): vpn service pid 19572 cleaned up 


Dan explained this issue here:

[http://mail.gnome.org/archives/networkmanager-list/2008-September/msg00003.html](http://mail.gnome.org/archives/networkmanager-list/2008-September/msg00003.html)

Any chance we can patch it for Hardy?  

Thanks!

---

### Post by Darrena on 2008-09-20
Thinking about this, backporting OpenVPN from Intrepid is probably easier than keeping two different packages of Network-Manager-OpenVPN for Intrepid and Hardy.

If you would like me to submit the simple patch for Hardy I can do that but I suspect that using your PPA to push an updated OpenVPN and increase the OpenVPN dependencies in your PPA is easier

Thanks!
Darren

---

### Post by thund3rman on 2008-09-22
I've tried installing openvpn from interpid (plus dependencies like openssl) and it worked. But it should be easier to manage just to recompile openvpn to use openssl from hardy.

If ASAC could provide that in his ppa it would be great :)

---

### Post by blueworld on 2008-09-22
Hi,

I got the Vodafone Mobile Connect (model- Huawei E172)  working with *99# and a blank password not "web" using Network Manager 0.7 on an Acer Aspire One witn Ubuntu 8.04.1 and the Ubuntu Netbook Remix :) Very happy with it.

---

### Post by heruan on 2008-09-27
Problems with certificate settings in WPA-EAP TLS are still an issue. For example, when trying to save modified settings I get: "Updating connection failed: client-cert." Launching from shell:

```

** (nm-connection-editor:18580): WARNING **: <WARN>  update(): update: Invalid connection: 'NMSetting8021x' / 'client-cert' invalid: 2

```

---

### Post by asac on 2008-10-02
> **Darrena said:**
> Thinking about this, backporting OpenVPN from Intrepid is probably easier than keeping two different packages of Network-Manager-OpenVPN for Intrepid and Hardy.

Uploaded openvpn_2.1~rc9-3ubuntu2~nm1~hardy1_source.changes to hardy network-manager PPA. I dont think that we need to bump the required version. people that track the PPA will automatically get openvpn when they upgrade.

---

### Post by Plumtreed on 2008-10-02
Please,tell me how to get Network Manager 0.7! I can't find it in Synaptic. What is that initial step in the first thread here?

Will I be getting a version that has been 'upgraded' to include corrections to the problems that have cropped up in this thread?

I'm Have a Acer Asptre 5315, 560, running Hardy. New and still stumbling in things Ubuntu!

---

### Post by heruan on 2008-10-06
With the latest version, the applet says that wired device is unmanaged. It worked before!

---

### Post by ShirishAg75 on 2008-10-06
By latest version of network-manager do you mean  0.7~~svn20081004t22504 version or some other? Find out by doing a 

dpkg -l network-manager

Update 07/10/08 9:21 AM :- I just restarted the machine and I get a similar no connectivity signal from the network-manager applet. I am using the wired interface. This is my eth0

shirish@Mugglewille:~$ dmesg | grep RTL
[    5.518281] eth0: RealTek RTL8139 at 0xcc00, 00:08:a1:92:56:33, IRQ 22
[    5.518342] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'

Please advice what I need to look at.

---

### Post by linkxs on 2008-10-07
i don´t use gnome, i use MWM (Motif Window Manager), Ubuntu 8.04.1, so i dont ahve a toolbar, therfore no applet. what i used to do was run network-admin from terminal, and the config would come up,i´d configure it there. now, to run THIS from terminal, it´s NetworkManager. here´s what happened when i tried running it:

> 
linkxs@Toshibuntu:~$ NetworkManager
You must be root to run NetworkManager!
linkxs@Toshibuntu:~$ sudo NetworkManager
linkxs@Toshibuntu:~$


and this is it. no window comes up,nothing. can anyone help?

thanks

---

### Post by codemaster on 2008-10-07
> **linkxs said:**
> i don´t use gnome, i use MWM (Motif Window Manager), Ubuntu 8.04.1, so i dont ahve a toolbar, therfore no applet. what i used to do was run network-admin from terminal, and the config would come up,i´d configure it there. now, to run THIS from terminal, it´s NetworkManager. here´s what happened when i tried running it:



and this is it. no window comes up,nothing. can anyone help?

thanks

I had this problem today, as well. You might want to try reading the following:

[https://bugs.launchpad.net/network-manager/+bug/256054/comments/24](https://bugs.launchpad.net/network-manager/+bug/256054/comments/24)

Basically, in /etc/NetworkManager/nm-system-settings.conf, change managed to true and reboot :)

---

### Post by JGJones on 2008-10-07
> **linkxs said:**
> i don´t use gnome, i use MWM (Motif Window Manager), Ubuntu 8.04.1, so i dont ahve a toolbar, therfore no applet. what i used to do was run network-admin from terminal, and the config would come up,i´d configure it there. now, to run THIS from terminal, it´s NetworkManager. here´s what happened when i tried running it:



and this is it. no window comes up,nothing. can anyone help?

thanks

Running Network-Manager in commandline just start the NM daemon :)

To edit network connections (wired, wireless, VPN, mobile etc) - just use this command:

nm-connection-editor

(there are also others if you use nm-[tab] to show a list)

Hope that helps

---

### Post by linkxs on 2008-10-07
> **codemaster said:**
> I had this problem today, as well. You might want to try reading the following:

[https://bugs.launchpad.net/network-manager/+bug/256054/comments/24](https://bugs.launchpad.net/network-manager/+bug/256054/comments/24)

Basically, in /etc/NetworkManager/nm-system-settings.conf, change managed to true and reboot :)

when i set it to true, after reboot it said that my wifi card is up, but it wasnt. now i set it to false again, it was like it was before. 

then, i tried nm-tools, and it said that nm wasnt running, then i did sudo NetworkManager, it didnt say anything, but when i ran nm-tools again it still said nm wasnt up. why isnt it up?!! :(

---

### Post by asac on 2008-10-13
after a short period of PPA issues new hardy builds should finally be available again. sorry for those hick-ups ;)

---

### Post by Redptc on 2008-10-14
What does that mean?

---

### Post by dannew on 2008-10-17
I just upgraded to Network-manager 0.7, everything works fine except nm-applet is invisible, how do I make it visible again?

---

### Post by apedraza on 2008-10-17
Hi,

PPTP VPN is still not working on NM 0.7. I've traced the problem to the nm-applet not passing on the configured user name.  Instead it passes on the host name. 

I dont know if this is all there is to it. There might be other issues involved besides this one. 

Another bug is that when you modify a vpn connection, nm-applet does not save the changes.

---

### Post by deep75 on 2008-10-17
HI 
I have installed last version from repo but nm-applet doesn't load. If i try in a terminal I obtain 

```
** (nm-applet:31800): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:31800): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

Any suggest?

---

### Post by Crick on 2008-10-18
> **dannew said:**
> I just upgraded to Network-manager 0.7, everything works fine except nm-applet is invisible, how do I make it visible again?
I get this as well. Not sure why. I have tried original nm to get MS pptp vpn working, then changed to wicd + kvpnc (which gave connection hangup issues), and now I'm trying this. Not yet at hair pulling out stage, but getting closer.

---

### Post by apedraza on 2008-10-21
> **Crick said:**
> I get this as well. Not sure why. I have tried original nm to get MS pptp vpn working, then changed to wicd + kvpnc (which gave connection hangup issues), and now I'm trying this. Not yet at hair pulling out stage, but getting closer.

I use kvpnc with great success while waiting on nm 0.7 pptp vpn issues to be fixed. 

Try to use keep alive packets on your connection to keep it going.

---

### Post by Rod Hull on 2008-10-24
> **deep75 said:**
> HI 
I have installed last version from repo but nm-applet doesn't load. If i try in a terminal I obtain 

```
** (nm-applet:31800): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:31800): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

Any suggest?

I get the very same error, but ONLY if I use fast-user-switching and log a second user onto another VT. The first user to logon gets the nm-applet correctly displayed, but the second (and any subsequent user that gets switched in) can't run nm-applet. If you manually start it from a terminal, the error posted above is given.

I've reverted back to the 0.6 version for now. This works perfectly with fast-user switching.

Is there any way to get 0.7 working correctly in a multi-user fast-switching environment?

---

### Post by Crick on 2008-11-01
> **apedraza said:**
> I use kvpnc with great success while waiting on nm 0.7 pptp vpn issues to be fixed. 

Try to use keep alive packets on your connection to keep it going.
I ended up enabling DHCP on my home router as a workaround. I will try your suggestion on my laptop, as that has to have a static IP (configured same as work's, so that there is no config change moving to and from work).

---

### Post by Steve1961 on 2008-11-01
I've finally taken the plunge and upgraded to nm 0.7 for the 3g features.  However, as far as I know there still isn't a workaround for the pptp vpn connection problem.  My vpn connection worked fine with the original network-manager, but I just get a failure to connect error with 0.7.  I was aware of this problem before I installed, but wondered if anyone has managed to get to the bottom of this issue, or come up with a workaround?

For information, I've purged the old vpn configuration data from gconf and reinstalled the new pptp plugin.  I've also tried addding a refuse-eap key in gconf but the vpn service then just refused to start

---

### Post by JGJones on 2008-11-02
PPTP VPN is also something I'm after. In my company, we have mobile workers, all with laptops and using 3G mobile broadband to keep in touch with the home office. They all use Microsoft VPN.

So Network Manager with its fantastic support for 3G is a godsend, but the lack of PPTP VPN is a major problem and is the only reason I still have a Windows partition on my laptop.

---

### Post by ShirishAg75 on 2008-11-02
Is there a forum thread to discuss NM issues in Intrepid somewhere which I don't know about?

---

### Post by Steve1961 on 2008-11-11
This thread seems to have gone a bit quiet.  Anybody heard when we're likley to get the next update on hardy with the refuse-eap option built into the gui

---

### Post by apedraza on 2008-11-11
It seems that there are still problems with pptp.  

There are workarounds for these problems.

1. You need to add a refuse-eap key in gconfig and set it to yes.  If you don't do this, the pptp client will send the host-name instead of your user name to the server. This will cause your connection to be rejected.

2. If you are using a domain name to log in, don't put it in the domain box.  Instead, put your domain name and your user-name together in the name field.  domain\login

3. This is my gconf setup:

gateway xxx.xxx.xxx.xxx -- put in the ip of your server here
lcp-echo-failure 5
lcp-echo-interval 30
mppe-stateful  yes
no-vj-comp yes
refuse-chap yes
refuse-eap yes -- new key you must put in.
refuse-mschap  yes
refuse-pap yes
require-mppe yes
require-mppe-128 yes
service-type org.freedesktop.NetowrkManager.pptp
user  domain\userlogin -- you have to do it like this otherwise it won't work.  on the gui, leave the domain name blank.

And finaly, the keys must be added in system\networking\connections\yourvpnpptpconnection\vpn.

If this does not work for you, then install KVPNC, it is for KDE but it works very well.  I've used it while nm 0.7 pptp was broken. It is not as convenient to use as the nm pptp client but it works.

I have not seen updates to the stock intrepid nm 0.7 components in a while.  I wonder if they are still being worked on.

The refuse-eap key trick was found by somebody else so I don't take credit for it.

Hope this helps....

---

### Post by Steve1961 on 2008-11-12
Thanks for the advice, but none of this seems to work for me.  I can still connect with the old network-manager on another machine though.  kvpnc also crashes often on me, although it does work when it plays nicely.

---

### Post by miatawnt2b on 2008-11-13
I installed the new networkmanager and wpa supplicant from the repos, but I am having trouble with connecting to my network.  I have a pretty simple setup, with no SSID broadcast and a 128bit WEP key.  NetworkManager will not connect no matter what I do if the SSID broadcast is turned off.  As soon as I broadcast the SSID from the router, it works perfectly. 

Another complaint I have is that pkcs12 key functionality has been removed from WPA.  I've extracted my keys, but I NetworkManager still has the connect button greyed out when I point it to the 3 keys.

-J

---

### Post by oygle on 2008-12-11
Somehow the network is not working at all on a Hardy computer. As I would like to get a E169 wireless modem going, can someone please tell me how to install Network Manager 0.7 SVN on Hardy _without_ an internet connection.

That is, what debs would I need ? These can be downloaded from another Ubuntu box and transferred to 'apt cache' (or wherever) on the Hardy computer with no networking.

---

### Post by oygle on 2008-12-11
Reinstalled the network manager on the computer that had network probs, and got the internet (and LAN) connection again.

Do I still use the instructions from the first post in this thread, or do I follow this post ..

> **Darrena said:**
> Alexander Sack the official Network Manager Maintainer for Ubuntu is now publishing packages here:

[https://launchpad.net/~network-manager/+archive](https://launchpad.net/~network-manager/+archive)

Add the following to your /etc/apt/sources.list and **REMOVE** the lines for my PPA:
deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

Do an apt-get update and then use the following command to switch to this version:
```
sudo apt-get install network-manager=0.7~~svn20080628t003601+eni2-0ubuntu0~pre1 libnm-glib0=0.7~~svn20080628t003601+eni2-0ubuntu0~pre1 libnm-util0=0.7~~svn20080628t003601+eni2-0ubuntu0~pre1 network-manager-gnome=0.7~~svn20080626t183232-0ubuntu0~pre1 
```

Once that is done you can do updates as normal to use this version

Also, what files should I backup, just in case I need to go back to the previous version of Network Manager ? I have these files at least:

/etc/ppp/peers/ppp0
/etc/network/interfaces
/etc/mtab
/etc/chatscripts/ppp0

are the above files the only ones that affect the configuration for Network manager ?


Oygle

---

### Post by oygle on 2008-12-11
I followed those instructions from post#1 in this thread, and when I got up to the 'sudo apt-get upgrade' part, it 'kept back' 5 packages ..

> 
:~/Desktop$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libnm-glib0 libnm-util0 network-manager network-manager-gnome wpasupplicant
The following packages will be upgraded:
  ifupdown libdbus-glib-1-2
2 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 125kB of archives.
After this operation, 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ifupdown libdbus-glib-1-2
Install these packages without verification [y/N]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main ifupdown 0.6.8ubuntu12~nm1~hardy1 [56.6kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main libdbus-glib-1-2 0.76-1ubuntu1~nm1~hardy1 [68.0kB]                                     
Fetched 125kB in 52s (2367B/s)                                                                                                   
Preconfiguring packages ...
(Reading database ... 139246 files and directories currently installed.)
Preparing to replace ifupdown 0.6.8ubuntu8 (using .../ifupdown_0.6.8ubuntu12~nm1~hardy1_i386.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace libdbus-glib-1-2 0.74-2 (using .../libdbus-glib-1-2_0.76-1ubuntu1~nm1~hardy1_i386.deb) ...
Unpacking replacement libdbus-glib-1-2 ...
Setting up ifupdown (0.6.8ubuntu12~nm1~hardy1) ...
Installing new version of config file /etc/udev/rules.d/85-ifupdown.rules ...

Setting up libdbus-glib-1-2 (0.76-1ubuntu1~nm1~hardy1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
:~/Desktop$ 


Hmm, now the update manager has 6 updates, 5 of them are the ones just mentioned, and it says ..

> 
You are about to install software that **can't be authenticated**! Doing this may allow a malicious individual to damage or take control of your system.

libnm-glib0 (version 0.6.6-0ubuntu5) will be upgraded to version 0.7~~svn20081018t105859-0ubuntu2~nm2~hardy1
libnm-util0 (version 0.6.6-0ubuntu5) will be upgraded to version 0.7~~svn20081018t105859-0ubuntu2~nm2~hardy1
network-manager (version 0.6.6-0ubuntu5) will be upgraded to version 0.7~~svn20081018t105859-0ubuntu2~nm2~hardy1
network-manager-gnome (version 0.6.6-0ubuntu3) will be upgraded to version 0.7~~svn20081012t133407-0ubuntu1~nm1~hardy1
wpasupplicant (version 0.6.0+0.5.8-0ubuntu2) will be upgraded to version 0.6.4-1~ubuntu1~ppa1~hardy1
libpcsclite1 (version 1.4.99-1ubuntu1) will be installed


Any problems with this ?

Oygle

---

### Post by oygle on 2008-12-11
All this has been installed, but the network manager applet is now missing ?

---

### Post by firebrick on 2009-01-04
I have the same problem as Oygle.
I followed the original update thread and needed to reset policy files to enable download of last 5 files.

Network-Manager is still here and working though icon is lost.

However, the real concern for me is that I'm still with version 0.6.6 not 0.7. Somehow it hasn't updated.

Does anyone know where we go from here to get 0.7?

In my case I'm running Hardy Xubuntu.

---

### Post by labinnsw on 2009-01-04
> **firebrick said:**
> I have the same problem as Oygle.
I followed the original update thread and needed to reset policy files to enable download of last 5 files.

Network-Manager is still here and working though icon is lost.

However, the real concern for me is that I'm still with version 0.6.6 not 0.7. Somehow it hasn't updated.

Does anyone know where we go from here to get 0.7?

In my case I'm running Hardy Xubuntu.

[This is the link to the instructions]("http://ubuntuforums.org/showthread.php?t=797059")

---

### Post by firebrick on 2009-01-04
> **labinnsw said:**
> [This is the link to the instructions]("http://ubuntuforums.org/showthread.php?t=797059")

Run through it again?

I had the identical process results that Oygle listed where the Network-Manager packages were downloaded and upgraded to 0.7

I take it that they are installed already. But from the menu or alt-f2 I can only access version 0.6.6.

I would appreciate advice on what I should do.

---

### Post by dumb_question on 2009-03-12
> **apedraza said:**
> I use kvpnc with great success while waiting on nm 0.7 pptp vpn issues to be fixed. 
[I]
Try to use keep alive packets on your connection to keep it going.

How do you do that? I have the same problem - KVPNC has to reconnect every minute. I can't find a keep-alive option anywhere though (or do you just mean "keep doing something"? I tried continuously pinging google from the terminal, but it croaks after a minute anyway). Any suggestions?

Thanks[/I]

Based on someone else's suggestion I tried turning **off** "Check connection status" in settings under Network / General, and that worked. Apparently if you keep bugging (some?) servers with these checks, they assume you are up to no good, and bounce you.

---

### Post by TerrorBite on 2009-07-07
I had a few issues installing the packages (following the instructions in the first post), however I solved them with the following commands:

I recieved a warning about a missing public key, and unauthenticated packages. This was solved by the following:

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 248DD1EEBC8EBFE8
sudo apt-get update

```

To resolve the issue with the packages being kept back, instead of "apt-get upgrade" I used "apt-get dist-upgrade" which has smarter dependency resolution.

After a reboot, NetworkManager is now able to recognise and use my mobile phone as a modem.

---

