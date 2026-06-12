---
title: "HOWTO: Automated WPA Encryption with ndiswrapper drivers"
date: 2005-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by notzac on 2005-05-03
Pre-amble:

I've been bashing at this for the last few hours as I just got myself a shiny new wireless router and wanted to use WPA-PSK rather than WEP. I don't pretend to be any sort of guru at this; I spent most of my time reading FAQs and Wiki entries; swore at my computer for a while when it didn't work and then just started experimenting. I've finally got what appears to be a fairly nice configuration that works great for me - I'm writing it up in the hopes that it helps someone else.

Assumptions:

[list][*]You can already access the network/internet -without- WPA or other encryption.
[*]You're using an ndiswrapper-based driver (probably not essential, but you'll have to modify a few of the commands if you're using madwifi or one of the native drivers - YMMV).
[*]Your wireless card comes up with an interface name of 'wlan0' (if not, you'll need to modify my examples to suit).
[*]You want to use WPA-PSK with either TKIP or AES/CCMP.
[*]Your router (or whatever) provides IP address details via DHCP (not essential, but you'll have to modify one of the files beyond my examples).
[*]Your router or WAP broadcasts its' SSID. Sorry, haven't worked out how to make this work with broadcasting switched off yet. :/
[*]You're working with an installation of Ubuntu Hoary.
[*]You're comfortable editing files and working with badly-written HOWTOs. :)[/list]

OK, here we go..

You should already have your wireless working -without- WPA encryption. If you don't, the rest of this probably won't help you.

First up, you'll need the wpasupplicant package. It's in the Universe repository, so you'll need to have that in your sources.list file. If you've already installed this package, I recommend that you reinstall; use these commands to get rid of it:

[INDENT][FONT=Courier New]sudo killall wpasupplicant
sudo dpkg --purge wpasupplicant[/FONT][/INDENT]

Now install a fresh copy:

[INDENT][FONT=Courier New]sudo apt-get install wpasupplicant[/FONT][/INDENT]

After you've got it installed, start by modifying the "default" file -- I'm not sure why to be honest, but the installer told me to start there and I did:

[INDENT][FONT=Courier New]sudo vi /etc/default/wpasupplicant[/FONT][/INDENT]

Here's what mine looks like; modify yours to taste:

```
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>          Wireless Driver
#  -i <ifname>          Interface (required, unless specified in config)
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

# OPTIONS="-w"
```

Save and exit.

Next, you'll need to sort your pre-shared key out. My router allows me to input the passphrase that makes up the key itself; I originally tried putting this passphrase in as the wireless key, which failed to work altogether for fairly obvious reasons. Hindsight is wonderful like that. Take the passphrase that you used in your router or WAP and use wpa_passphrase to generate the key. You use this command in the following format:

[INDENT][FONT=Courier New]wpa_passphrase <ssid> <passphrase>[/FONT][/INDENT]

So the command I ran looks something like this:

[INDENT][FONT=Courier New]wpa_passphrase MyHomeWireless SuperSecretPassphrase[/FONT][/INDENT]

..which gives you an output something like:

```
network={
        ssid="MyHomeWireless"
        #psk="SuperSecretPassphrase"
        psk=e42ac2538ef03f906d37332a0df4446150e04cdcdd392e309486075065a70a1f
}
```

Copy all that - we'll need in a moment. You now need to put that in to a configuration file for wpa_supplicant, which you first need to create. Given that you'll have the keys to your wireless access in this file, a little extra precaution is in order. Use the following commands to create and then open the file for editing:

[INDENT][FONT=Courier New]sudo touch /etc/wpa_supplicant.conf
sudo chmod 600 /etc/wpa_supplicant.conf
sudo vi /etc/wpa_supplicant.conf[/FONT][/INDENT]

Using the output of wpa_passphrase we copied earlier as a base, you'll need to tell wpa_supplicant a few more details about your network. Here's what my copy of this file looks like when complete, with the sample data:

```
network={
        ssid="MyHomeWireless"
        #psk="SuperSecretPassphrase"
        psk=e42ac2538ef03f906d37332a0df4446150e04cdcdd392e309486075065a70a1f
        key_mgmt=WPA-PSK
        proto=WPA
}
```

Save and exit.

You should probably test this now - here's a good command to copy/paste to your cli (this will only work if you fulfill the assumptions of this HOWTO):

[INDENT][FONT=Courier New]sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && dhclient wlan0[/FONT][/INDENT]

If that doesn't get you to the point where you can ping other hosts on your network, something is most likely wrong with wpa_supplicant (I'm assuming that it hasn't got anything to do with DHCP). Run these two commands:

[INDENT][FONT=Courier New]sudo dhclient -r wlan0 && ifconfig wlan0 down && killall wpa_supplicant
sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd[/FONT][/INDENT]

This will give you a bunch of debugging output, and someone who is much more skilled than I might be able to help you out. Sorry, but this HOWTO isn't going to help you much more, as it's beyond my ken completely.

If you got lucky and you -are- able to ping hosts on your network, now is the time to automate it. It's actually really easy. Run this command first to bring the wireless link down cleanly:

[INDENT][FONT=Courier New]sudo dhclient -r wlan0 && ifconfig wlan0 down && killall wpa_supplicant[/FONT][/INDENT]

You need to tell your network interface configuration file how to deal with the wireless config nicely; here's what you need to put in for your wireless card (again, if you don't completely fulfill the assumptions of this HOWTO, you'll need to change a few things). Open up /etc/network/interfaces:

[INDENT][FONT=Courier New]sudo vi /etc/network/interfaces[/FONT][/INDENT]

..here's the part you'll need to add/modify in yours for the wireless:

```
auto wlan0
iface wlan0 inet dhcp
pre-up /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Save and exit.

We're all done! Wireless will now come up on boot (assuming that your computer already detects the card and loads the drivers for it already), and you can start/stop the wireless link with the following two commands:

[INDENT][FONT=Courier New]sudo ifup wlan0
sudo ifdown wlan0[/FONT][/INDENT]

--

I hope this has helped someone. If you've got questions I'll try to help; please bear in mind that I've only got a rough idea of how this works, so my answers might be vague and not particularly useful. ;)

---

### Post by vnbuddy2002 on 2005-05-03
Sorry dude. I have only two words for you. "Excellent Guide". I will trash my current "WEP" (Worst Entrance Protector).

---

### Post by thread on 2005-05-07
Hrm... it doesn't quite work for me. I've tried lots of stuff, but here's my wpa_supplicant output:

```
$ wpa_supplicant -ieth0 -c /etc/wpa_supplicant.conf -d ndiswrapper -c /etc/wpa_supplicant.conf
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'default'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Priority group 0
   id=0 ssid='Bell'
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:12:f0:01:aa:da
wpa_driver_hostap_set_wpa: enabled=1
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_countermeasures: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 180 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:09:5b:49:43:e3 ssid='Bell' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Signal 2 received - terminating
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_hostap_set_wpa: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=0
wpa_driver_hostap_set_countermeasures: enabled=0

```

What's this skip - no WPA/RSN IE mean?? My thread is here

[http://ubuntuforums.org/showthread.php?p=161762](http://ubuntuforums.org/showthread.php?p=161762)

---

### Post by kperkins on 2005-05-09
[QUOTE=thread]Hrm... it doesn't quite work for me. I've tried lots of stuff, but here's my wpa_supplicant output:

```
$ wpa_supplicant -ieth0 -c /etc/wpa_supplicant.conf -d ndiswrapper -c /etc/wpa_supplicant.conf
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'default'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Priority group 0
   id=0 ssid='Bell'
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:12:f0:01:aa:da
wpa_driver_hostap_set_wpa: enabled=1
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_countermeasures: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 180 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:09:5b:49:43:e3 ssid='Bell' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Signal 2 received - terminating
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_hostap_set_wpa: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=0
wpa_driver_hostap_set_countermeasures: enabled=0

```

What's this skip - no WPA/RSN IE mean?? My thread is here

[http://ubuntuforums.org/showthread.php?p=161762](http://ubuntuforums.org/showthread.php?p=161762)[/QUOTE]
I think that RSN authentication only works with WPA/IEEE 802.11i wireless.  Is your router set up using that, and your wireless card not? Or vice versa?  Or do you have wpasupplicant set up to use that and neither your card or router can?  From the stuff you showed it looks like your router can't handle it ("No suitable AP found")--although that could just be you not being able to access it, because of wpasupplicant problems. Hope this helps some.

---

### Post by mq001k on 2005-05-31
Hey great guide, but note that if your wireless is already configured to run WEP you must comment out the lines in /etc/network/interfaces pertaining to that configuration.  It didn't take too long to figure out, but it did throw me for a little loop.

---

### Post by Crumps on 2005-06-01
Ok, I did some looking around and I found out how to make WPA work with broadcast disabled. It's just a matter of adding two lines. Here is an example:

```
ap_scan=2
network={
scan_ssid=1
ssid="My SSID"
psk="SooperSekretPassphrase"
key_mgmt=WPA-PSK
proto=WPA
}
```

The "ap_scan" line tells your machine to let the driver (ndiswrapper) do the scanning instead of wpa_supplicant. The "scan_ssid" line tells it to send SSID specifc broadcast requests. Only adding both those lines to my config file let me connect to my AP while broadcast was disabled. I hope this helps some people out.

---

### Post by az on 2005-06-01
I have copied this to the forum-wiki delta

[http://test.wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA](http://test.wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA)

Perhaps someone could complete it by adding the latest comments...

---

### Post by seezar on 2005-06-12
I've followed everthing but cant figure out why I'm getting the following when I try to activate it:

$ sudo ifconfig eth1 up && /usr/sbin/wpa_supplicant
bash: /usr/sbin/wpa_supplicant: No such file or directory


UPDATE:
well I know now why i get that error, for some reason I'm unable to install wpasupplicant:

$ sudo apt-get install wpasupplicant
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  wpasupplicant
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 138kB of archives.
After unpacking 385kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe wpasupplicant 0.3.8-1 [138kB]
Fetched 138kB in 0s (153kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/wpasupplicant_0.3.8-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/wpasupplicant_0.3.8-1_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


UPDATE #2:
Well finally got it installed and now get the following:

$  sudo ifconfig eth1 up && /usr/sbin/wpa_supplicant
Failed to read configuration file '/etc/wpa_supplicant.conf'.

---

### Post by hw-tph on 2005-06-14
[QUOTE=seezar]Well finally got it installed and now get the following:

$  sudo ifconfig eth1 up && /usr/sbin/wpa_supplicant
Failed to read configuration file '/etc/wpa_supplicant.conf'.[/QUOTE]

Did you create /etc/wpa_supplicant.conf? notzac described it in his original post. For reference, here is mine, with keys removed:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
	ssid="hoganas"
	psk=LotsAndLotsOfCharactersGeneratedByWpa_Passphrase
	key_mgmt=WPA-PSK
	proto=WPA
}
```


Håkan

---

### Post by Mikings on 2005-06-17
Very useful guide: has anyone found a .deb package for wpasupplicant that works with Warty?

---

### Post by mrfilgueira on 2005-06-18
[QUOTE=thread]Hrm... it doesn't quite work for me. I've tried lots of stuff, but here's my wpa_supplicant output:

[code]$ wpa_supplicant -ieth0 -c /etc/wpa_supplicant.conf -d ndiswrapper -c /etc/wpa_supplicant.conf
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
i

Hi !

Better late than never...

It should be -D ndiswrapper. Thus wpa_supplicant's script is using PRISM2 driver. Good luck !!   :smile:

---

### Post by TheCat on 2005-06-21
Thank you thank you thank you!  I'm using Fedora Core 4 with a Linksys WMP54G and this helped a LOT.

---

### Post by bugmenot on 2005-06-24
[QUOTE=notzac]sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd[/QUOTE]

wpa_supplicant will not run as root and thus cannot read the configuration file.  The first shell that sees this line will split it at "&&".

Perhaps something like this would be more appropriate:

sudo sh -c 'ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd'

---

### Post by mjbanks on 2005-06-27
I'm rather noob-ish, so please excuse me if I'm doing something stupid here  :???: 

I installed the driver for my wireless card (linksys wpc54gs) on my toshiba satellite laptop. I installed and setup wpa-supplicant the way described in this thread. I edited wpasupplicant.conf properly. 

I then go to run this:
```

sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && dhclient wlan0
```

and I get some crazy error messages...

```
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:12:17:3d:c8:49
Sending on   LPF/wlan0/00:12:17:3d:c8:49
Sending on   Socket/fallback
SIOCSIFFLAGS: Permission denied
mjbanks@ubuntu:~$ sudo gedit /etc/wpa_supplicant.conf mjbanks@ubuntu:~$ sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
sit0: unknown hardware address type 776
Open a socket for LPF: Operation not permitted
```


Anybody have any ideas what's going wrong? I'm really liking ubuntu so far, and just wish I could get this wireless up and running.

Thanks!  :)

---

### Post by oFooBaro on 2005-06-29
```

sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && dhclient wlan0
```

You must start dhclient with 'sudo rights'.

Change the command to:
```

sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && **sudo** dhclient wlan0
```

---

### Post by mjbanks on 2005-06-29
Thanks I'll try that tonight when I get home from work and see how it goes

---

### Post by mjbanks on 2005-06-29
I tried that, it runs some DHCP finder or something on port 67 (sorry, don't have the code with me at work), but just times out. I can post that code later.

Also, I've posted more information in another thread (didn't want to keep adding to this howto)...

[http://ubuntuforums.org/showthread.php?p=233181#post233181](http://ubuntuforums.org/showthread.php?p=233181#post233181)

Any help would be terrific  :)

---

### Post by DeMi on 2005-07-14
Yes indeed a really nice article.

The only thing is, when i have both network cable and Wlan card in my system:

/etc/init.d/networking restart ---> goes fine

I can also see that both interfaces (eth0 and wlan0) in ifconfig are properly configured. 

But, i cant ping any host in my network, no networking activity is posible.

If i unplug one of them, either the Wlan card or the eth and i run /etc/init.d/networking restart, my internet works again!

Does anyone have a clue?

---

### Post by graabein on 2005-07-15
How does this work with my other computers? 

I'm trying to secure my father's wireless network and the host is a Windows XP and my machine is of course a Ubuntu Linux. I need to be able to hook up a couple laptops from time to time.

When I bring up the wireless network on the XP laptops do I then input the passphrase or do I have to run it through a keygen (wpa_passphrase)?

Another thing -- SSID is the name of the wireless network?

---

### Post by spacemonkey on 2005-07-25
I've got the same problem as mjbanks.  When I run the command it runs a dhcp finder type thing but eventually times out.  My wireless works fine without WPA, so I don't know what the problem is.

---

### Post by Anthem on 2005-08-28
Sorry to bump after so long, but I'm really stuck.

I'm relatively new at this, but I've been slogging through and finally making progress.

I got the wireless driver installed.
I connected to my wireless access point.
I turned on WPA and successfully browsed with WPA on.

But when I restarted my computer, I was unable to do anything (including ping the router).  I plugged in ethernet, logged into the router, and turned of WPA, but I still can't ping it.  iwlist shows the SSID and the whole nine yards, so I don't know what the problem is.  Here's my network file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid dogrun
pre-up /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Any hints?  I was pretty excited once I got it working, so it's jarring to have lost it again.

---

### Post by pjbgravely on 2005-09-13
I had the same problem I believe, After the reboot test, the card came up but I could not see the DNS. In System/Administration/Network, when I disabled eth0 it started working great. After a reboot it refused to work again I disabled eth0 and stopped and started the wifi card. I probably need to disable eth0 in the start up scripts. Maybe that will fix it.

***update*** I fixed it by un configuring eth0 in the GUI ***

I also found that it wouldn't work when I had quotes in the WPA key.

Paul

---

### Post by anselmograciani on 2006-03-04
Excellent, excellent , excellent guide!!!!!
Thank you, thank you, thank you, thank you!!!!. 

Thank you again.


Saludos.
Anselmo.

---

### Post by chrismacp on 2006-03-26
Thank a lot for the instructions. Got my belkin USB and Linksys WRT54G working in a fairly respectible time. I'm very new to linux so am VERY pleased to have managed to get this to work.

CHEERS

---

### Post by sionghua on 2006-10-30
I got everything setup and running ok, except that it is not automated even though I included the wpa_supplicant command in /etc/network/interfaces so everytime I start my computer I need to run wpa_supplicant manually and then dhclient manually as well in order to access to internet. Any idea why automation is not working? 

my interfaces file as follow:
> 
auto wlan0
iface wlan0 inet dhcp
wireless-mode Managed
wireless-essid bplus1
pre-up wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -Bw
post-down killall -q wpa_supplicant


By the way I notice that I need to completely shut down my computer before I login to ubuntu again to make sure the usb adapter refresh, if I simply restart it will not be detected.

---

### Post by lowracer on 2007-09-08
I'm using wicd, but can't get the WPA or even WEP to work, using ndiswrapper around a broadcom chipset.  Do I need to do all this or has the wicd install already done it for me? 

I started to do these steps and discovered that I already have the latest wpasupplicant running.

One interesting clue is that the psk in my existing .conf file was set to the passphrase in quotes, not the key.  Still after changing that, I'm unable to connect with WPA.

---

### Post by proghead on 2007-09-08
> **notzac said:**
> Pre-amble:
I hope this has helped someone. If you've got questions I'll try to help; please bear in mind that I've only got a rough idea of how this works, so my answers might be vague and not particularly useful. ;)

I just wanted to say that i used this to the tee on Feisty 7.04 and it worked flawlessly!:popcorn:

---

### Post by Phlogiston on 2007-09-27
ok this guide is cool, but why is dhclient started immediately when I do ifup? I mean in the case the wpa_supplicant takes longer to do the authentification, then the whole thing fails. 

Any way to control that? So that dhclient is run after wpa_supplicant suceeded?

---

