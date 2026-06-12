---
title: "HOW TO: Zydas ZD1211 wireless with WPA"
date: 2005-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by shof2k on 2005-11-19
HOW TO: Zydas ZD1211 wireless with automatic WPA

[Edit] I've included the versions of the packages used and cleared the text up.  [/Edit]

_Aim_
I hope this helps you set up a WPA encrypted wireless network when using a ZD1211 based   wireless card, such as Safecom SWLU-5400 dongle.
Thanks to ubuntu user dom for pointing me in the right direction :)

_User level_
Intermediate.  This isn't meant to be a simple list of commands to type in to a terminal because networking has too many options for any one script to cover.  You may need to tweak some of the commands or files to your own system settings. 

_Pre-requisites_
You have a 2.6.12-9 kernel.  If you managed to get this working on another kernel type, then post your details. 
You can navigate around the file system using the terminal
Can copy / move files using the terminal
Can untar packages
Can follow bad how to's :smile: 

_How To Part 1 - preparation _
You will need the ZD1211 kernel module and wpa supplicant.  Unfortunately, the versions supplied by ubuntu don't work, so we have to remove them first.  Using synaptic or using a terminal and typing:
```
sudo modprobe -r zd1211
```
```
sudo apt-get remove wpasupplicant
```

The following may not be essential, but it's worth doing to ensure better success with other programs.
```

        sudo apt-get install linux-tree
	sudo apt-get update
	sudo apt-get install build-essential
	sudo apt-get install kernel-package
	sudo apt-get install gcc
	sudo apt-get install libncurses5
	sudo apt-get install libncurses5-dev
	sudo apt-get install libqt3-mt-dev
	sudo apt-get install wireless-tools
```

Unpack the linux source and create a standard symbolic link
```

        cd /usr/src
	sudo tar --bzip2 -xvf linux-2.6.12.tar.bz2
	sudo ln -s /usr/src/linux-2.6.12 /usr/src/linux 
```

Create standard symbolic link for the linux headers.
	```
sudo ln -s /usr/src/linux-headers-2.6....  /usr/src/linux-headers
```


Download the source to openssl from [http://www.openssl.org/source/]("http://www.openssl.org/source/") and unpackage it /usr/src/openssl. I've used version 0.96m.

Download the latest zd1211 driver source from [http://zd1211.ath.cx/download]("http://zd1211.ath.cx/download") and unpackage it to /usr/src/zd1211src. I used version r38.

If you're having difficulty compiling these, there is an alternative source archive from  [http://www.zydas.com.tw/downloads/download-1211.asp]("http://www.zydas.com.tw/downloads/download-1211.asp").  I've never got these to work, but it might help you.

Download the latest wpa supplicant source from 
[http://hostap.epitest.fi/wpa_supplicant]("http://hostap.epitest.fi/wpa_supplicant")
I used version 0.39.

Unpackage it to /usr/src/wpasupplicant.  Inside the source folder, create a symbolic link called openssl pointing to  /usr/src/openssl/include.
```

   sudo ln -s /usr/src/openssl/include /usr/src/wpasupplicant/openssl
```


Go into the zd1211 source type
```
 sudo gedit Makefile 
```
Make sure that the lines
KERN_26=y
KERNEL_SOURCE=/usr/src/linux
are present.  If not comment out the current values and replace with the above.

Compile the zd1211 module.
```

        sudo make
	sudo make install 
```

Copy the resulting zd1211.ko to /lib/modules/...../net

Install the module
```
sudo modprobe -v zd1211
```

Attatch the dongle, dmesg should show the following
```

[4294699.485000]  _____     ____    _    ____
[4294699.485000] |__  /   _|  _ \  / \  / ___|
[4294699.485000]   / / | | | | | |/ _ \ \___ \
[4294699.485000]  / /| |_| | |_| / ___ \ ___) |
[4294699.485000] /____\__, |____/_/   \_\____/
[4294699.485000]      |___/
[4294699.485000] zd1211 - version 2.0.0.0 
```

Note the version number and format may change.  What you don't want are any sort of error messages as this indicates something is wrong.


_How To Part 2 - Connecting to an open network _

If your access point is unencrypted, you should now be able to connect to it.  You can use the iwconfig wireless tools to specify your accessid etc. If you're having problems connecting, try the following articles:
[http://www.ubuntuforums.org/showthread.php?t=92142]("http://www.ubuntuforums.org/showthread.php?t=92142")
[http://www.ubuntuforums.org/showthread.php?t=86389]("http://www.ubuntuforums.org/showthread.php?t=86389")

To see if your module is active type the following 
```
 ifconfig
``` will give a list of all network connections.
```
 iwconfig 
``` will give a similar list for all wireless connections.  You should see something like this:
```

wlan0     802.11b/g NIC  ESSID:"youressid"
          Mode:Managed  Frequency=2.462 GHz  Access Point: your-access-point
          Bit Rate:54 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=80/92  Signal level=30/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11601  Invalid misc:0   Missed beacon:0

```
```
 iwlist scanning 
``` will search out the wireless networks available. If you can see your network here then the module is working.

_How To Part 3 - Connecting to an encrypted network _

I don't recommend using a wireless network without some sort of encryption.  If you want WEP encryption, use the gnome networking tool (system-administration-networking) and specify a WEP key.

If you want WPA encryption (stronger than WEP), then compile wpa supplicant.
```

        sudo cp /usr/src/wpasupplicant
	sudo make
```

Set up /etc/wpa_supplicant.conf, changing the values in italics
```

network={
        ssid="*network id*"
        scan_ssid=1
        pairwise=TKIP
        psk="*encryption key*"
        key_mgmt=WPA-PSK
        proto=WPA
} 
```

Connect your dongle and type the following to activate the wireless network
```
sudo ifconfig eth0 down
```to shut down your ethernet connection 
```
sudo ifconfig wlan0 up
```to start your wireless connection
```
cd /usr/src/wpasupplicant
	sudo ./wpa_supplicant -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas
```

After a few moments, use ifconfig to see if you have connected to your access point.  If not, check dmesg and the system logs for error messages.

Once you're happy that you can use the connection, the final step is to automate the process.  Backup and edit /etc/network/interfaces and add the following code

```

pre-up /usr/src/wpasupplicant/wpa_supplicant -Bw -i wlan0 -c/etc/wpa_supplicant.conf -D zydas

post-down killall -q wpa_supplicant 
```

To restart your network:
```
 sudo /etc/init.d/networking restart 
```

and hopefully wpa should now be working..........

Hope this helps :)

---

### Post by horobi on 2005-12-03
hi, i followed your instructions but whe i try to compile the module i get this:

horobi@nx9010:/usr/src/zd1211src/zd1211-driver-r39$ sudo make
/lib/modules/2.6.12-10-386/build
/usr/src/zd1211src/zd1211-driver-r39
-I/usr/src/zd1211src/zd1211-driver-r39/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/usr/src/zd1211src/zd1211-driver-r39 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
horobi@nx9010:/usr/src/zd1211src/zd1211-driver-r39$

can you help? thanx in advance

---

### Post by shof2k on 2005-12-04
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory. Stop

Did you follow the prerequisites and download the stuff at the top?
Since it's complaining about not finding this folder, see if you can get to it.  Can you also tell me which kernel you are using.  
Thanks,

---

### Post by horobi on 2005-12-06
i followed the prerequisites and downloaded all the stuff...

i'm trying to start again from scratch... my kernel is 2.6.12-10-386

the lib/modules/2.6.12-10-386 is not where it should be....

thanx

---

### Post by shof2k on 2005-12-06
mmm i'm afraid I don't know why that folder hasn't been created.  You could try creating it and then copying the module into there.

Let me know how you get on, this is my first HOW TO and I'd like to know that I've helped someone :)

---

### Post by horobi on 2005-12-10
mmmmh i dunno if it's so simple... i mean if during the compiling of the module u  need folders or source libraries they have to be in certain locations.... maybe u downloaded source kernel before making this HOWTO or stuff like that....

---

### Post by tuza on 2005-12-10
Hi

I followed this guide, and it worked allmost...

When I execute the code:

 ./wpa_supplicant -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas

It takes my wlan0 down, for some reason. I checked dmesg output and it tells the following:

wlan0: no IPv6 routers present

Do you have any suggestions/tip?

---

### Post by shof2k on 2005-12-10
You need to disable IPv6 from your ubuntu set up.  This won't cause you any serious problems as the world is still running on IPv4.

1) Go to System-Administration-Networking and delete anything that mentions IPv6.
2) Open a terminal and type "sudo gedit /etc/network/interfaces" and put a # sign in front of any line that mentions ipv6.
3) Follow this link [http://ubuntuforums.org/archive/index.php/t-87798.html](http://ubuntuforums.org/archive/index.php/t-87798.html) to get a speed boost in firefox.

Hope that helps,

---

### Post by bandan on 2005-12-13
Hi,
I've followed your HOW TO and successfully compiled the zd1211 driver for my Yakumo QuickWlan. With WEP it's working. 
But I can't make wpa_supplicant. I've downloaded openssl and made a symbolic link with that line:

*ln -s /usr/src/openssl-0.9.8a/include/ /usr/src/lnx_wpa_supplicant_1_2_0_0/*

but when i try to make the supplicant I'm getting the following:
```

root@BruceLee:/usr/src/lnx_wpa_supplicant_1_2_0_0# make
cc -MMD -O2 -Wall -g -I../driver/modules -I../utils -I../zdsta/src  -DCONFIG_DRIVER_WEXT -DCONFIG_DRIVER_ZYDAS -DEAP_TLS -DEAP_PEAP -DEAP_MD5 -DEAP_MSCHAPv2 -DIEEE8021X_EAPOL -DEAP_TLS_FUNCS -DCONFIG_WIRELESS_EXTENSION   -c -o config.o config.c
In Datei, eingefügt von config.c:23:
sha1.h:6:25: Fehler: openssl/sha.h: Datei oder Verzeichnis nicht gefunden
In Datei, eingefügt von config.c:26:
eap.h:5:25: Fehler: openssl/ssl.h: Datei oder Verzeichnis nicht gefunden
eap.h:6:25: Fehler: openssl/err.h: Datei oder Verzeichnis nicht gefunden
In file included from config.c:26:
eap.h:107: Fehler: syntax error before »SSL_CTX«
eap.h:107: Warnung: kein Semikolon am Ende von »struct« oder »union«
config.c: In Funktion »wpa_config_parse_string«:
config.c:92: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »hexstr2bin« unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_ssid«:
config.c:105: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_psk«:
config.c:171: Warnung: Zeigerziele bei Übergabe des Arguments 3 von »wpa_hexdump_ascii« unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_eap«:
config.c:480: Warnung: Zeigerziele bei Übergabe des Arguments 3 von »wpa_hexdump« unterscheiden sich im Vorzeichenbesitz
config.c:481: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_identity«:
config.c:490: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_anonymous_identity«:
config.c:507: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_password«:
config.c:523: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_ca_cert«:
config.c:540: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_client_cert«:
config.c:556: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_private_key«:
config.c:572: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_private_key_passwd«:
config.c:588: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_ca_cert2«:
config.c:605: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_client_cert2«:
config.c:621: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_private_key2«:
config.c:637: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_parse_private_key2_passwd«:
config.c:653: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeichenbesitz
config.c: In Funktion »wpa_config_read_network«:
config.c:930: Warnung: Zeigerziele bei Übergabe des Arguments 2 von »pbkdf2_sha1« unterscheiden sich im Vorzeichenbesitz
make: *** [config.o] Fehler 1
root@BruceLee:/usr/src/lnx_wpa_supplicant_1_2_0_0#

```

Does anyone know why make doesn't find those files?
thx bandan

---

### Post by shof2k on 2005-12-14
Hi

My German is rusty but you appear to be missing files ssl.h and err.h.  Navigate to /usr/src/wpa..../openssl and see if the files exist as it may be your archive or link is corrupt.

Hope that helps

---

### Post by mrmailer on 2005-12-20
this is what i just posted to hostap list.  i have fedora core 4.  Also, do you have to set the essid before using wpa_supplicant, or is it set, or what?  do you run dhclient wlan0 after?


Sheesh, why is it so hard to get this working with WPA?  It works fine
without.  I followed the instructions as per this page.
[http://ubuntuforums.org/archive/index.php/t-92327.html](http://ubuntuforums.org/archive/index.php/t-92327.html)
on my fedora core 4 machine

here is my /etc/wpa_supplicant.conf.  Now I set the essid manually,
then issue the command
wpa_supplicant -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas
And then I ran dhclient wlan0, but it never gets the IP.  Then the
keyboard, but not the mouse, stopped working.  help?

##### Example wpa_supplicant configuration file ###############################
# Empty lines and lines starting with # are ignored

# NOTE! This file may contain password information and should probably be made
# readable only by root user on multiuser systems.

# global configuration (shared by all network blocks)
#
# Interface for separate control program. If this is specified, wpa_supplicant
# will create this directory and a UNIX domain socket for listening to requests
# from external programs (CLI/GUI, etc.) for status information and
# configuration. The socket file will be named based on the interface name, so
# multiple wpa_supplicant processes can be run at the same time if more than
# one interface is used.
# /var/run/wpa_supplicant is the recommended directory for sockets and by
# default, wpa_cli will use it when trying to connect with wpa_supplicant.
ctrl_interface=/var/run/wpa_supplicant

# Access control for the control interface can be configured by setting the
# directory to allow only members of a group to use sockets. This way, it is
# possible to run wpa_supplicant as root (since it needs to change network
# configuration and open raw sockets) and still allow GUI/CLI components to be
# run as non-root users. However, since the control interface can be used to
# change the network configuration, this access needs to be protected in many
# cases. By default, wpa_supplicant is configured to use gid 0 (root). If you
# want to allow non-root users to use the contron interface, add a new group
# and change this value to match with that group. Add users that should have
# control interface access to this group.
#
# This variable can be a group name or gid.
#ctrl_interface_group=wheel
ctrl_interface_group=0

# IEEE 802.1X/EAPOL version
# wpa_supplicant was implemented based on IEEE 802-1X-REV-d8 which defines
# EAPOL version 2. However, there are many APs that do not handle the new
# version number correctly (they seem to drop the frames completely). In order
# to make wpa_supplicant interoperate with these APs, the version number is set
# to 1 by default. This configuration value can be used to set it to the new
# version (2).
eapol_version=1

# AP scanning/selection
# By default, wpa_supplicant requests driver to perform AP scanning and then
# uses the scan results to select a suitable AP. Another alternative is to
# allow the driver to take care of AP scanning and selection and use
# wpa_supplicant just to process EAPOL frames based on IEEE 802.11 association
# information from the driver.
# 1: wpa_supplicant initiates scanning and AP selection
# 0: driver takes care of scanning, AP selection, and IEEE 802.11 association
#    parameters (e.g., WPA IE generation); this mode can also be used with
#    non-WPA drivers when using IEEE 802.1X mode
ap_scan=2

# network block
#
# Each network (usually AP's sharing the same SSID) is configured as a separate
# block in this configuration file. The network blocks are in preference order
# (the first match is used).
#
# network block fields:
#
# ssid: SSID (mandatory); either as an ASCII string with double quotation or
#       as hex string; network name
#
# scan_ssid:
#       0 = do not scan this SSID with specific Probe Request frames (default)
#       1 = scan with SSID-specific Probe Request frames (this can be used to
#           find APs that do not accept broadcast SSID or use multiple SSIDs;
#           this will add latency to scanning, so enable this only when needed)
#
# bssid: BSSID (optional); if set, this network block is used only when
#       associating with the AP using the configured BSSID
#
# priority: priority group (integer)
# By default, all networks will get same priority group (0). If some of the
# networks are more desirable, this field can be used to change the order in
# which wpa_supplicant goes through the networks when selecting a BSS. The
# priority groups will be iterated in decreasing priority (i.e., the larger the
# priority value, the sooner the network is matched against the scan results).
# Within each priority group, networks will be selected based on security
# policy, signal strength, etc.
# Please note that AP scanning with scan_ssid=1 is not using this priority to
# select the order for scanning. Instead, it uses the order the networks are in
# the configuration file.
#
# proto: list of accepted protocols
# WPA = WPA/IEEE 802.11i/D3.0
# RSN = WPA2/IEEE 802.11i (also WPA2 can be used as an alias for RSN)
# If not set, this defaults to: WPA RSN
#
# key_mgmt: list of accepted authenticated key management protocols
# WPA-PSK = WPA pre-shared key (this requires 'psk' field)
# WPA-EAP = WPA using EAP authentication (this can use an external
#       program, e.g., Xsupplicant, for IEEE 802.1X EAP Authentication
# IEEE8021X = IEEE 802.1X using EAP authentication and (optionally) dynamically
#       generated WEP keys
# NONE = WPA is not used; plaintext or static WEP could be used
# If not set, this defaults to: WPA-PSK WPA-EAP
#
# pairwise: list of accepted pairwise (unicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# NONE = Use only Group Keys (deprecated, should not be included if APs support
#       pairwise keys)
# If not set, this defaults to: CCMP TKIP
#
# group: list of accepted group (broadcast/multicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# WEP104 = WEP (Wired Equivalent Privacy) with 104-bit key
# WEP40 = WEP (Wired Equivalent Privacy) with 40-bit key [IEEE 802.11]
# If not set, this defaults to: CCMP TKIP WEP104 WEP40
#
# psk: WPA preshared key; 256-bit pre-shared key
# The key used in WPA-PSK mode can be entered either as 64 hex-digits, i.e.,
# 32 bytes or as an ASCII passphrase (in which case, the real PSK will be
# generated using the passphrase and SSID). ASCII passphrase must be between
# 8 and 63 characters (inclusive).
# This field is not needed, if WPA-EAP is used.
# Note: Separate tool, wpa_passphrase, can be used to generate 256-bit keys
# from ASCII passphrase. This process uses lot of CPU and wpa_supplicant
# startup and reconfiguration time can be optimized by generating the PSK only
# only when the passphrase or SSID has actually changed.
#
# eapol_flags: IEEE 802.1X/EAPOL options (bit field)
# Dynamic WEP key require for non-WPA mode
# bit0 (1): require dynamically generated unicast WEP key
# bit1 (2): require dynamically generated broadcast WEP key
#       (3 = require both keys; default)
#
# Following fields are only used with internal EAP implementation.
# eap: space-separated list of accepted EAP methods
#       MD5 = EAP-MD5 (unsecure and does not generate keying material ->
#                       cannot be used with WPA; to be used as a Phase 2 method
#                       with EAP-PEAP or EAP-TTLS)
#       MSCHAPV2 = EAP-MSCHAPv2 (cannot be used separately with WPA; to be used
#               as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       OTP = EAP-OTP (cannot be used separately with WPA; to be used
#               as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       GTC = EAP-GTC (cannot be used separately with WPA; to be used
#               as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       TLS = EAP-TLS (client and server certificate)
#       PEAP = EAP-PEAP (with tunnelled EAP authentication)
#       TTLS = EAP-TTLS (with tunnelled EAP or PAP/CHAP/MSCHAP/MSCHAPV2
#                        authentication)
#       If not set, all compiled in methods are allowed.
#
# identity: Identity string for EAP
# anonymous_identity: Anonymous identity string for EAP (to be used as the
#       unencrypted identity with EAP types that support different tunnelled
#       identity, e.g., EAP-TTLS)
# password: Password string for EAP
# ca_cert: File path to CA certificate file. This file can have one or more
#       trusted CA certificates. If ca_cert is not included, server certificate
#       will not be verified. This is insecure and the CA file should always be
#       configured.
# client_cert: File path to client certificate file
# private_key: File path to client private key file
# private_key_passwd: Password for private key file
# phase1: Phase1 (outer authentication, i.e., TLS tunnel) parameters
#       (string with field-value pairs, e.g., "peapver=0" or
#       "peapver=1 peaplabel=1")
#       'peapver' can be used to force which PEAP version (0 or 1) is used.
#       'peaplabel=1' can be used to force new label, "client PEAP encryption",
#       to be used during key derivation when PEAPv1 or newer. Most existing
#       PEAPv1 implementation seem to be using the old label, "client EAP
#       encryption", and wpa_supplicant is now using that as the default value.
#       Some servers, e.g., Radiator, may require peaplabel=1 configuration to
#       interoperate with PEAPv1; see eap_testing.txt for more details.
#       'peap_outer_success=0' can be used to terminate PEAP authentication on
#       tunneled EAP-Success. This is required with some RADIUS servers that
#       implement draft-josefsson-pppext-eap-tls-eap-05.txt (e.g.,
#       Lucent NavisRadius v4.4.0 with PEAP in "IETF Draft 5" mode)
# phase2: Phase2 (inner authentication with TLS tunnel) parameters
#       (string with field-value pairs, e.g., "auth=MSCHAPV2")
# Following certificate/private key fields are used in inner Phase2
# authentication when using EAP-TTLS or EAP-PEAP.
# ca_cert2: File path to CA certificate file. This file can have one or more
#       trusted CA certificates. If ca_cert2 is not included, server
#       certificate will not be verified. This is insecure and the CA file
#       should always be configured.
# client_cert2: File path to client certificate file
# private_key2: File path to client private key file
# private_key2_passwd: Password for private key file

# Example blocks:

# Only WPA-PSK is used. Any valid cipher combination is accepted.

  network={
  ssid="NetworkForMe"
  scan_ssid=1
  pairwise=TKIP
  psk="mykeywords"
  key_mgmt=WPA-PSK
  proto=WPA
  }

---

### Post by mrmailer on 2005-12-22
btw, if i use ap_scan=1 or =2, iwconfig/ifconfig starts locking up after i use wpa_supplicant 1.2.0

if i use 0, after i run wpa_supplicant, it resets my ESSID to "" and i cannot change it.

---

### Post by roblowe on 2005-12-22
Hi Can I have the necessary files in cd burned with windows or do I need to connect the ubuntu machine and dowload it? thanks

rob

---

### Post by sguart on 2005-12-29
[QUOTE=mrmailer]this is what i just posted to hostap list.  i have fedora core 4.  Also, do you have to set the essid before using wpa_supplicant, or is it set, or what?  do you run dhclient wlan0 after?


Sheesh, why is it so hard to get this working with WPA?  It works fine
without.  I followed the instructions as per this page.
[http://ubuntuforums.org/archive/index.php/t-92327.html](http://ubuntuforums.org/archive/index.php/t-92327.html)
on my fedora core 4 machine

here is my /etc/wpa_supplicant.conf.  Now I set the essid manually,
then issue the command
wpa_supplicant -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas
And then I ran dhclient wlan0, but it never gets the IP.  Then the
keyboard, but not the mouse, stopped working.  help?

...cut...snip...

  network={
  ssid="NetworkForMe"
  scan_ssid=1
  pairwise=TKIP
  psk="mykeywords"
  key_mgmt=WPA-PSK
  proto=WPA
  }[/QUOTE]

First of all,

Thanks to shof2k's howto. I made the most progress after reading this howto. I think we should clean it up and append it to the ubuntu zd1211 wiki howto.

I had the same problem with keyboard locked up. However, it only happened twice so far. I have the problem with the whole machine locked up while it's negotiating or scanning for network. This happened multiple times. Also, sometimes the driver will failed to initialize properly during ifup/down. modprobing it again won't work. I need to unplug the device and plug it back in again. 

I have the gigafast wf748-cui usb dongle. It's running in 802.11b mode cuz the usb port is 1.1 only.

I tried 3 different zd1211 driver. The latest opensource one, from the link provided in the howto. This is based on zydas 2.0.0.0 series. This one compiled right away. However, it will hang during network device initialization during bootup, waiting for dhcp i guess, ctrl-c will get pass it. Also, this one won't hang on to the connection after broadcast ssid is set to disabled.

The other two were from zydas's website. One is the 2.2.0.0 and another one is the 2.3.1.0. Both of them require modification to source code to compile.

For 2.3.1.0, my problem was that it will never associate to the AP for some reason. So I abandoned it after trying multiple settings.

For 2.2.0.0, it behaves almost like the opensource driver, except that it will keep the connection after broadcast id disable is turned on. Also, it won't hang during network device initialization during bootup.

So, that's the driver that I am using for now. It will work with WPA only. And it will only connect to AP after enabling ssid broadcast and then disable it. Using WPA2, it will connect to the AP but won't be able to dhcp.

For getting the /etc/wpa_supplicant.conf parameters to work, i left the proto, pairwise, and group fields commented out. It's default to use all the options. While wpa_supplicant is running, I use wpa_cli to display the status of the connection. This will show those parameters' default value from the AP. Then you can tweak them.

That's my experience so far with my hardware and ubuntu breezy. I think we might have better luck if zydas developer integrate zydas driver support into the latest wpa_supplicant.

again, thanks shof2k for the howto...

best of luck to all that's still struggling...

sg

---

### Post by Lambert on 2005-12-31
> Unfortunately, the versions supplied by ubuntu don't

I was looking for a bug report on driver zd1211 but didn't see one. It might be a good idea to report a bug so this is fixed in dapper.

---

### Post by shof2k on 2006-01-01
The zd1211 module is a pain to deal with.  The 2 main areas of concern are 1) Getting the module to work and connect to an open wireless point, and 2) Getting WPA to sucessfully work with it.

I can only say please keep trying and you will get there in the end.  Try to connect to an open network first to prove that ubuntu's networking is ok.  Then move on to WPA encryption, then move on to automating it.

I have edited the HOW-TO to be clearer on each of the above phases and I'll arrange a bugzilla report and a request to get a working zd1211 in dapper.

Good luck folks,

---

### Post by shof2k on 2006-01-01
Follow up.  This doesn't seem to work with the 2.6.12-10 kernel. I've updated the HOW-TO warning of this.

---

### Post by shof2k on 2006-01-01
I put the wrong version for wpasupplicant - my bad.

I've updated the HOW-TO with the versions for each application. Have fun.

---

### Post by sguart on 2006-01-01
[QUOTE=shof2k]I put the wrong version for wpasupplicant - my bad.

I've updated the HOW-TO with the versions for each application. Have fun.[/QUOTE]

oh wait, i didn't read the update carefully... how did the newer wpa_supplicant work with the zydas driver? i tried the latest one before, 0.4.7. if i use the -D zydas switch, it will complain that it doesn't know about this driver. i thought the one supplied by zydas is a special build to include the zydas driver support? do you have to integrate the zd1211 source into wpa_supplicant source and then make?

oh i google and found a link to someone that patch the 0.4.7 wpa_supplicant with zydas support...

[http://www.nabble.com/Zydas-wpa_supplicant-1_2_0_0-port-to-wpa_supplicant-0.4.7-t811756.html](http://www.nabble.com/Zydas-wpa_supplicant-1_2_0_0-port-to-wpa_supplicant-0.4.7-t811756.html)

everything works after switching to wpa supplicant 0.4.7 w/ zydas driver builtin... hidden network.... wpa2... surviving reboot... good stuff!!!

also, the part in the howto where you mentioned to copy the module to some path... 

this is redundant. if using the latest opensource driver, make install will do this. if using zydas driver from website, make alone will do this for u.

just a heads up,

thanks for the latest info!

sg

---

### Post by shof2k on 2006-01-02
Ah yes.  When compiling wpasupplicant, you need to create a .config file and specify in that to include support for the zydas chip.  I'll edit a copy of it into the HOW-TO.

I've also removed the line about copying the zd1211 module.  The make-install will do just that so you're right there :)

---

### Post by ghee22 on 2006-01-05
ok, i don't have an internet connection directly from my breezy box, it only has the usb zydas wireless for internet.  I DO have an internet connection and a usb memory stick where i am putting all files needed onto so i can transfer them over to the breezy box.

unfortunately, i can't get past one of your steps, sudo apt-get install linux-tree.  linux-tree is not found.  do you have steps for people in my situation?

---

### Post by shof2k on 2006-01-07
linux-tree is part of the standard breezy libraries.  Check /etc/apt/sources.list to make sure all are available to you.

The ones you want are:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe

---

### Post by ghee22 on 2006-01-07
[QUOTE=shof2k]linux-tree is part of the standard breezy libraries.  Check /etc/apt/sources.list to make sure all are available to you.[/QUOTE]

Ah, I see. the problem here is that the machine that has the internet connection is Windows.  How does one download the linux-tree manually from a windows box, and after copying to the breezy box, install from a file?

---

### Post by sguart on 2006-01-08
[QUOTE=ghee22]Ah, I see. the problem here is that the machine that has the internet connection is Windows.  How does one download the linux-tree manually from a windows box, and after copying to the breezy box, install from a file?[/QUOTE]

in my experience, it's much easier to set it up if the machine has internet connection... so give the machine a ethernet card and plug it in... if you have telnetd or sshd setup then u can boot the machine up headless(without display, kb, and mouse... only power) and then remotely set it up from your windows machine.

they are in the process of releasing a 4gb dvd iso that will come with packages so ppl without an inet connection can set it up easily.

otherwise u will have to lookup what the linux-tree deb package is consist of, and download each one of the bundle packages individually and install them.

---

### Post by ghee22 on 2006-01-09
> **sguart]in my experience, it's much easier to set it up if the machine has internet connection...[/QUOTE]
agreed... 

[QUOTE=sguart]so give the machine a ethernet card and plug it in... [/QUOTE]
my laptop's pcmcia slot doesn't work anymore!  so all i have is the usb wireless.

[QUOTE=sguart]they are in the process of releasing a 4gb dvd iso that will come with packages so ppl without an inet connection can set it up easily.[/QUOTE]
CAN'T WAIT!   said:**
> otherwise u will have to lookup what the linux-tree deb package is consist of, and download each one of the bundle packages individually and install them.
Yeah, I'm working on that, posting details when found anything.  If anyone knows the details of where i can get this info, please post.

thanks for the interesting reply sguart

---

### Post by ghee22 on 2006-01-10
[QUOTE=sguart]
they are in the process of releasing a 4gb dvd iso that will come with packages so ppl without an inet connection can set it up easily.
[/QUOTE]

they have a live 2.5 gb dvd iso so far right here: [http://torrent.ubuntu.com/releases/breezy/release/dvd/](http://torrent.ubuntu.com/releases/breezy/release/dvd/)

---

### Post by JuanFerS on 2006-01-10
I know this is probably not relevant to the thread but...
I got mine working (Asus A4L laptop) thanks!!!
Haven't tried wpa yet though...

---

### Post by shof2k on 2006-01-11
It's relavant to the post, so thanks for the post.  Now I know the HOW-TO is useful :)

---

### Post by JuanFerS on 2006-01-16
Just one more thing...

You need to have version 3.4 of GCC installed not 4.0 which is the latest you can get through apt-get.

---

### Post by Roberto N. on 2006-02-05
[QUOTE=shof2k]HOW TO: Zydas ZD1211 wireless with automatic WPA

[...]
Unpack the linux source and create a standard symbolic link
```

        cd /usr/src
	sudo tar --bzip2 -xvf linux-2.6.12.tar.bz2
	sudo ln -s /usr/src/linux-2.6.12 /usr/src/linux
 
```

[...]
[/QUOTE]

Peraphs this is a banal question...but i'm wondering about it ...:-k 
In my /usr/src there is
linux-source-2.6.12.tar.bz2 and not linux-2.6.12.tar.bz2... is the same thing? i can proceed?

Thanks

---

### Post by salgado on 2006-02-05
[QUOTE=JuanFerS]I know this is probably not relevant to the thread but...
I got mine working (Asus A4L laptop) thanks!!!
Haven't tried wpa yet though...[/QUOTE]

Hi Juan,

Did you get this to work on Breezy with the 2.6.12-10 kernel?

---

### Post by aaf on 2006-02-07
I'm a bit confused and am hoping somebody can spell a couple of things out for me.  I have Breezy, so should I follow this HOWTO ?

The prerequisites say that I should have a 2.6.10-9 kernel but later on in the how to it seems to specify the 2.6.12 kernel sources.  Also, the [wiki]("https://wiki.ubuntu.com/WifiDocs/ZydasZD1211?action=show&redirect=zd1211wifi)") suggests this HOWTO as a specific solution for breezy users.

So, given I have a fresh breezy install (kernel 2.6.12-10), would I be advised to follow these instructions?

Thanks in advance...

---

### Post by shof2k on 2006-02-08
The prerequisite is for a 2.6.12-9 kernel.  I tried working on a 2.6.12-10 kernel without success.

Fat fingers on my part...I have corrected the how to.  I never thought this HOW-TO would be good enough for the wiki :D  Let's hope the dapper version works without this.

---

### Post by GreenCountry on 2006-02-08
Shof2k, thanks so much for this thread, I would never have gotten this far without it...

So I've been trying to get a consistent wireless link up, without playing with any security whatsoever, and I haven't been able to.

I'm running Breezy in an iBook G3 500 MHz.  Kernel version 2.6.12-10-powerpc.  I managed to make it compile by editing the zd1211's Makefile line that read "CC=gcc" to be "CC=gcc-3.4" so it would compile on the older 3.4 version of GCC.

The driver loads properly, it detects the zd1211 (which, by the way, my dongle is a TrendNet TEW-429UB), I get wlan0 up and running fine.  GNOME's Network utility lists it as well, and thru that utility I configured wlan0 to be the default gateway.  I can even associate with my base station, according to iwconfig, and the DHCP from the base station is working.

BUT - I can't ping anywhere reliably.  I tried pinging the router itself, and one time it worked, but after that it hasn't.  I tried pinging [www.yahoo.com](www.yahoo.com), and sometimes it works, sometimes it doesn't.  I tried host-ing [www.google.com](www.google.com), and same intermittent working/not.

Mind you, this isn't even trying to futz with the WPA.

Anyone know what gives?

---

### Post by shof2k on 2006-02-09
Glad zd1211 is installed.  This kinda sounds like network access problems.  The hardware modules work ok, it's just getting linux to reliably work it.Something to try:
1) Type ifconfig in the command line to see what interfaces are active.  Ideally you should have only 'lo' and 'wlan0' active.  If you see 'eth0', shut it down with the command
```
sudo ifconfig eth0 down 
```

2) Type iwconfig in the command line to see what sort of wireless access you have.  It may be worth displaying the contents of that and the last 50 lines of dmesg to see if any funnies are happening.

Keep the faith!

---

### Post by GreenCountry on 2006-02-09
[QUOTE=shof2k]Glad zd1211 is installed.  This kinda sounds like network access problems.  The hardware modules work ok, it's just getting linux to reliably work it.Something to try:
1) Type ifconfig in the command line to see what interfaces are active.  Ideally you should have only 'lo' and 'wlan0' active.  If you see 'eth0', shut it down with the command
```
sudo ifconfig eth0 down 
```

2) Type iwconfig in the command line to see what sort of wireless access you have.  It may be worth displaying the contents of that and the last 50 lines of dmesg to see if any funnies are happening.

Keep the faith![/QUOTE]
Darn, I just got antsy and am now installing YDL.  I want to try this though.

So, are you saying that if both eth0 and wlan0 are up, Ubuntu (or linux generally?) will always pick the eth0?  It seems like a rough way to run things... there has to be a way to have both eth0 and wlan0 running and have linux detect that the internet route is thru wlan0...

---

### Post by shof2k on 2006-02-09
I'm not sure exactly, but I had similar problems when both interfaces were up. Killing eth0 made my wireless stable.  The gnome networking tool appears to do this, but I trust the command line method more.

---

### Post by GreenCountry on 2006-02-09
Woo hoo!!!  It's always a good feeling to get something working in Linux.

Thanks shof2k, you were right, I took down eth0, and wlan0 stays up and Ubuntu routes correctly to it.  Weird - and maybe has to do with iptables, which I don't have time to figure out right now.

WPA's next... but maybe I'll wait and see if Dapper has it right...

---

### Post by shof2k on 2006-02-10
Good for you, consider yourself my first satisfied customer :)

I would strongly recommend using some sort of access control or encryption.  Even WEP is better than nothing.

Roll on WPA in dapper!

---

### Post by JuanFerS on 2006-02-10
I compiled it with both the 2.6.12-9 and 2.6.12-10 kernel.

When I updated from 12-9 to 12-10 the card didn't work anymore, so I had to recompile the driver again.

---

### Post by turbulens on 2006-02-11
I got the excact same problem, 
I have followed the howto but still cant get to work.

--

bcb@ubuntu:/usr/src/zd1211src$ make
/lib/modules/2.6.12-10-powerpc/build
/usr/src/zd1211src
-I/usr/src/zd1211src/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.12-10-powerpc/build SUBDIRS=/usr/src/zd1211src modules
make: *** /lib/modules/2.6.12-10-powerpc/build: No such file or directory.  Stop.
make: *** [all] Error 2
bcb@ubuntu:/usr/src/zd1211src$

--
When I try to create the build folder i got this output.
--

bcb@ubuntu:/usr/src/zd1211src$ make
/lib/modules/2.6.12-10-powerpc/build
/usr/src/zd1211src
-I/usr/src/zd1211src/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.12-10-powerpc/build SUBDIRS=/usr/src/zd1211src modules
make[1]: Entering directory `/lib/modules/2.6.12-10-powerpc/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-powerpc/build'
make: *** [all] Error 2
bcb@ubuntu:/usr/src/zd1211src$

Any ideas?

Regards turbulens

---

### Post by GreenCountry on 2006-02-11
Turbulens: I know this isn't "my" HOWTO thread, but I was wondering if I might be able to help.  

I remember getting an error something like that before I read this thread more carefully and got both the linux-source package as well as the linux-headers package.  They are two different things, and moreover, once you download the linux-source package, you have to make sure to unzip the package with "sudo" to have all the linux kernel source files in the proper place.  I am guessing you might have missed one of these steps...?  

Apologies if I'm off.

---

### Post by lexor on 2006-02-19
I have a Sitecom WL-113 USB Adapter, for myself the adapter works out the box at least so I think, I can scan for wireless access points and pick them up but cant connect to my own wireless access point as it uses wpa and the wpa_supplicant useing apt-get dont support my USB adapter.

I have read the one from the Zydas site does, but I have no idea on setting it up I have read a few posts but to be honest my knowlege is limited and I only come up with lots of errors.

I have set up a Belkin wireless card useing ndiswrapper and wpa_supplicant, works great. So no big deal but it would be nice to get the USB working all the same.

---

### Post by Hachi on 2006-02-21
Hi, thanks for the great HOWTO shof2k.

I managed to get my 3com OfficeConnect usb working on 2.6.12-10-386, but I've not gone on to try WPA just yet. 

As for the /lib/modules error, I had to apt-get the linux-headers specific for my kernel version:

```
sudo apt-get install linux-headers-2.6.12-10-386
```

After that I also had to install GCC 3.4:

```
sudo apt-get install gcc-3.4
```

________
Hachi

---

### Post by dom on 2006-03-01
[QUOTE=shof2k]HOW TO: Zydas ZD1211 wireless with automatic WPA
<snip>
Thanks to ubuntu user dom for pointing me in the right direction :)
</snip>
[/QUOTE]

no worries bud, any time,

just quickly browsing now and saw this. I'll read in detail over a coffee sometime and see if i learn anything new from your good looking report.

i have recently added some init scripts to have this run on boot up, as it was annoying me to have to start the custom wpasupplicant each time, and annoying for non root/sudo users also :)

i think i have issues with stop/restart piece of the init script though. But it's starting and i know how to use 'kill' so i'm not in too much trouble :)

i can share of course.

feel free to send me pm's i don't get back here half as much as i'd like to and then i miss things like this.

---

### Post by spuriosity on 2006-03-27
Great HowTo, thank you.  The howto, as well as some other user comments, helped me to get my USB wireless working.

This is my first ever post on a forum, so I apologize in advance for any bad form on my part.

Just wanted to describe what worked for me.

I did not yet do WPA - I will explore WPA in the future.

My system:

- Zonet ZEW2501 USB wireless
- an old NEC Ready 330T laptop
- default Ubuntu Breezy 5.10 installation
- kernel 2.6.12-10-386
- talking to a wireless router

To get it to work on 2.6.12-10-386, I followed the original HowTo steps, plus Hachi's 2 steps notes (kernel headers were not included in the other installations, and the zd1211 code wanted gcc-3.4 since my default install was 4.0 and this produced many compile errors)

sudo apt-get install linux-headers-2.6.12-10-386
sudo apt-get install gcc-3.4

I used the zd1211 driver version:
zd1211-driver-r67

change the zd1211 Makefile:
CC=gcc-3.4

A few warnings on compile, but it worked fine.

For what it's worth, I use a script based on the zd1211 website recommendations to reload and reset the network on return from hibernation - it has worked every time now (thanks to this howto that got me set to quickly compile the newer driver).

modprobe -v zd1211
ifconfig wlan0 up 
iwconfig wlan0 essid myssid
/etc/init.d/networking restart
dhclient wlan0 

Thank you for your work!

---

### Post by foodeater on 2006-05-02
Hi, I am completely new to linux, and am trying to use the gigafastwf741-uic usb dongle. 

The problem is that I am using a power book g3 "pismo". I think this means some of these instructions are a bit different for me, and I am using linux (and the command line!) for the first time, this is really throwing me for a loop. 

I just want to be clear on the linking, I have 2 hears folders one end with ppc. I linked to the one without the ppc extension, is this wrong?

GreenCountry, it sounds like you are also using the a ppc. Is it possible to download the compiled files from you? The tip to change gcc to gcc-3.4 let me get farther in compiling, but I still got tons of errors, instead of missing errors, I got  div by zero among others.

I decided to try to load it anyway since I have a main computer ( that I am typing this from) So then the network part of ubuntu took forever to load on start up, and of course it didn't see the dongle. Unfortunately I can't copy the error message(s) for every one to see because I re-installed ubuntu. I could try it again, but I need a break ;-)

Does this give enough information to tell me what I was doing wrong? I hope so because I really want to use ubuntu/linux, but without wireless... 

Thanks for any help!! These forums are really cool, I have been learning tons.

PS does airport work(out of the box)? I think I can get one for 30 dollars.

---

### Post by GreenCountry on 2006-05-02
Sorry, I sold the iBook that was running Ubuntu... I'm running Damn Small Linux on a 300MHz x86 now...

---

### Post by sguart on 2006-05-07
All,

i came across this [http://ubuntuforums.org/showthread.php?t=144820]("http://ubuntuforums.org/showthread.php?t=144820")

it's about the networkmanager app that will be in the next version. But looks like wheelspin is putting together a script to install drivers based on people's howtos. Maybe he can add the zydas driver install into his script. What do you think shof2k?

Another thing, it seems like i will lose my wireless connection if i am inactive for more than 30min or so and after that i will not be able to reestablish connection with ap.

If it's just slightly longer than 30min, from wpa_cli, the wpa_supplicant is reporting status as disconnect. If I kill the wpa_supplicant and restart then I will regain the connection.

If it's alot longer than 30min, then wpa_cli will report that it's trying to associate with the AP but it will always timed out. Removing and reinserting my usb wireless adapter and restart the wpa_supplicant will fix it.

I can get around it by keeping the connection busy with ping. But I was wondering if other ppl have encountered this and found a solution? Is there a driver switch or wpa_supplicant switch for this?

hmm... i also noticed that the zydas website has updated driver and wpa_supplicant for download with instructions... so ppl might try it out if the current drivers are not working... [http://www.zydas.com.tw/downloads/download-1211.asp]("http://www.zydas.com.tw/downloads/download-1211.asp")

thanks
sg

---

### Post by AtreidesNZ on 2006-05-15
Hey, I'm having some trouble getting **make** to work properly.

I followed all of the good, reasonably clear instructions from the beginning of shof2k's HowTo, so now I have the latest versions of lots of things, and have the linux source and headers and driver source and such.
I do have the *2.6.12-10-386* kernel, which some people say works with this and others say doesn't.
I have gcc 4, but I apt-got gcc 3.4 as well and changed the zd1211 Makefile line to "CC=gcc-3.4" as Hachi mentioned.

However, when I try to *make the zd1211 driver*, it does not work. The error is **"No rule to make target 'modules'. Stop."**

Here's the complete make error:
> peter@ubuntu-peter:/usr/src/zd1211src$ sudo make
/lib/modules/2.6.12-10-386/build
/usr/src/zd1211src
-I/usr/src/zd1211src/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
*make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/usr/src/zd1211src modules*
make[1]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** **No rule to make target `modules'.  Stop.**
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make: *** [all] Error 2
peter@ubuntu-peter:/usr/src/zd1211src$


Any idea what I'm doing wrong or have to do further?

Thanks,
Atreides

---

### Post by shof2k on 2006-05-16
Haachi is correct in recommending gcc-3.4.  I never got 2.6.12-10 to work only 2.6.12-9, but thats probably me as it also works with the dapper kernel.

You need to create a link called /lib/modules/2.6.12-10-386/build pointing to either /usr/src/linux or /usr/src/linux-headers.  I can't be more specific as I'm on a public PC here.

---

### Post by AtreidesNZ on 2006-05-17
Sorry for my delay, and thanks for your quick response. I've now tried your suggestion and am afraid it has not worked.

Making a link /lib/modules/2.6.12-10-386/build pointing to /usr/src/linux causes one hell of a lot of errors - couple of dozen per .c or .o file it tries to do something to, and a lot of division by zero as well. Pointing the link to /usr/src/linux-headers causes a lesser number of errors but it stops straight away. No such file or directory for a gcc-version.sh, no Module.symvers, no Makefile.build. There is a /usr/src/linux-headers so that's not exactly the problem.

Any more ideas? Would you like me to post the actual text of the errors? This does seem like progress since it gets something different to happen! ;)

---

### Post by shof2k on 2006-05-18
link to /usr/src/linux-headers-2.6.12-10-386 as /lib/modules/2.6.12-10-386/build.  

Hope that helps

---

### Post by AtreidesNZ on 2006-05-18
[COLOR=DarkRed]YES! **WE HAVE SUCCESS!**[/COLOR]

It was indeed that reasonably banal but typically obscure bit of trouble with symbolic linking. With /lib/modules/2.6.12-10-386/build pointing to exactly /usr/src/linux-headers-2.6.12-10-386, make and make install have succeeded, I can modprobe -v zd1211, ifconfig wlan0 up, and iwconfig, iwlist scanning, and it all works! I'll try the particular programs I'm interested in after the weekend (I'm going away) but thought that posting this now would be worthwhile.

**Thank you shof2k!**

I'll have an update on whether I actually manage to connect to a network and get the programs working - and setting up WPA encryption will be an odyssey in itself, I expect. *But I've got the driver installed!* :D

---

### Post by rainycoast on 2006-09-12
**SUCCESS** 

Thanks so much for taking the time to write the guide. I was just about ready to give up on ever getting this to work. 

Please contribute more guides!

Cheers,

John

---

### Post by G_Dem on 2006-10-19
Thanks so much for this guide. You dont understand how many probs I had getting my old linksys card to work. My new Zyxel AG-225H and your guide has finally got me a wireless connection.

The only thing is when WEP is enabled and I try to configure the WEP key, when I OK it, it stays connecting for ages. Then I cant seem to open up any programs, log off or do anything. The system doesn't hang as such but it just doesn't seem to obey my commands. Any ideas???

---

### Post by Ryanmt on 2006-11-07
im thinking about buying a Hawking HWL2 but im slightly worried after seeing how comeplex this guide is. I go from one wifi network to another quite often so editing text files for it isnt really idea. Does this work with the wifi manager in dapper once its installed and up and running?

---

### Post by shof2k on 2006-11-07
You may need to switch off your cable connection using "sudo ifconfig eth0 down".  If your machine still hangs try using an unencrypted network. If that works, then the fault is with the gnome network manager.

---

### Post by kufio on 2007-03-13
I cant install the driver, this is the logmake
make both
make[1]: Entering directory `/home/kufio/driverwifi'
make clean
make[2]: Entering directory `/home/kufio/driverwifi'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg winevl_iface
make[2]: Leaving directory `/home/kufio/driverwifi'
make ZD1211REV_B=0
make[2]: Entering directory `/home/kufio/driverwifi'
/lib/modules/2.6.15-28-386/build
/home/kufio/driverwifi
-I/home/kufio/driverwifi/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211 -DZDCONF_LP_SUPPORT=0
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zdmisc.o src/zd1211.o
make -C /lib/modules/2.6.15-28-386/build SUBDIRS=/home/kufio/driverwifi modules
/usr/src/linux-headers-2.6.15-28-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.15-28-386/scripts/gcc-version.sh: line 12: gcc: command not found
make[3]: gcc: Command not found
make[3]: Entering directory `/usr/src/linux-headers-2.6.15-28-386'
  CC [M]  /home/kufio/driverwifi/src/zd1205.o
/bin/sh: gcc: command not found
make[4]: *** [/home/kufio/driverwifi/src/zd1205.o] Error 127
make[3]: *** [_module_/home/kufio/driverwifi] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.15-28-386'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/kufio/driverwifi'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/kufio/driverwifi'
make: *** [all] Error 2
:


I have gcc 3.4 installed
thanks

---

### Post by vlerknozem on 2007-05-21
> Download the latest zd1211 driver source from [http://zd1211.ath.cx/download](http://zd1211.ath.cx/download) and unpackage it to /usr/src/zd1211src. I used version r38.

Hello, 

I've tried to download the drivesource, but it doesn't exist.

It's moved to this location: [http://zd1211.wiki.sourceforge.net/](http://zd1211.wiki.sourceforge.net/). I don't know what I need to download.

I'm sorry for my bad english;)

---

### Post by TCE on 2007-05-23
You need to download the vendor based driver. Then download the driver by using subversion after installing it by typing apt-get install subversion.  Just follow the link to Vendor based community driver than look for the install directions on that page for all the info you need.

---

### Post by matrix_83 on 2007-07-06
Hi,
I tried to compile the source but I have the following errors:

```

root@Franz-Ubuntu:/usr/src/modules/zd1211# make
/lib/modules/2.6.20-16-generic/build
/usr/src/modules/zd1211
-I/usr/src/modules/zd1211/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/modules/zd1211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/zd1211/src/zd1205.o
/usr/src/modules/zd1211/src/zd1205.c:34:26: error: linux/config.h: Nessun file o directory
In file included from /usr/src/modules/zd1211/src/zd1205.c:42:
/usr/src/modules/zd1211/src/zd1205.h:1332: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.h:1279: warning: ‘zd_readl’ declared inline after being called
/usr/src/modules/zd1211/src/zd1205.h:1279: warning: previous declaration of ‘zd_readl’ was here
/usr/src/modules/zd1211/src/zd1205.c: In function ‘zd1205_validate_frame’:
/usr/src/modules/zd1211/src/zd1205.c:2806: warning: unused variable ‘len1’
/usr/src/modules/zd1211/src/zd1205.c: In function ‘zd1205_translate_scan’:
/usr/src/modules/zd1211/src/zd1205.c:7176: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘U32’
/usr/src/modules/zd1211/src/zd1205.c:7176: warning: unknown conversion type character ‘,’ in format
/usr/src/modules/zd1211/src/zd1205.c:7176: warning: spurious trailing ‘%’ in format
/usr/src/modules/zd1211/src/zd1205.c: In function ‘zd1205_list_bss’:
/usr/src/modules/zd1211/src/zd1205.c:7381: warning: format ‘%2d’ expects type ‘int’, but argument 2 has type ‘U32’
/usr/src/modules/zd1211/src/zd1205.c:7381: warning: spurious trailing ‘%’ in format
/usr/src/modules/zd1211/src/zd1205.c: At top level:
/usr/src/modules/zd1211/src/zd1205.c:7520: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c:7601: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c:7690: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c:7706: warning: type qualifiers ignored on function return type
/usr/src/modules/zd1211/src/zd1205.c: In function ‘CalculateQuality’:
/usr/src/modules/zd1211/src/zd1205.c:10046: warning: unused variable ‘rxOffset’
make[2]: *** [/usr/src/modules/zd1211/src/zd1205.o] Error 1
make[1]: *** [_module_/usr/src/modules/zd1211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```

notice that "Nessun file o directory" means that no file or directory exists (if you don't understand italian!). How I can do? Thanks!!

---

### Post by enupnia on 2007-08-14
try this instead:

apt-get install source zd1211-source
tar -xvzf zd1211-source*
module-assistant update
module-assistant build zd1211


it worked for me.

I still have a problem with wpa because i got an error compiling end I can't find a working link for the zydas wpa supplicant port

---

### Post by enupnia on 2007-08-14
I did everything read in this how to.

anyway, my zydas dongle is not working. the output of dmesg sounds good:

[ 1229.250923]  _____     ____    _    ____
[ 1229.250932] |__  /   _|  _ \  / \  / ___|
[ 1229.250941]   / / | | | | | |/ _ \ \___ \
[ 1229.250950]  / /| |_| | |_| / ___ \ ___) |
[ 1229.250958] /____\__, |____/_/   \_\____/
[ 1229.250967]      |___/
[ 1229.250975] ZD1211B - version 2.14.0.0
[ 1229.254091] usbcore: registered new driver zd1211b
[ 1238.584975] usb 2-1: new full speed USB device using ohci_hcd and address 4
[ 1238.793794] vendor_id = ce0a
[ 1238.793816] product_id = 1512
[ 1238.793823] USB 1.1 Host
[ 1238.794057] Release Ver = 1048
[ 1238.794068] zd1211:bulk out: wMaxPacketSize = 4000
[ 1238.794080] zd1211:bulk in: wMaxPacketSize = 4000
[ 1238.794092] zd1211:interrupt in: wMaxPacketSize = 4000
[ 1238.794103] zd1211:interrupt in: int_interval = 1
[ 1238.794113] zd1211:bulk out: wMaxPacketSize = 4000
[ 1238.794129] EEPORM Ver = 4810
[ 1238.794137] zd1211:macp->release != EEPVer
[ 1238.809757] zd1211:USB Download Boot code success

but then there's NO wlan0 in ifconfig, 
If I add it in /etc/network/interfaces and then "ifconfig wlan0 up"  or "ifup wlan0" all I get is:

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

I really need help, thx

---

