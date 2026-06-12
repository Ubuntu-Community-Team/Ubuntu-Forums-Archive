---
title: "How To: set up wpa_supplicant roaming mode and automatically start at boot"
date: 2009-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Alexis Phoenix on 2009-09-05
I've spent days struggling to do this, so I thought I would share my success.  I now have a laptop which connects seamlessly to a wireless network at boot-time, and has roaming enabled, without needing a gui tool such as kwlan.

**Step 1**
Please read the file /usr/share/doc/wpasupplicant/README.Debian.gz, using the command: ```
zcat /usr/share/doc/wpasupplicant/README.Debian.gz | less
```This will explain in more detail what I am going to show you here.

There are some tutorials around which tell you to insert something like > ```
iface wlan0 inet dhcp
pre-up wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant.conf
``` into your /etc/network/interfaces file.  DON'T DO THIS!  It doesn't seem to work on recent versions of Ubuntu, and wpa_supplicant provides a better way anyhow.
[B]
Step 2[/B]
Open the file /etc/network/interfaces in your favourite text editor.  I'm pasting mine straight in here - eth1 is my wireless interface.```
auto lo eth1
iface lo inet loopback

iface eth1 inet manual
	wpa-driver wext
	wpa-roam /etc/wpa_supplicant.conf

iface default inet dhcp

```The "auto" line means that interfaces lo (loopback) and eth1 (wireless) will be started automatically at boot time.  The "iface" line for eth1 has to contain the "manual" directive for roaming to work - this allows wpa_supplicant to do the task of connecting.  The options starting "wpa-" are passed to wpa_supplicant as if they were on the command line.  See the README for more of these which may be relevant to your setup.  The last line gets your dhcp client started: "default" is the fallback interface when there are no identifiers in the wpa_supplicant.conf network stanza's.  See below for further explanation.

**Step 3**
Edit your /etc/wpa_supplicant.conf file - you have probably already done this - if not, the file /usr/share/doc/wpasupplicant/examples/wpa-roam.conf contains "sane defaults" - you just need to make it personal to your computer.  The Ubuntu supplied wpa_supplicant.conf file probably starts with the lines:```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=netdev
update_config=1

```
The first two lines are synonymous with following the example given in the doccumentation:```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev

```You need to make sure you are a member of the group "netdev" (or some other group you wish to use for this purpose - change the file to match) and add any other users to the same group for whom you want to have roaming enabled.  This enables ordinary users to update the configuration using wpa_cli or wpa_gui.

If these lines are not already there, add them in.

If you have not already done so, add network blocks for the networks you wish associate with.  These will look something like: ```
network={
	ssid="MyNetwork"
	#psk="text passphrase"
	psk=(a huge long number here)
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP
}

```Use wpa_passphrase to generate PSK's and paste them in - this saves the overhead of wpa_supplicant having to do this each time it connects.  Note the use of quote marks if you must use the "bare" passphrase.  See man wpa_supplicant.conf and man wpa_supplicant for further information.
 
_IMPORTANT:_ Set the file's permissions to 600, and ensure it is owned by root, as follows```
sudo chown root.root /etc/wpa_supplicant.conf
sudo chmod 600 /etc/wpa_supplicant.conf
```This will ensure anyone logged into your computer cannot read it and possibly compromise your network.  (Ufortunately it is not proof against an attacker with physical access to your computer).

**Network identifiers**
You can have more fine grained control over how IP addresses are assigned to your computer, by using an identifier in each network stanza in /etc/wpa_supplicant.conf.  These identifiers then correspond to logical interfaces in /etc/network/interfaces.  If an identifier is not given for a network block, the "default" interface is used and relevant commands may be applied to that.  It appears that the default interface is started automatically at boot time so does not need to appear in the "auto" line.  A network identifier takes the form:```
id_str="something"
```.  So the "MyNetwork" block shown above could look like:```
network={
	ssid="MyNetwork"
	#psk="text passphrase"
	psk=(a huge long number here)
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP
	**id_str="home"**
}
```
You can then add stanza's using these identifiers to the /etc/network/interfaces file, where they become the names of logical interfaces.  This one shows dhcp, but it could easily be static or manual:```
iface home inet dhcp
```If you want the network started at boot time, add it to the "auto" line at the top of the file.  See the man page for interfaces for further details.  To keep things simple, try without identifiers first.

---

### Post by tekknokrat on 2011-05-06
Hi, 

if someone has the issue that the interface is not brought up on boot with this setup in combination with a wireless usb interface just add this line in /etc/network/interfaces:

```

auto lo eth1
iface lo inet loopback

iface eth1 inet manual
        **pre-up sh -c "sleep 10"**
	wpa-driver wext
	wpa-roam /etc/wpa_supplicant.conf

iface default inet dhcp

```

This makes the initialization of interface waiting for 10 seconds. I assume some problems with upstart.

@Alexis:
I hope you do not see this as offense, I just need a place to post this oneliner. Just, remove otherwise...

---

