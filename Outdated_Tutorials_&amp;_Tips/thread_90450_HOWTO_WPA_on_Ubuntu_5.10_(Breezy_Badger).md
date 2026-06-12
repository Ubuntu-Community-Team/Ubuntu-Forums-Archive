---
title: "HOWTO: WPA on Ubuntu 5.10 (Breezy Badger)"
date: 2005-11-15
forum: Outdated Tutorials &amp; Tips
---

### Post by b1c1l1 on 2005-11-15
**0. Preface**

First of all, I'd like to thank luca_linux for posting the great [ipw2200+wpa HOWTO]("http://www.ubuntuforums.org/showthread.php?t=26623"), which helped me get my own WPA set up.  However, that HOWTO is a little old (based on an older wpasupplicant and Ubuntu 5.04?) and assumed that one had internet access from the WPA-needing system (how else to apt-get wpasupplicant?).  Also, the newer wpasupplicant package provides its own startup script.  So here is my updated version, most specifically targeted at newer users not as familiar with Linux.

**1. Assumptions**

[LIST]
[*]You have access to a computer setup with internet access that can download a small file (156KB) and transfer it to some portable media (e.g. a floppy disk).
[*]You have successfully installed Ubuntu 5.10 (Breezy Badger) on the system that needs WPA-enabled wireless access.
[*]You have your wireless card driver installed and correctly configured.
[/LIST]

**2. Download wpasupplicant**

On the internet-enabled computer, download wpasupplicant from the Ubuntu repository.  On a Linux machine, it would look like this:

```

wget http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/wpasupplicant_0.4.5-0ubuntu1_i386.deb

```

And then copy it to a floppy drive (or whatever you plan to copy it to):

```

mount /media/floppy
cp wpasupplicant_0.4.5-0ubuntu1_i386.deb /media/floppy
umount /media/floppy

```

**3. Install wpasupplicant**

Now get on your Breezy Badger machine, mount the disk with wpasupplicant, and install it:

```

mount /media/floppy
sudo dpkg -i /media/floppy/wpasupplicant_0.4.5-0ubuntu1_i386.deb

```

**4. Edit wpasupplicant configuration files**

First I would recommend backing up the default configuration files:

```

sudo cp /etc/default/wpasupplicant /etc/default/wpasupplicant_backup
sudo cp /etc/wpa_supplicant.conf /etc/wpa_supplicant.conf_backup

```

Then begin by editing **/etc/default/wpasupplicant**:

```

sudo gedit /etc/default/wpasupplicant

```

Change line 5 to:
```

ENABLED=1

```

and change line 16 to something like:
```

OPTIONS="-D [COLOR="Red"]madwifi[/COLOR] -i [COLOR="Red"]ath0[/COLOR] -c /etc/wpa_supplicant.conf -w"

```

Values in [COLOR="Red"]red[/COLOR] **need to be customized** to match your system.  The first parameter indicates the driver being used, in my example madwifi for my Netgear WG311T, but can be one of: hostap, hermes, madwifi, atmel, wext, ndiswrapper, broadcom, ipw, wired, bsd, and ndis.  If not sure which one to use, consult the wpa_supplicant [README]("http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain").

Now we will edit **/etc/wpa_supplicant.conf**:

```

sudo gedit /etc/wpa_supplicant.conf

```

Comment out the last 4 lines like so:

```

#network={
#        ssid=""
#        key_mgmt=NONE
#}

```

Then we will append the appropriate information to the end of this file from the terminal:

```

wpa_passphrase [COLOR="Red"]your_ssid[/COLOR] | grep -v "#psk" | sudo tee -a /etc/wpa_supplicant.conf

```

Once again, [COLOR="Red"]your_ssid[/COLOR] needs to be customized to match your setup.  This step allows us to store the passphrase in something other than plain text.  The operation will appear to halt: it is waiting for you to enter in your WPA passphrase.  Type it in, and press enter.  Some output will appear: that information has just been added to your configuration file.  Then we will only allow root to read the file:

```

sudo chmod 600 /etc/wpa_supplicant.conf

```

Now we are done editing the configuration files!

**5. Configure wpasupplicant to start when booting**

It is essential that wpasupplicant run **after** your wireless card driver is loaded but **before** Ubuntu attempts to configure it via DHCP or whatever.  Since the scripts in /etc/rcS.d are executed in ascending alphanumeric order, this meant, in the case of my setup, after the hotplug (run level 40) but before networking (also run level 40).  Therefore, I needed the startup script to be alphabetically between "hotplug" and "networking", so I called it "iwpa":

```

cd /etc/rcS.d
sudo ln -s ../init.d/wpasupplicant S40iwpa

```

Now wpasupplicant will startup at the appropriate time each time you have to reboot.

**6. Start wpasupplicant**

Fortunately, we don't have to reboot to enjoy the newly configured WPA.  Just bring up the startup script and restart your networking:

```

sudo invoke-rc.d wpasupplicant start
sudo invoke-rc.d networking restart

```

Enjoy!

---

### Post by Caesar on 2005-11-16
Is there any wpasupplicant package for PPC Macs?

EDIT: it looks like this one should work [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wpasupplicant&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wpasupplicant&searchon=names&subword=1&version=breezy&release=all)

---

### Post by Randy Sparks on 2005-11-25
Thanks! This worked a treat on my system. I use a 3Com OfficeConnect 11g card with ndiswrapper. The encryption on my wifi router is WPA-PSK/TKIP.

---

### Post by punkr0x on 2005-11-26
I attempted to use this howto to set up wpa on my laptop.  It was connecting fine to my router without WPA, but upon setting the router to WPA and installing wpasupplicant using this tutorial, it no longer connects.  It just blinks at me (where before I was getting a solid connection light).

---

### Post by sciurus on 2005-11-27
Any suggestions in how to use wpa in an environment where the laptop will be roaming from network-to-network with different (or nonexistent) wpa keys?

---

### Post by Caesar on 2005-11-27
Any idea about the driver I'm supposed to use with an Apple AirPort card (802.11b not 802.11g AirPort Extreme)?

The card works great with WEP-configured access points... but at home I use a WPA secured network and I still can't use Ubuntu to login on my Wi-Fi network :(

---

### Post by Spider-One on 2005-11-29
Is networking supposed to automatically detect/configure the interface? For some reason I'm not getting an IP. Is there some config file I should edit to tell it to configure wlan0?

FIXED

I had to alter /etc/network/interfaces so everything that had eth0 was replaced with wlan0. I wasnt getting an IP even with that or dhclient, but turns out that was my router, restarted the router and it worked like a charm.

---

### Post by luca_linux on 2005-11-29
Good work.
I've been very busy lately and my HowTos haven't been updated. I'm now downloading Breezy.

---

### Post by paranode on 2005-11-29
Most of it went smoothly until I tried to run the service and it said the hermes driver was not supported.  I have a Dell TrueMobile 1150 which is using the hermes driver and works with WEP.  Do I have to custom-compile this?

---

### Post by ex` on 2005-11-29
Would just like to say that it worked smoothly with the default ipw drivers and WPA-PSK.
Simply restarting the services nor my old fashioned way of /etc/init.d/networking restart didn't bring it to life, though.
But it worked after a restart.

Cheers for this, I couldn't get it to work with the default wpa_supplicant package oddly enough, but this one works great. :)

---

### Post by skyboy on 2005-12-01
Hi, 
It worked like a charm at work where I need to connect with WPA-PSK but when I came back home, nothing worked, and I couldn't connect to my no WEP router anymore without having to kill the wpasupplicant process.
Is there a way to make it detect if it need WPA or not ?? because I travel a lot and sometimes I need WPA and sometimes not.
 
HOW can I remove iwpa from starting at bootup ?? I guess I will start it when I need it. It's easier like that.

EDIT :
OK, I found how to setup several and define one without wpa 
I had to add this after the network{with WPA}
network={
        ssid="ConnectionPoint"
        key_mgmt=NONE
}

EDIT2:
I still have trouble switching from WPA environment to Non-WPA environment :(
any help appreciate
.
EDIT3:
ok, solved. I had to change the order of the network being declared and add priority. Now everything works great. From WPA environment to Non-WPA and vise verca.

---

### Post by pilothaz on 2005-12-03
AMAZING i finally got this to work.  thank you so much for this HOW-TO. 

Thanks again.
-Pilothaz

---

### Post by mapstieks on 2005-12-06
Thank you very much. I was almost giving up on Ubuntu (I love it otherwise), because I could not get WPA to work. Now I am back on air!

---

### Post by valnar on 2005-12-19
It is not working correctly for me.  in Breezy, should we be using wlan0 or eth0?

Robert

---

### Post by cblanquer on 2005-12-19
[QUOTE=Randy Sparks]Thanks! This worked a treat on my system. I use a 3Com OfficeConnect 11g card with ndiswrapper. The encryption on my wifi router is WPA-PSK/TKIP.[/QUOTE]


I have a 3Com Office Connect card [3CRXJK10075] that I could easily configure with ndiswrapper & iwndows drivers on Mandriva 2006. Now I am facing some trouble to get this working on Kubuntu 5.10.
Can you post some additional infos on the way you did configure yours ?
THX
==================================
Solved - I can activate both wired or wireless solutions. I followed the advices from some of the threads in the forum (I shall post the links).
I am missing to setup some parameters to ensure everything is automatic, I still have some manual actions to do to enable the connections.

The important point is the method:
1. ensure the card works
2. ensure the interface works 
3. set up WPE or WPA 

For 2 I have followed the advice of useing network-manager instead of the default tool in Kubuntu, which has helped a lot.

(to be followed...)

---

### Post by coldrick on 2005-12-25
Excellent howto - thanks much.

---

### Post by ex` on 2005-12-26
Slight note for those of you using the Dapper branch or a custom-built kernel higher than or equal to 2.6.13 and the ipw2200 module: you need to specify the "wext" (Kernel wireless extensions) driver instead of the ipw driver.

So your /etc/default/wpasupplicant 16th line will look like:
```

OPTIONS="-D wext -i <interface> -c /etc/wpa_supplicant.conf -w"

```

Perhaps worth including in the first post. :)

---

### Post by Rob2687 on 2005-12-26
what does wext do?
I'm running 2.6.14 and madwifi and it works okay without that.

---

### Post by ex` on 2005-12-26
[QUOTE=Rob2687]what does wext do?
I'm running 2.6.14 and madwifi and it works okay without that.[/QUOTE]
Apologies, it's for the ipw2200 module only as it turns out. I've edited my earlier post. :)

---

### Post by jmcwb on 2005-12-28
Not having too much success.  My card is a Netgear WG511 that of course works just fine when I boot under xp.  It more or less works ok using WEP and the prism54 isl3890 driver.  When I try to use wpa as outlined here I keep getting "No such file or directory" yet /etc/wpa_supplicant.conf certainly exists

root@laptop:/etc/rcS.d# invoke-rc.d  wpasupplicant start
/etc/default/wpasupplicant: line 16: -i eth1 -D prism54 -c /etc/wpa_supplicant.conf: No such file or directory

cat /etc/wpa_supplicant.conf:
root@laptop:/etc# cat /etc/wpa_supplicant.conf
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

# reading passphrase from stdin
network={
	ssid="xxxxxx"
	psk=jibberish-hex-stuff
       	scan_ssid=1
       	proto=WPA
       	key_mgmt=WPA-PSK
}

Can anyone help me with whats missing?

---

### Post by firecat53 on 2005-12-29
For now, try starting wpa_supplicant manually, without using anything in the /etc/default file except the 'enabled=1' line.

```
sudo wpa_supplicant -ieth1 -Dprism54 -c/etc/wpa_supplicant.conf -w -dd 
```

Make sure your interface is actually eth1 and that you're calling the correct driver name according the wpa_supplicant docs (sorry...I use madwifi :)) The -dd will give you the most debugging output while it's running. You can also add a -B once it's working to move it into the background. Mine also works without any of the stuff in /etc/wpa_supplicant.conf before the network={..... line.

Also make sure when you're messing with it that you kill all instances of wpa_supplicant before you start it again. That's tripped me up more than once!!

Good luck!

Scott

---

### Post by jmcwb on 2005-12-29
Scott-

Thanks for your suggestion.  I've tried running with both prism54 and ndiswrapper to no avail.  Someone suggested that 'ap_scan=2' be set since I don't enable SSID Broadcast.  It looks like I'll have to abandon my netgear card when running under ubuntu and only use it when I'm booted into xp.  Someday linux may catch up with the 21st century.

---

### Post by vulturesrow on 2005-12-30
This how-to seemed to work well for me. However, I still cant retrieve webpages without first restarting networking by hand. I am assuming there is some problem with start order of the services but I did this exactly by the howto so I cant figure out how I went wrong? Any ideas, advice, etc would be appreciated.

---

### Post by vulpes76 on 2006-01-03
Hi all, I'm pretty newish to linux and i attempted to setup WPA using this howto and couldn't get it to work. so i decided to go back to WEP, but now i can't get that to work either i uninstalled wpasupplicant and reverted to the backups i made of wpasupplicant and wpasupplicant.conf and removed /etc/rcS.d/S40iwpa however now my wireless card doesn't seem to pickup any signals at all with WEP or no security at all does anyone have any idea how i can fix this?

---

### Post by Rud on 2006-01-03
If you get the following error:

wpa_supplicant: error while loading shared libraries: libssl.so.0.9.8: cannot open shared object file: No such file or directory

Do the following:

sudo ln -s libssl.so.0.9.7 /usr/lib/libssl.so.0.9.8
sudo ln -s libcrypto.so.0.9.7 /usr/lib/libcrypto.so.0.9.8

*This is if you download the wpasupplicant_0.4.7-0ubuntu3_i386.deb version, which you shouldn't because it relies on openssl-0.9.8, which Ubuntu doesn't yet have a package for it. I thought it would be better to use a new version of wpa_supplicant, but it isn't.

---

### Post by vulpes76 on 2006-01-03
Thanks Rud.

No my problem was much simpler i stupidly somehow turned off my wireless:oops:

---

### Post by Gandalf on 2006-01-03
Nice howto!

Though i'd suggest you change the below line
```

sudo ln -s ../init.d/wpasupplicant S40iwpa

```

to

```

sudo update-rc.d wpasupplicant defaults

```

which will automatically add all symlinks to rc*.d according to default profile!!

---

### Post by M8tRiX on 2006-01-04
I am trying to follow the first part of the howto, but i do not have a floopy drive on my Toshiba M300 laptop.

Is their another way around it without using a floopy drive ?

Kind Regards

---

### Post by gosh on 2006-01-04
[QUOTE=M8tRiX]I am trying to follow the first part of the howto, but i do not have a floopy drive on my Toshiba M300 laptop.

Is their another way around it without using a floopy drive ?

Kind Regards[/QUOTE]

Yes, you should be able to download your drivers from the Toshiba-site. Save them in a convenient place (home) and then follow the HowTo.

---

### Post by appdx on 2006-01-05
when i try sudo invoke-rc.d wpasupplicant start I get 
Starting wpa_supplicant: wpa_supplicant v0.4.5
Copyright (c) 2003-2005, Jouni Malinen <jkmaline@cc.hut.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.

This product includes software developed by the OpenSSL Project
for use in the OpenSSL Toolkit ([http://www.openssl.org/](http://www.openssl.org/))

usage:
  wpa_supplicant [-BddehLqqvwW] -i<ifname> -c<config file> [-D<driver>] \
      [-P<pid file>] [-N -i<ifname> -c<conf> [-D<driver>] ...]

drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  prism54 = Prism54.org driver (Intersil Prism GT/Duette/Indigo)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
options:
  -B = run daemon in the background
  -d = increase debugging verbosity (-dd even more)
  -K = include keys (passwords, etc.) in debug output
  -t = include timestamp in debug messages
  -h = show this help text
  -L = show license (GPL and BSD)
  -q = decrease debugging verbosity (-qq even less)
  -v = show version
  -w = wait for interface to be added, if needed
  -W = wait for a control interface monitor before starting
  -N = start describing new interface

No configuration found.
invoke-rc.d: initscript wpasupplicant, action "start" failed.
appdx@ubuntu:~$ sudo update-rc.d wpasupplicant defaults
 System startup links for /etc/init.d/wpasupplicant already exist.
appdx@ubuntu:~$ sudo invoke-rc.d wpasupplicant start
Starting wpa_supplicant: wpa_supplicant v0.4.5
Copyright (c) 2003-2005, Jouni Malinen <jkmaline@cc.hut.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.

This product includes software developed by the OpenSSL Project
for use in the OpenSSL Toolkit ([http://www.openssl.org/](http://www.openssl.org/))

usage:
  wpa_supplicant [-BddehLqqvwW] -i<ifname> -c<config file> [-D<driver>] \
      [-P<pid file>] [-N -i<ifname> -c<conf> [-D<driver>] ...]

drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  prism54 = Prism54.org driver (Intersil Prism GT/Duette/Indigo)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
options:
  -B = run daemon in the background
  -d = increase debugging verbosity (-dd even more)
  -K = include keys (passwords, etc.) in debug output
  -t = include timestamp in debug messages
  -h = show this help text
  -L = show license (GPL and BSD)
  -q = decrease debugging verbosity (-qq even less)
  -v = show version
  -w = wait for interface to be added, if needed
  -W = wait for a control interface monitor before starting
  -N = start describing new interface

No configuration found.
invoke-rc.d: initscript wpasupplicant, action "start" failed.
Anyone help?

---

### Post by Rud on 2006-01-05
[QUOTE=appdx]
No configuration found.
invoke-rc.d: initscript wpasupplicant, action "start" failed.
Anyone help?[/QUOTE]

Show us what your /etc/wpa_supplicant.conf looks like.

Also, I would recommend we add these options to wpa_supplicant.conf in the HOWTO:

scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK

I kept getting kicked off my wireless until I did (I believe it was because of the scan_ssid option).

---

### Post by mog27 on 2006-01-05
I have some questions...

In my wpa_supplicant.conf file, can I use AES or TKIP encryption?  And where would that go?

Also in that same conf file, could I use other forms of WPA such as WPA2?

---

### Post by spier on 2006-01-05
[QUOTE=mog27]I have some questions...

In my wpa_supplicant.conf file, can I use AES or TKIP encryption?  And where would that go?

Also in that same conf file, could I use other forms of WPA such as WPA2?[/QUOTE]

Sure, just build your wpa_supplicant.conf accordingly the example file found  in  

/usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz 

I`m using wpa2 + AES  with this settings:

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="homessid"
        scan_ssid=1
 	proto=RSN
	pairwise=CCMP
	group=CCMP
	key_mgmt=WPA-PSK
	psk=ab12ab12ab12..............f87d4
}

```

---

### Post by PauloStar on 2006-01-26
Thanks SO much! This works perfectly with my DLW-G650+ using ndiswrapper! :p

---

### Post by henshu70 on 2006-02-02
The link to downloading wpasupplicant_0.4.5-0ubuntu1_i386.deb is not working. It would be nice to update it. I found a working link on

[http://debian.yorku.ca/ubuntu/pool/universe/w/wpasupplicant//wpasupplicant_0.4.5-0ubuntu1_i386.deb](http://debian.yorku.ca/ubuntu/pool/universe/w/wpasupplicant//wpasupplicant_0.4.5-0ubuntu1_i386.deb)

---

### Post by PatientZero on 2006-02-03
Following the Howto:

Each time I enter this line in the terminal:

wpa_passphrase (myssid) | grep -v "#psk" | sudo tee -a /etc/wpa_supplicant.conf

I get this:

Passphrase must be 8..63 characters


Any reason why or have I missed a step?  Oh, left out the ssid so the co-worker doesn't freak out.

---

### Post by PatientZero on 2006-02-03
Fixed this little problem.  It seems that it does not like spaces in the ssid.  Of course, I just had to have a space in there.  Removed it and continued on.

---

### Post by STN on 2006-02-04
Thanks for the update on wpa_supplicant. However, madwifi seem to have disappeared from sourceforge.org/net/com and I have no idea where to find driver for SMCWCBT-G-CA that uses Atheros chipset. As far as I know, madwifi supports Atheros chipset cards. So I am assuiming that it will work with my SMC wireless notebook card (if I can find the driver - that is).  

Will my card work with ndiswrapper? If so, I may be able to download and install it. 

Thanks.

---

### Post by PsTJsT on 2006-02-06
A couple of other suggestions:

My adapter (D-Link DWL-G520) and router (D-Link DI-624) do not connect unless I've enabled static DHCP assignment on my router (and set my wireless device to the same settings).  If you're still having problems after following the instructions above, you might want to give this a try.

If your wpa_supplicant.conf file includes "proto=WPA" you should connect via WPA2 if your router either allows it ("WPA2 auto") or requires it ("WPA2 only").  If you want to force the issue, change it to "proto=RSN" or "proto=WPA2."  I understand including the "proto=" line may be optional for some people, but it isn't for me if I want to use WPA2.

---

### Post by imekon on 2006-02-07
I'm not having much luck with my DWL-G650. I know WPA works as I have a PDA that works fine with it, but not ubuntu on my laptop.

My wpa_supplicant.conf file is:

```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
#ap_scan=2
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli

network={
	scan_ssid=1
	ssid="<ESSID>"
	psk=<PSK>
	key_mgmt=WPA-PSK
	proto=WPA
	#proto=WPA2
	pairwise=TKIP
	group=TKIP
}
```

The log I get from running wpa_supplicant manually is as follows:

```

$ wpa_supplicant -d -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf

Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Priority group 0
   id=0 ssid='<ESSID>'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: xx:xx:xx:xx:xx:xx
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=11):
     xx xx xx xx xx xx xx xx xx xx xx                  <ESSID>     
Wireless event: cmd=0x8b1a len=24
Wireless event: cmd=0x8b19 len=12
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
State: SCANNING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=0
wpa_driver_madwifi_set_countermeasures: enabled=0
No keys have been configured - skip key clearing

```

Any ideas why I can't connect to my DI-624 access point?

---

### Post by hackyou on 2006-02-08
Great it works perfect :D
Thanks for this tut;)

---

### Post by Jozz on 2006-02-09
I cannot get this working on my laptop, at school. Normally in Windows you need SecureW2.

SSID = windesheim
Username = [email]studentnumber@windesheim.nl[/email]
Password = mypassword

configuration in Ubuntu now:

wpa_supplicant.conf:
```

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
#network={
#        ssid="windesheim"
#        key_mgmt=NONE
#}


# reading passphrase from stdin
network={
	ssid="windesheim"
	psk=0c5ed147c7221ff85ffb21642fd118c47ac68204ef1d898f2d0129aacb7a95cb
}

```

/etc/default/wpasupplicant:
```

# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>		Wireless drive, typically optional.
#  -i <ifname>		Interface
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-D wext -i eth1 -c /etc/wpa_supplicant.conf -w"

# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"

```

My wireless network card is an Intel® PRO/Wireless 2200BG
I didn't install any extra drivers because Ubuntu recognized the card already.

Does anyone know what I did wrong or what I have to change?

---

### Post by gidkill on 2006-02-10
This isn't working for me. I have Breezy installed on an HP dv1000, fresh. No modifications, other than downloading wpa_supplicant via Synaptic. After starting the wpasupplicant services, and then restarting networking services, I noticed that I wasn't getting a dhcp address. So I started wpa_supplicant manually, and got the following output. Any ideas?

gideon@lucky:/etc$ sudo wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D ipw
ioctl[SIOCSIWPMKSA]: Operation not supported
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:14:bf:30:50:0f (SSID='jafn' freq=0 MHz)
Associated with 00:14:bf:30:50:0f
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
... [ad infinitum]

---

### Post by drakeoutlaw on 2006-02-11
Jozz,

Change "wext" to ipw in /etc/default/wpasupplicant in the options line

---

### Post by mr_crimp on 2006-02-12
Hi, Thanks for this nice howto. But I can't get it to work. I have followed the howto point by point. I'm still pretty new to linux so I don't know where to start debugging. 

If I right-click on the "Network-connection" icon in the Gnome menu and choose "Properties" and then "Configure" the list over my network devices shows that my wireless connection is not configured. But if I click "Properties" and check the "Enable this connection" I get a list over all the networks available so I guess that the network card is working correctly? Is that right? But also the little wireless light on my laptop(just beneath my screen) is turned off.

I don't know if this helps but I have tried to type this in the terminal:
```

~$sudo wpa_supplicant -ieth1 -ipw -c/etc/wpa_supplicant.conf -w -dd
Initializing interface 'pw' conf '/etc/wpa_supplicant.conf' driver 'default'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 13 - start of a new network block
ssid - hexdump_ascii(len=9):
     4d 6f 6e 6b 65 79 4e 65 74                        Home
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 20: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='Home'
Initializing interface (2) 'pw'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'pw' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..
ioctl[SIOCGIFINDEX]: No such device
Waiting for interface..

```

If you need more information or some log files please tell me and I will find it.

My hardware: IBM T42 with Intel PRO2200 b/g Wireless network card.

I hope someone can help me, because I'm pretty lost here. If this problem don't have anything to do with WPA/wpasupplicant but just general configuration of my network card please tell me and then I'm sorry and will ask my question in another forum. 

Thanks...

---

### Post by skitxoz on 2006-02-14
Has anyone gotten this to work with a Hermes driver (orinoco gold card)?

Thanks

---

### Post by Chowbow on 2006-02-14
Wow, thanks for this How-To!!! Worked great. The only thing that was confusing (for this total Linux newb) was the part where you have highlighted in red... "ath0", I was not sure if I put in "wlan0" (which it was), or something else. 

Nevertheless, thanks again. Worked awesome. :)

---

### Post by donaldd on 2006-02-14
I thought I followed the instructions correctly but now cannot see any ipw2200 module, not sure how to correct the following error, appreciate if someone could point me in the right direction.

donald@home:/usr/src/ieee80211-1.1.11$ sudo make install
make -C /lib/modules/2.6.12-10-686/build M=/usr/src/ieee80211-1.1.11 MODVERDIR=/usr/src/ie ee80211-1.1.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  Building modules, stage 2.
  MODPOST
*** Warning: "ieee80211_wx_get_auth" [/usr/src/ieee80211-1.1.11/ieee80211.ko] undefined!
*** Warning: "ieee80211_wx_set_auth" [/usr/src/ieee80211-1.1.11/ieee80211.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
install -d /lib/modules/2.6.12-10-686/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_c cmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.12-10-686/net/ieee80211/
install -d `echo /lib/modules/2.6.12-10-686/include | grep "/net\$" || echo /lib/modules/2 .6.12-10-686/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /li b/modules/2.6.12-10-686/include | grep "/net\$" || echo /lib/modules/2.6.12-10-686/include /net`
mkdir -p /lib/modules/2.6.12-10-686/net/ieee80211//.tmp_versions
install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_cryp t_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.12-10-686/net/ieee80211//.tmp_version s
/sbin/depmod -a 2.6.12-10-686
WARNING: Loop detected: /lib/modules/2.6.12-10-686/net/ieee80211/ieee80211.ko which needs ieee80211.ko again!
WARNING: Module /lib/modules/2.6.12-10-686/net/ieee80211/ieee80211.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200.ko ignored,  due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200/ipw2200.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2100/ipw2100.ko ignored, due to loop

---

### Post by rjeeves33 on 2006-02-14
Wow - Totally Awesome.  I was 'risking it' and using WEP.  I now have an awesome WPA key and feel much better for it \\:D/ 

Thanks for a great How To

p.s I noticed my Wireless wouldn't associate with my AP until I disabled Hidden SSID on the AP.  After enabling SSID broadcast it worked fine.  Awesome

---

### Post by RichardMatley on 2006-02-16
Hi - thanks for this guide, it really helped me set up WPA on my laptop, but I had to experiment a bit to adapt it to use a static IP address, so I thought I'd post what I did in case it is useful to anyone else:

Install wpasupplicant.

Edit /etc/defaults/wpasupplicant:
> 
ENABLED=1
OPTIONS="-w"
OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"


Edit /etc/wpasupplicant.conf, replacing the network section with:

> 
network={
        ssid=<my SSID>
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=<my PSK>
}


Changed permissions and linked into /etc/rcS.d:

> 
chmod 600 /etc/wpasupplicant.conf
cd /etc/rcS.d
ln -s ../init.d/wpasupplicant  S40iwpa


I then used the graphical setup utility to set the IP address:

Main Menu - System Settings - Network Settings
Administrator mode
Select the wireless interface and click configure interface
Selected manual IP, entered the IP, netmask and ESSID but left the WEP box empty.
Selected the routes tab and entered the gateway address
Selected the DNS tab for nameservers

It seemed that the gateway address was not saved properly so I edited /etc/network/interfaces and added to the ath0 section the line:
> 
gateway <my gateway address>


---

### Post by CarlosinFL on 2006-02-18
[QUOTE=b1c1l1]
Then we will append the appropriate information to the end of this file from the terminal:

```

wpa_passphrase [COLOR="Red"]your_ssid[/COLOR] | grep -v "#psk" | sudo tee -a /etc/wpa_supplicant.conf

```

Once again, [COLOR="Red"]your_ssid[/COLOR] needs to be customized to match your setup.  This step allows us to store the passphrase in something other than plain text.  The operation will appear to halt: it is waiting for you to enter in your WPA passphrase.  Type it in, and press enter.  Some output will appear: that information has just been added to your configuration file.  Then we will only allow root to read the file:

```

sudo chmod 600 /etc/wpa_supplicant.conf

```
[/QUOTE]

I don't understand and am stuck on this section. I followed everything fine until the above section I quoted. I edited the string I added to the end of the file and inserted my "ssid" and then don't know what I am suppose to do next. Am I suppose to add something where is says "#psk"?

---

### Post by x1hate1x on 2006-02-18
If there is anyone out there that got this to work with a Dlink DWL-G520 card and could post what their configs are it would be greatly appreciated.  :confused:

---

### Post by hopspitfire on 2006-02-28
very nice :P helped me a bunch

---

### Post by Brian on 2006-02-28
Hi All

Ive have a little problem, at home Ubuntu wireless works fine but at my school they use EAP-MSCHAP v2 and i don't quite know how a can get on it. 
The way we do in windows i by user and pass. 

Ive like to keep my home settings (my settings fore the wireless at home), meaning either a script or some way to control which setting to use. 

thx in advance 

Brian

---

### Post by PsTJsT on 2006-02-28
[QUOTE=x1hate1x]If there is anyone out there that got this to work with a Dlink DWL-G520 card and could post what their configs are it would be greatly appreciated.[/QUOTE]

I have a D-Link DWL-G520 (Atheros chipset) connecting to a D-Link DI-624 via WPA2...

Here are the non-commented lines of my wpa_supplicant.conf file:
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
	ssid="PsTJsT_Network"
	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
	psk=3cb3 ... 6fe0
}

And here are the non-commented lines of my wpasupplicant file:
ENABLED=1
OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf -w"

Obviously the device (in my case, ath0) and the driver (in my case, madwifi) need to reflect the specific setup/system as described in the how-to at the begining of this thread.

Also, FWIW, my adapter and router do not connect unless I've enabled static DHCP assignment on my router (and set my wireless device to the same settings), so perhaps you might want to try using a static IP address if that's an option.

Let me know if you want/need to see the complete text (including the commented lines that I've omitted) of the config files.

---

### Post by Pedric on 2006-03-02
My ipw2200 comes up deactivated after reboot (I'm on dapper drake right now), and so I wrote a little script to enforce WPA and activate the wlan interface (this assumes that wpa_supplicant is up and running):

```
#make sure eth1 is down
ifconfig eth1 down

#select the network with id=$1 (see wpa_cli list_networks)
wpa_cli select_network $1

#force reassociation with the wireless adapter
wpa_cli reassociate eth1

#bring up eth1
ifconfig eth1 up

#set eth1 to connect to the corresponding ssid (ssid of the network with id=$i, obtained from wpa_cli)
#(stripping " from the output of wpa_cli)
iwconfig eth1 essid `wpa_cli -i eth1 get_network $1 ssid|sed -es/\"//g`

#(optional) run DHCP client to get an IP adress/gateway/dns configuration
dhclient eth1
```
(replace eth1 with your wireless interface)

save this as /usr/local/bin/wlan_wpanet
and chmod +x /usr/local/bin/wlan_wpanet

If you have e.g. two entrys in /etc/wpa_supplicant.conf, such as:

```
network={
        ssid="UNIVERSITY"     
        psk=bab....yourpresharedkeyhere....cc6
}
network={
        ssid="HOME"
        psk=19298a7....yourpresharedkeyhere....37f4
}
```

and 

sudo wpa_cli list_networks

shows:

```
Selected interface 'eth1'
network id / ssid / bssid
0       UNIVERSITY        any     
1       HOME   any     
```

then you can connect with
sudo wlan_wpanet 0
or
sudo wlan_wpanet 1

this may be a little complicated but it works...

---

### Post by sal on 2006-03-06
[QUOTE=b1c1l1]**0. Preface**

First of all, I'd like to thank luca_linux for posting the great [ipw2200+wpa HOWTO]("http://www.ubuntuforums.org/showthread.php?t=26623"), which helped me get my own WPA set up.  However, that HOWTO is a little old (based on an older wpasupplicant and Ubuntu 5.04?) and assumed that one had internet access from the WPA-needing system (how else to apt-get wpasupplicant?).  Also, the newer wpasupplicant package provides its own startup script.  So here is my updated version, most specifically targeted at newer users not as familiar with Linux.

**1. Assumptions**

[LIST]
[*]You have access to a computer setup with internet access that can download a small file (156KB) and transfer it to some portable media (e.g. a floppy disk).
[*]You have successfully installed Ubuntu 5.10 (Breezy Badger) on the system that needs WPA-enabled wireless access.
[*]You have your wireless card driver installed and correctly configured.
[/LIST]

**2. Download wpasupplicant**

On the internet-enabled computer, download wpasupplicant from the Ubuntu repository.  On a Linux machine, it would look like this:

```

wget http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/wpasupplicant_0.4.5-0ubuntu1_i386.deb

```

And then copy it to a floppy drive (or whatever you plan to copy it to):

```

mount /media/floppy
cp wpasupplicant_0.4.5-0ubuntu1_i386.deb /media/floppy
umount /media/floppy

```

**3. Install wpasupplicant**

Now get on your Breezy Badger machine, mount the disk with wpasupplicant, and install it:

```

mount /media/floppy
sudo dpkg -i /media/floppy/wpasupplicant_0.4.5-0ubuntu1_i386.deb

```

**4. Edit wpasupplicant configuration files**

First I would recommend backing up the default configuration files:

```

sudo cp /etc/default/wpasupplicant /etc/default/wpasupplicant_backup
sudo cp /etc/wpa_supplicant.conf /etc/wpa_supplicant.conf_backup

```

Then begin by editing **/etc/default/wpasupplicant**:

```

sudo gedit /etc/default/wpasupplicant

```

Change line 5 to:
```

ENABLED=1

```

and change line 16 to something like:
```

OPTIONS="-D [COLOR="Red"]madwifi[/COLOR] -i [COLOR="Red"]ath0[/COLOR] -c /etc/wpa_supplicant.conf -w"

```

Values in [COLOR="Red"]red[/COLOR] **need to be customized** to match your system.  The first parameter indicates the driver being used, in my example madwifi for my Netgear WG311T, but can be one of: hostap, hermes, madwifi, atmel, wext, ndiswrapper, broadcom, ipw, wired, bsd, and ndis.  If not sure which one to use, consult the wpa_supplicant [README]("http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain").

Now we will edit **/etc/wpa_supplicant.conf**:

```

sudo gedit /etc/wpa_supplicant.conf

```

Comment out the last 4 lines like so:

```

#network={
#        ssid=""
#        key_mgmt=NONE
#}

```

Then we will append the appropriate information to the end of this file from the terminal:

```

wpa_passphrase [COLOR="Red"]your_ssid[/COLOR] | grep -v "#psk" | sudo tee -a /etc/wpa_supplicant.conf

```

Once again, [COLOR="Red"]your_ssid[/COLOR] needs to be customized to match your setup.  This step allows us to store the passphrase in something other than plain text.  The operation will appear to halt: it is waiting for you to enter in your WPA passphrase.  Type it in, and press enter.  Some output will appear: that information has just been added to your configuration file.  Then we will only allow root to read the file:

```

sudo chmod 600 /etc/wpa_supplicant.conf

```

Now we are done editing the configuration files!

**5. Configure wpasupplicant to start when booting**

It is essential that wpasupplicant run **after** your wireless card driver is loaded but **before** Ubuntu attempts to configure it via DHCP or whatever.  Since the scripts in /etc/rcS.d are executed in ascending alphanumeric order, this meant, in the case of my setup, after the hotplug (run level 40) but before networking (also run level 40).  Therefore, I needed the startup script to be alphabetically between "hotplug" and "networking", so I called it "iwpa":

```

cd /etc/rcS.d
sudo ln -s ../init.d/wpasupplicant S40iwpa

```

Now wpasupplicant will startup at the appropriate time each time you have to reboot.

**6. Start wpasupplicant**

Fortunately, we don't have to reboot to enjoy the newly configured WPA.  Just bring up the startup script and restart your networking:

```

sudo invoke-rc.d wpasupplicant start
sudo invoke-rc.d networking restart

```

Enjoy![/QUOTE]

im ussing an emachine m6810 with broadcom (ndiswrapper),
when the computer comes up do i have to do an sudo dhclient wlan0 to bring up the network? because it wont come up on its own?

---

### Post by seiser on 2006-03-09
Hi guys, could anyone of you set up WPA with the Netgear WG511 (V1!).
I tried to follow the guide carefully, but when it comes to entering the key I'm not sure if I'm doing this right. 

my key is in ASCII and 63 charakters wide. I learnt that if I enter an ASCII key I need to use psk="\adsswe43adfa**?=`"§ .... ".
then I get an error msg that the key is 65 charakers wide and that's invalid
(see [this post ]("http://ubuntuforums.org/showthread.php?t=141180")for detailed error msg and a description of what I was doing)

if I enter it without quotation marks I get errors too (probably because no ASCII charakters are expected, just HEX). 

I think I'm very close to set it up, but cant get any further! thanks a million for your comittment. >>seb

---

### Post by seiser on 2006-03-09
right, I tried a little further and fixed the problem with the **Key**.

my wpa_supplicant.conf looks like that now: 

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1
network={
	ssid="WG"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
psk=7b3.....e4351e4
}

```
it allows me to continue the howto, creating the link and trying to start WPA supplicant
```

seb@ubuntu-seb:/etc/rcS.d$ sudo invoke-rc.d wpasupplicant start
Starting wpa_supplicant: done. 

``` looking good!
even 
```

seb@ubuntu-seb:/etc/rcS.d$ sudo invoke-rc.d networking restart
 * Reconfiguring network interfaces...                                   [ ok ]

```
looks good, but(!) according to the howto I should be able to connect to my AP. actually it doesent!

I'm using WEP encryption right now, that's why I shut down the interface with ifdown
```
There is already a pid file /var/run/dhclient.eth1.pid with pid 10806
killed old client process, removed PID file
....

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:09:5b:45:df:68
Sending on   LPF/eth1/00:09:5b:45:df:68
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.178.1 port 67

``` gives some strange messages, but maybe just warnings. if I ifup again, it connects to the WEP accesspoint SSID "WG2" not to the WPA AP SSID "WG". so I'm trying to *invoke-rc.d networking restart* again (like above) (it returns ok, again) but no way, it's still connected to "WG2". 

I redo ifdown and reconfiguring "Networking" (using the Sytem -> Administration) and delete all WEP settings (but I dont disable the connection). I'm restarting my Notebook and iwconfig tells me 

```

eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ifup and ifdown dont work. I retry

```

seb@ubuntu-seb:/etc/rcS.d$ sudo invoke-rc.d wpasupplicant stop
Stopping wpa_supplicant: done.
seb@ubuntu-seb:/etc/rcS.d$ sudo invoke-rc.d wpasupplicant start
Starting wpa_supplicant: done.
seb@ubuntu-seb:/etc/rcS.d$ sudo invoke-rc.d networking restart
 * Reconfiguring network interfaces...                                   [ ok ]

```
but that dosent change the output of iwconfig!

I hope somebody knows how to help out. Maybe there is a better way to erradicate my old WEP settings?!

I also tried this, knowing it wouldnt work - but maybe it indicates some fault:
```

seb@ubuntu-seb:/etc/rcS.d$ sudo dhclient eth1
...

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:09:5b:45:df:68
Sending on   LPF/eth1/00:09:5b:45:df:68
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.178.21
PING 192.168.178.1 (192.168.178.1) 56(84) bytes of data.

--- 192.168.178.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


```

please note, I originally started [this thread]("http://ubuntuforums.org/showthread.php?t=141180") (further information about my problem)

I think I have to erase all the original (WEP) settings, does anyone know how to do that? any ideas? 

thanks guys...

---

### Post by Enkido on 2006-03-11
Thank you soooo much for this!

After 2.5 months, and just over 55 formats....my ipw2200 with WPA is now working!! (Despite having half my hair fall out, this problem has helped me understand Linux much better)

At last, I can free up more disk space by removing M$ XP (WiFi was my only problem)...

My laptop is a Sony Vaio VGN-A215M. Just in case someone else has the same machine + problem :mrgreen:

---

### Post by kditty on 2006-03-12
i am using a dlink dwl 520+ card, im just wondering if anyone got this working for this specific card? this part confused me, i wasnt sure what to use in place of madwifi...

and change line 16 to something like:
Code:

OPTIONS="-D madwifi -i ath0 -c /etc/wpa_supplicant.conf -w"


Values in red need to be customized to match your system. The first parameter indicates the driver being used, in my example madwifi for my Netgear WG311T, but can be one of: hostap, hermes, madwifi, atmel, wext, ndiswrapper, broadcom, ipw, wired, bsd, and ndis. If not sure which one to use, consult the wpa_supplicant README.

---

### Post by Enkido on 2006-03-12
kditty..

The dlink 520+ uses the TI ACX100/ACX111 chipset. You can try this site:

[http://acx100.sourceforge.net/wiki/Main_Page](http://acx100.sourceforge.net/wiki/Main_Page)

---

### Post by kditty on 2006-03-12
[QUOTE=Enkido]kditty..

The dlink 520+ uses the TI ACX100/ACX111 chipset. You can try this site:

[http://acx100.sourceforge.net/wiki/Main_Page](http://acx100.sourceforge.net/wiki/Main_Page)[/QUOTE]

enkido, thanks for the link, its a good starting point. but i dont see anything on there about WEP and it also doesnt list ubuntu as supporting my driver. maybe ill check around the site and see if i recognize anything even though i really dont know what im looking for ;)

---

### Post by kditty on 2006-03-12
just a FYI for anyone reading this. i am online through my dlink dwl 520+ right now, i just cant get the WEP or WPA to work, im not sure which value to change 'madwifi' to in the original posters instructions. i dont know if its ndiswrapper or what, im affraid to experiment because i might lose my connection altogether. any help is appriciated.

---

### Post by Enkido on 2006-03-12
[QUOTE=kditty]just a FYI for anyone reading this. i am online through my dlink dwl 520+ right now, i just cant get the WEP or WPA to work, im not sure which value to change 'madwifi' to in the original posters instructions. i dont know if its ndiswrapper or what, im affraid to experiment because i might lose my connection altogether. any help is appriciated.[/QUOTE]


Right. I was a bit confused as to how you were able to establish a connection using the "madwifi" driver on a ACX100 chipset :confused: So after some reading, i've found out that d-link use a diffrent chipset for almost every new revision of the same model :-k 

"madwifi" is a driver for cards using the Atheros chipset. As your NIC is working, then it may well be that your d-link card revision is based on an Atheros chipset - so  i would suggest that you don't change the madwifi bit..

What settings do you have in your  /etc/wpa_supplicant.conf ?

---

### Post by kditty on 2006-03-13
[QUOTE=Enkido]Right. I was a bit confused as to how you were able to establish a connection using the "madwifi" driver on a ACX100 chipset :confused: So after some reading, i've found out that d-link use a diffrent chipset for almost every new revision of the same model :-k 

"madwifi" is a driver for cards using the Atheros chipset. As your NIC is working, then it may well be that your d-link card revision is based on an Atheros chipset - so  i would suggest that you don't change the madwifi bit..

What settings do you have in your  /etc/wpa_supplicant.conf ?[/QUOTE]
that file you mentioned comes up blank from sudo gedit etc/wpa_supplicant.conf im not sure what settings i have...should i open it a different way?

---

### Post by Enkido on 2006-03-13
[QUOTE=kditty]that file you mentioned comes up blank from sudo gedit etc/wpa_supplicant.conf im not sure what settings i have...should i open it a different way?[/QUOTE]

You need to do:  sudo gedit /etc/wpa_supplicant.conf

This is one way of editing the file. If it comes up blank again, make sure you have the wpa_supplicant installed: 

sudo apt-get install wpasupplicant

If it's already there you will get: "wpasupplicant is already the newest version". If not, it will be installed. You will then be able to edit the wpa_supplicant.conf file using the aforementioned method - the file should already contain some example settings...

---

### Post by kditty on 2006-03-13
after following this tutorial, i can not connect on my breezy install. im on live cd right now... i dont know if i messed something up or what, i also installed the recommended updates so im not sure if it was this tutorial that messed up my settings, or the update. 

what would be the process to get rid of this and just go back to my unencrypted network? this was too advanced for me and i knew i shouldnt have tried it but against ym better judgement i tried anyway and now im screwed :X 

if i cant undo this process, or if this process isnt the problem, is there a way that i can just restore ubuntu breezy without a full install? id hate to lose all my settings but id also hate never being able to connect to the internet.

---

### Post by Enkido on 2006-03-13
[QUOTE=kditty]after following this tutorial, i can not connect on my breezy install. im on live cd right now... i dont know if i messed something up or what, i also installed the recommended updates so im not sure if it was this tutorial that messed up my settings, or the update. 

what would be the process to get rid of this and just go back to my unencrypted network? this was too advanced for me and i knew i shouldnt have tried it but against ym better judgement i tried anyway and now im screwed :X 

if i cant undo this process, or if this process isnt the problem, is there a way that i can just restore ubuntu breezy without a full install? id hate to lose all my settings but id also hate never being able to connect to the internet.[/QUOTE]

Oh no :-k 

Did this happen after you installed the wpasupplicant or have you changed something else? 

What message is it giving you?

---

### Post by kditty on 2006-03-13
[QUOTE=Enkido]Oh no :-k 

Did this happen after you installed the wpasupplicant or have you changed something else? 

What message is it giving you?[/QUOTE]

well i installed the wpasupplicant, and never restarted or loaded it, because the other computer was busy and i couldnt go to encrypt the network, nor do it from here becausei  would get kicked off. so i never actually applied the settings that i made. then i updated with ubuntu recommended updates, and i was online for about 14 hours befor i rebooted. 

once i rebooted my computer, the network fails to pick up. it never connected automaticaly in the first place, i had to change the channle and the mode to managed but then it would pick up my network and i could connect fine, and that was more than on with me. but now that i rebooted and the wpasupplicant took effect, my wireless is shot, i cant connect no matter what, and no matter what i change i cant reconfigure to connect. 

there is no message that it gives me, it just gets stuck at enabling network. and i cant get online at all except for the live cd.

i would hate to have to reinstall ubuntu from scratch and reconfigre everything and redownload everything but if i cant uninstall/reverse the changes that i made through this tutorial, then i will have to do that. how do i go about uninstalling this and stopping it from loading when my computer starts?

---

### Post by Enkido on 2006-03-13
[QUOTE=kditty]well i installed the wpasupplicant, and never restarted or loaded it, because the other computer was busy and i couldnt go to encrypt the network, nor do it from here becausei  would get kicked off. so i never actually applied the settings that i made. then i updated with ubuntu recommended updates, and i was online for about 14 hours befor i rebooted. 

once i rebooted my computer, the network fails to pick up. it never connected automaticaly in the first place, i had to change the channle and the mode to managed but then it would pick up my network and i could connect fine, and that was more than on with me. but now that i rebooted and the wpasupplicant took effect, my wireless is shot, i cant connect no matter what, and no matter what i change i cant reconfigure to connect. 

there is no message that it gives me, it just gets stuck at enabling network. and i cant get online at all except for the live cd.

i would hate to have to reinstall ubuntu from scratch and reconfigre everything and redownload everything but if i cant uninstall/reverse the changes that i made through this tutorial, then i will have to do that. how do i go about uninstalling this and stopping it from loading when my computer starts?[/QUOTE]

If you think it's the wpasupplicant thats causing this (I doubt that it is), then you could remove it using:

sudo apt-get remove wpasupplicant

One thing you got realize when you are using Linux as a new user, is that you may have to reinstall from scratch many many times, before you get a perfect system. You really must no be afraid to try different things - this will help you understand your system better.

You could always have M$ XP running as a backup system on a another partition, while you try and get your Linux settings right. It is tempting to use WiFi with no encryption enabled to save time setting it all up, but realize that you are putting your privacy at risk here. 

Good luck :)

---

### Post by kditty on 2006-03-13
[QUOTE=Enkido]If you think it's the wpasupplicant thats causing this (I doubt that it is), then you could remove it using:

sudo apt-get remove wpasupplicant

One thing you got realize when you are using Linux as a new user, is that you may have to reinstall from scratch many many times, before you get a perfect system. You really must no be afraid to try different things - this will help you understand your system better.

You could always have M$ XP running as a backup system on a another partition, while you try and get your Linux settings right. It is tempting to use WiFi with no encryption enabled to save time setting it all up, but realize that you are putting your privacy at risk here. 

Good luck :)[/QUOTE]

im not sharing any folders or anything, just the internet connection. i need access on this computer, so until something easier comes along i have to stay unencrypted. ive never really looked into how unsecure it is, what are the downfalls? im not sharing any files or anything just a straight connection, if someone wants to leech my bandwidth thats fine with me but what kind of privacy am i putting at risk?

---

### Post by Enkido on 2006-03-14
[QUOTE=kditty]im not sharing any folders or anything, just the internet connection. i need access on this computer, so until something easier comes along i have to stay unencrypted. ive never really looked into how unsecure it is, what are the downfalls? im not sharing any files or anything just a straight connection, if someone wants to leech my bandwidth thats fine with me but what kind of privacy am i putting at risk?[/QUOTE]

Well, using tools such as airsnort and ethereal anyone with some basic knowledge could observe some of your surfing habits, read what you are posting, intercept your e-mail, etc...

However, what worries me most is the fact that a wardriver could use the connection for illegal activity, while the culprit remains anonymous the activity will be traced back to the subscriber. Just think of people using the Internet to send out Spam, viruses, share copyrighted material and whats worse upload illegal content...all this activity will be traced back to you, and you will have a difficult time proving it was not you :cry: 

WEP is now hackable, but WPA is still very difficult. Last year in a ISSA (Information Systems Security Association) meeting in Los Angeles, a team of FBI agents demonstrated current WEP-cracking techniques and broke a 128 bit WEP key in about three minutes!

Read more about it here:

[http://www.compliancepipeline.com/160502612](http://www.compliancepipeline.com/160502612)

---

### Post by GoodPanos on 2006-03-14
> Hi, 
 It worked like a charm at work where I need to connect with WPA-PSK but when I came back home, nothing worked, and I couldn't connect to my no WEP router anymore without having to kill the wpasupplicant process.
 Is there a way to make it detect if it need WPA or not ?? because I travel a lot and sometimes I need WPA and sometimes not.
 
 HOW can I remove iwpa from starting at bootup ?? I guess I will start it when I need it. It's easier like that.
 
 EDIT :
 OK, I found how to setup several and define one without wpa 
 I had to add this after the network{with WPA}
 network={
 ssid="ConnectionPoint"
 key_mgmt=NONE
 }
 
 EDIT2:
 I still have trouble switching from WPA environment to Non-WPA environment 
 any help appreciate
 .
 EDIT3:
 ok, solved. I had to change the order of the network being declared and add priority. Now everything works great. From WPA environment to Non-WPA and vise verca.

Can you please post detail instructions on how you accomplished this.  Or if any one else knows that would be great.  Basically I want to be able to connect to multiple wifi spots with WPA or without and so forth.

---

### Post by king.knut on 2006-03-15
Thanks b1c1l1 for your superb HOW-TO. I just installed WPA support on Dapper Flight 4 (Live-CD) using Copy and Paste. It worked perfectly. I use a D-Link DWL-G520 card with Atheros 5212 Chipset running madwifi. The encryption on my wifi router is WPA-PSK/TKIP.

For Dapper I had to download wpasupplicant_0.4.7-0ubuntu4_i386.deb form  [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/)  and in addition libqt3-mt_3.3.5-1ubuntu18_i386.deb  from  [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/)

I suppose it's a good idea always to go to these repositories and download the latest versions. Or, if one's got modem connection, install via Adept or Synaptic  (enable the Universe repository first).

Only one problem occured. At first KWifiManager didn't show the Local IP. And of course I couldn't go online. I found a workaround, that seems to me a little inconvenient. I started Wifi-Radar, configured the network once more and started the network again using Wifi-Radar. Then everything worked fine.

Has anybody got an idea how to get the Local IP via DHCP without using Wifi-Radar?

Would I get it without problems after reboot just following your HOW-TO? Can't test this, 'cause I set it up running a Live-system.

---

### Post by slavik on 2006-03-16
hey buddy, I'm in the same boat as you (wpa uni network) ...
does the securew2 instructions for your uni network say to use eap-pap?

---

### Post by TrinitronX on 2006-03-18
I just finished a new Dapper install (Flight CD 5), after a failed attempt to upgrade my breezy install (I had heavily modified it, so some rather bad mesa video driver issues popped up, resulting in an 'abandon ship' operation :P).

Anyways... this process worked fine, although the wpa supplicant package was already installed, I am using a D-Link g520 (atheros chip) with the preinstalled madwifi drivers in Dapper.  I merely followed steps 4 through 6, using my already premade config file (salvaged from breezy).

I always wondered why sometimes my wireless would go out in breezy... step 5 explains it.

Thanks!
\\:D/

---

### Post by forkmantis on 2006-03-18
Brilliant howto.  Thanks.  I got wpa working on my buntu box in one afternoon.

Here's the fun part.  Prior to switching to wpa, I had a samba share so that my wife and I could store music and such on this box's 250GB HD.  I also occasionally ssh into this machine from my laptop.  Once I installed and configured wpa_supplicant, I am no longer able to ssh into this machine, access the samba share, or even ping it from inside my house.  Ironically, I can ssh in from remote locations.  

I'm still new-ish to both linux and network administration, so I'm not really sure how to diagnose this issue.  I've googled things like "wpa_supplicant ssh server" etc, but have not really found anything useful.  I don't mind reading and learning, but at this point I sure could use a point in the right direction.

[EDIT 4/2/2006]
I was finally able to resolve the problem.  I had been using wpa_supplicant version 0.4.5 that I'd installed w/ apt-get.  I noticed that version 0.4.8 had been released, so I DLed the source, compiled, and installed it.  Now my laptops can connect to my PC just fine.

---

### Post by scottylans on 2006-03-24
Hi guys!


I just made this post here
[http://ubuntuforums.org/showpost.php?p=857088&postcount=620](http://ubuntuforums.org/showpost.php?p=857088&postcount=620)

Not knowing this thread exists.


Sorry to hassle you all :( - but I'm wondering if someone out there has the time and patience to re-write the 5.04 / 5.10 2 HOW-TO's into a single simple one.

Bear in mind, when I used to setup ipw2200 I used to just fresh install Ubuntu on my laptop from scratch, follow the guide and it worked :(

Anyone care to comment?  - sorry to be demanding, you can always say no!  it's just a suggestion so people don't need to read a 60 page thread plus another 8 :(

---

### Post by AgeOfDawn on 2006-03-24
[QUOTE=rjeeves33]Wow - Totally Awesome.  I was 'risking it' and using WEP.  I now have an awesome WPA key and feel much better for it \\:D/ 

Thanks for a great How To

p.s I noticed my Wireless wouldn't associate with my AP until I disabled Hidden SSID on the AP.  After enabling SSID broadcast it worked fine.  Awesome[/QUOTE]

I was having some problems getting this to work with my intel ipw2200 but all problems went away as soon as I turned off Hidden SSID on my AP.

---

### Post by tharsan on 2006-03-25
I'd like to thank you for this HOW TO, it really got me setup.

I now run my IBM Thinkpad T40 between school (using a 128-bit WEP encryption scheme) and home (using WPA-PSK) seamlessly. As soon as I start Ubuntu, it determines which network is available and connects, it's actually even easier than my setup in Windows!

Thank you very much!

---

### Post by scottylans on 2006-03-31
[QUOTE=scottylans]Hi guys!


I just made this post here
[http://ubuntuforums.org/showpost.php?p=857088&postcount=620](http://ubuntuforums.org/showpost.php?p=857088&postcount=620)

Not knowing this thread exists.


Sorry to hassle you all :( - but I'm wondering if someone out there has the time and patience to re-write the 5.04 / 5.10 2 HOW-TO's into a single simple one.

Bear in mind, when I used to setup ipw2200 I used to just fresh install Ubuntu on my laptop from scratch, follow the guide and it worked :(

Anyone care to comment?  - sorry to be demanding, you can always say no!  it's just a suggestion so people don't need to read a 60 page thread plus another 8 :([/QUOTE]


Sorry to hassle chaps, but any comments?

---

### Post by scottylans on 2006-04-10
Anyone at all? Think we should have a nice straightforward 5.10 howto? from install - > running? including WPA?

:(

---

### Post by X1NN on 2006-04-11
I'm not sure what I'm doing wrong, connections dialog says I'm sending and recieveing packets. But the browser is not getting on. Any suggestions would be greatly appreciated.

---

### Post by PvSinNL on 2006-04-13
Thanks a lot for this HOWTO! It worked like a charm on my system (Acer Aspire 2012WLMi notebook with Intel Centrino 2200BG adapter, Linksys WRT54G router).

---

### Post by x5452 on 2006-04-23
I did not find this how to first and tried the old one for Horay, so can someone tell me a way to "wipe clean" anything relevant from my failed attempts before? So that I can start over with this how to, or does it matter? can i just start this how to from beginning and it will 'replace' stuff i did before??

---

### Post by cthornhill on 2006-04-23
YES! for goodness sake we need current code as well...I know Dapper is close, but lots of us need the best WPA support possible under 5.10 NOW. We also deserve a decent howto that works. Ihave been ranting about this for a month. How are we supposed to convince people they are safe in Ubuntu if we don't fix things that are this basic - and I mean a fix that does not include hacking the latest non-release code!

---

### Post by x5452 on 2006-04-23
are you saying yes to me, there is a way, or yes as in concurring with my statement????  :-)  im still lost...

---

### Post by orko on 2006-04-23
I do not know which driver option i should use (ndis, wext..) because i use rt2500. Can anyone help me out??

---

### Post by Monolith on 2006-04-25
[QUOTE=PvSinNL]Thanks a lot for this HOWTO! It worked like a charm on my system (Acer Aspire 2012WLMi notebook with Intel Centrino 2200BG adapter, Linksys WRT54G router).[/QUOTE]

Same here with a paradigit 9154 laptop and Centrino 2200BG! (Thomson speedtouch modem/router)

Thanks for the howto!

---

### Post by Zeno Cosini on 2006-08-24
Thanks for the How To - unfortunately, I have not been able to get WPA working. I am using a Thinkpad T43 with Intel PRO/Wireless 2200BG under Ubuntu 5.10. I have followed Luca's How To ([http://www.ubuntuforums.org/showthread.php?t=26623&highlight=WPasupplicant)](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=WPasupplicant)), as well as the How To in this thread. I installed the latest stable version of all modules,

ipw2200 driver: 1.1.0
firmware: 2.4
ieee80211 stack: 1.1.12.

Although Wireles Extensions v 17 should be enough ([http://ipw2200.sourceforge.net/)](http://ipw2200.sourceforge.net/)), 

```

modprobe ipw2200
iwconfig 

```

shows the warning 

Warning: Driver for device eth1 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

My /etc/wpa_supplicant.conf is as follows:

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="XXX"
        scan_ssid=1
        proto=RSN
        pairwise=CCMP
        group=CCMP
        key_mgmt=WPA-PSK
        psk=7b..ef
}

```

(where XXX is of course the real ssid, and psk is the full hex passcode).

Based on the b1c1l1's How To, I also changed /etc/default/wpasupplicant:

```

# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>          Wireless drive, typically optional.
#  -i <ifname>          Interface
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-D ipw -i wlan0 -c /etc/wpa_supplicant.conf -w"

# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"

```

(I don't know why this file is not mentioned in Luca's How To.) Should I have used eth1 instead of wlan0?

Trying to configure wpa_supplicant with 

sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd

results in the following output:

```

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 20 - start of a new network block
ssid - hexdump_ascii(len=3):
     65 63 6f                                          XXX
scan_ssid=1 (0x1)
proto: 0x2
pairwise: 0x10
group: 0x10
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='XXX'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: zz:zz:zz:zz:zz:zz
wpa_driver_ipw_set_wpa: enabled=1
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_ipw_set_countermeasures: enabled=0
wpa_driver_ipw_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
Daemonize..

```

(Again, instead of XXX, there is my real ssid, instead of the zz's, there is the real MAC address.)

The problems seem to start with 
ioctl[SIOCSIWPMKSA]: Operation not supported

Any ideas would be greatly appreciated.

---

