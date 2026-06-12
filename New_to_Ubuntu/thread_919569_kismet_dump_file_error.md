---
title: "kismet dump file error"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by mike22 on 2008-09-14
Hi, I tried to run kismet and I get this error:

FATAL: Dump file error: Unable to open dump file Kismet-Sep-14-2008-1.dump (Permission denied)



This means that I have to be root to get it working? If so how? Is it sudo kismet?

Or do I reinstall kismet and use suiduser install instead of make install?

---

### Post by pytheas22 on 2008-09-14
I haven't used kismet in a long time, but as I recall, it needed to be run as root.  It's not only because of dump file issues, but also because you need to be root to access wireless cards in the way that kismet wants.  So run it with:
```

sudo kismet
```

---

### Post by mike22 on 2008-09-14
I still get the same error.

---

### Post by pytheas22 on 2008-09-14
Which directory are you trying to run kismet from?  It might help to start it with:
```

cd ~/Desktop
sudo kismet
```

Also, check your kismet configuration file (not sure where it is, but probably /etc/kismet/kismet.conf or something like that).  Is there an invalid location set to save the dump file?

---

### Post by mike22 on 2008-09-14
> **pytheas22 said:**
> Which directory are you trying to run kismet from?  It might help to start it with:
```

cd ~/Desktop
sudo kismet
```

Also, check your kismet configuration file (not sure where it is, but probably /etc/kismet/kismet.conf or something like that).  Is there an invalid location set to save the dump file?

Where in the configuration file is saving the dump file? Sorry I'm a little lazy today.


edit: I have four files saved to my desktop recently. They are: Kismet-Sep-14-2008-1.network, Kismet-Sep-14-2008-1.cisco, Kismet-Sep-14-208-1.csv, and Kismet-Sep-14-2008-1.xml.

---

### Post by pytheas22 on 2008-09-14
I don't know where in the configuration file it says where the dump should be saved to but I'll take a look.  Could you please copy and paste here the entire terminal output that you get when you try to run kismet, as well as your /etc/kismet/kismet.conf file?

Also, how did you install kismet?  Did you compile from source or use a Debian package?

---

### Post by mike22 on 2008-09-14
> **pytheas22 said:**
> I don't know where in the configuration file it says where the dump should be saved to but I'll take a look.  Could you please copy and paste here the entire terminal output that you get when you try to run kismet, as well as your /etc/kismet/kismet.conf file?

Also, how did you install kismet?  Did you compile from source or use a Debian package?

I Believed I compiled it from source. As in cd (tar directory), ./configure, make, make install?

**When I run kismet:**


```
Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to michael (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (rt73-gpl-cvs): Enabling monitor mode for rt73 source interface wlan1 channel 6...
Source 0 (rt73-gpl-cvs): Opening rt73 source interface wlan1...
Spawned channel control process 19467
Dropped privs to michael (1000) gid 1000
Will attempt to put networkmanager to sleep...
Allowing clients to fetch WEP keys.
Logging networks to Kismet-Sep-14-2008-1.network
Logging networks in CSV format to Kismet-Sep-14-2008-1.csv
Logging networks in XML format to Kismet-Sep-14-2008-1.xml
Logging cryptographically weak packets to Kismet-Sep-14-2008-1.weak
Logging cisco product information to Kismet-Sep-14-2008-1.cisco
Logging gps coordinates to Kismet-Sep-14-2008-1.gps
Logging data to Kismet-Sep-14-2008-1.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from /usr/local/etc/ap_manuf
Reading client manufacturer data and defaults from /usr/local/etc/client_manuf
Using network-classifier based data encryption detection
Not tracking duplicate IVs
Putting networkmanager to sleep...
**FATAL: Dump file error: Unable to open dump file Kismet-Sep-14-2008-1.dump (Permission denied)**
Sending termination request to channel control child 19467...
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
         restart or reconfigure it for normal operation.
Waiting for channel control child 19467 to exit...
Trying to wake networkmanager back up...
Kismet exiting.
Done.

```





**My configuration file:**

```
# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2008.05.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
suiduser=michael

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=rt73,wlan1,rt73-gpl-cvs

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource


# Automatically destroy VAPs on multi-vap interfaces (like madwifi-ng).
# Madwifi-ng doesn't work in rfmon when non-rfmon VAPs are present, however
# this is a fairly invasive change to the system so it CAN be disabled.  Expect
# things not to work in most cases if you do disable it, however.
vapdestroy=true


# Do we channelhop?
channelhop=true

# How many channels per second do we hop?  (1-10)
channelvelocity=5

# By setting the dwell time for channel hopping we override the channelvelocity
# setting above and dwell on each channel for the given number of seconds.
#channeldwell=10

# Do we split channels between cards on the same spectrum?  This means if 
# multiple 802.11b capture sources are defined, they will be offset to cover
# the most possible spectrum at a given time.  This also controls splitting
# fine-tuned sourcechannels lines which cover multiple interfaces (see below)
channelsplit=true

# Basic channel hopping control:
# These define the channels the cards hop through for various frequency ranges
# supported by Kismet.   More finegrain control is available via the 
# "sourcechannels" configuration option.
# 
# Don't change the IEEE80211<x> identifiers or channel hopping won't work.

# Users outside the US might want to use this list:
# defaultchannels=IEEE80211b:1,7,13,2,8,3,14,9,4,10,5,11,6,12
defaultchannels=IEEE80211b:1,6,11,2,7,3,8,4,9,5,10

# 802.11g uses the same channels as 802.11b...
defaultchannels=IEEE80211g:1,6,11,2,7,3,8,4,9,5,10

# 802.11a channels are non-overlapping so sequential is fine.  You may want to
# adjust the list depending on the channels your card actually supports.
# defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64,100,104,108,112,116,120,124,128,132,136,140,149,153,157,161,184,188,192,196,200,204,208,212,216 
defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64

# Combo cards like Atheros use both 'a' and 'b/g' channels.  Of course, you
# can also explicitly override a given source.  You can use the script 
# extras/listchan.pl to extract all the channels your card supports.
defaultchannels=IEEE80211ab:1,6,11,2,7,3,8,4,9,5,10,36,40,44,48,52,56,60,64

# Fine-tuning channel hopping control:
# The sourcechannels option can be used to set the channel hopping for 
# specific interfaces, and to control what interfaces share a list of 
# channels for split hopping.  This can also be used to easily lock
# one card on a single channel while hopping with other cards.
# Any card without a sourcechannel definition will use the standard hopping
# list.
# sourcechannels=sourcename[,sourcename]:ch1,ch2,ch3,...chN

# ie, for us channels on the source 'prism2source' (same as normal channel
# hopping behavior):
# sourcechannels=prism2source:1,6,11,2,7,3,8,4,9,5,10

# Given two capture sources, "prism2a" and "prism2b", we want prism2a to stay
# on channel 6 and prism2b to hop normally.  By not setting a sourcechannels 
# line for prism2b, it will use the standard hopping.
# sourcechannels=prism2a:6

# To assign the same custom hop channel to multiple sources, or to split the 
# same custom hop channel over two sources (if splitchannels is true), list
# them all on the same sourcechannels line:
# sourcechannels=prism2a,prism2b,prism2c:1,6,11

# Port to serve GUI data
tcpport=2501
# People allowed to connect, comma seperated IP addresses or network/mask
# blocks.  Netmasks can be expressed as dotted quad (/255.255.255.0) or as
# numbers (/24)
allowedhosts=127.0.0.1
# Address to bind to.  Should be an address already configured already on
# this host, reverts to INADDR_ANY if specified incorrectly.
bindaddress=127.0.0.1
# Maximum number of concurrent GUI's
maxclients=5

# Do we have a GPS?
gps=true
# Host:port that GPSD is running on.  This can be localhost OR remote!
gpshost=localhost:2947
# Do we lock the mode?  This overrides coordinates of lock "0", which will
# generate some bad information until you get a GPS lock, but it will 
# fix problems with GPS units with broken NMEA that report lock 0
gpsmodelock=false

# Packet filtering options:
# filter_tracker - Packets filtered from the tracker are not processed or
#                  recorded in any way.
# filter_dump    - Packets filtered at the dump level are tracked, displayed,
#                  and written to the csv/xml/network/etc files, but not 
#                  recorded in the packet dump
# filter_export  - Controls what packets influence the exported CSV, network,
#                  xml, gps, etc files.
# All filtering options take arguments containing the type of address and
# addresses to be filtered.  Valid address types are 'ANY', 'BSSID',
# 'SOURCE', and 'DEST'.  Filtering can be inverted by the use of '!' before
# the address.  For example,
# filter_tracker=ANY(!00:00:DE:AD:BE:EF)
# has the same effect as the previous mac_filter config file option.
# filter_tracker=...
# filter_dump=...
# filter_export=...

# Alerts to be reported and the throttling rates.
# alert=name,throttle/unit,burst/unit
# The throttle/unit describes the number of alerts of this type that are
# sent per time unit.  Valid time units are second, minute, hour, and day.
# Burst rates control the number of packets sent at a time
# For example:
# alert=FOO,10/min,5/sec
# Would allow 5 alerts per second, and 10 alerts total per minute.
# A throttle rate of 0 disables throttling of the alert.
# See the README for a list of alert types.
alert=NETSTUMBLER,10/min,1/sec
alert=WELLENREITER,10/min,1/sec
alert=LUCENTTEST,10/min,1/sec
alert=DEAUTHFLOOD,10/min,2/sec
alert=BCASTDISCON,10/min,2/sec
alert=CHANCHANGE,5/min,1/sec
alert=AIRJACKSSID,5/min,1/sec
alert=PROBENOJOIN,10/min,1/sec
alert=DISASSOCTRAFFIC,10/min,1/sec
alert=NULLPROBERESP,10/min,1/sec
alert=BSSTIMESTAMP,10/min,1/sec
alert=MSFBCOMSSID,10/min,1/sec
alert=LONGSSID,10/min,1/sec
alert=MSFDLINKRATE,10/min,1/sec
alert=MSFNETGEARBEACON,10/min,1/sec
alert=DISCONCODEINVALID,10/min,1/sec
alert=DEAUTHCODEINVALID,10/min,1/sec

# Known WEP keys to decrypt, bssid,hexkey.  This is only for networks where
# the keys are already known, and it may impact throughput on slower hardware.
# Multiple wepkey lines may be used for multiple BSSIDs.
# wepkey=00:DE:AD:C0:DE:00,FEEDFACEDEADBEEF01020304050607080900

# Is transmission of the keys to the client allowed?  This may be a security
# risk for some.  If you disable this, you will not be able to query keys from
# a client.
allowkeytransmit=true

# How often (in seconds) do we write all our data files (0 to disable)
writeinterval=300

# How old (and inactive) does a network need to be before we expire it?
# This is really only good for limited ram environments where keeping a
# total log of all networks is problematic.  This is in seconds, and should
# be set to a large value like 12 or 24 hours.  This is intended for use
# on stationary systems like an IDS
# logexpiry=86400

# Do we limit the number of networks we log?  This is for low-ram situations
# when tracking everything could lead to the system falling down.  This
# should be combined with a sane logexpiry value to flush out very old 
# inactive networks.  This is mainly for stationary systems like an IDS.
# limitnets=10000

# Do we track IVs?  this can help identify some attacks, but takes a LOT
# of memory to do so on a busy network.  If you have the RAM, by all
# means turn it on.
trackivs=false

# Do we use sound?
# Not to be confused with GUI sound parameter, this controls wether or not the
# server itself will play sound.  Primarily for headless or automated systems.
sound=false
# Path to sound player
soundplay=/usr/bin/play
# Optional parameters to pass to the player
# soundopts=--volume=.3
# New network found
sound_new=${prefix}/share/kismet/wav/new_network.wav
# Wepped new network
# sound_new_wep=${prefix}/com/kismet/wav/new_wep_network.wav
# Network traffic sound
sound_traffic=${prefix}/share/kismet/wav/traffic.wav
# Network junk traffic found
sound_junktraffic=${prefix}/share/kismet/wav/junk_traffic.wav
# GPS lock aquired sound
# sound_gpslock=${prefix}/share/kismet/wav/foo.wav
# GPS lock lost sound
# sound_gpslost=${prefix}/share/kismet/wav/bar.wav
# Alert sound
sound_alert=${prefix}/share/kismet/wav/alert.wav

# Does the server have speech? (Again, not to be confused with the GUI's speech)
speech=false
# Server's path to Festival
festival=/usr/bin/festival
# Are we using festival lite?  If so, set the above "festival" path to also
# point to the "flite" binary
flite=false
# Are we using Darwin speech? 
darwinsay=false
# What voice do we use?  (Currently only valid on Darwin)
speech_voice=default
# How do we speak?  Valid options:
# speech    Normal speech
# nato      NATO spellings (alpha, bravo, charlie)
# spell     Spell the letters out (aye, bee, sea)
speech_type=nato
# speech_encrypted and speech_unencrypted - Speech templates
# Similar to the logtemplate option, this lets you customize the speech output.
# speech_encrypted is used for an encrypted network spoken string
# speech_unencrypted is used for an unencrypted network spoken string
#
# %b is replaced by the BSSID (MAC) of the network
# %s is replaced by the SSID (name) of the network
# %c is replaced by the CHANNEL of the network
# %r is replaced by the MAX RATE of the network
speech_encrypted=New network detected, s.s.i.d. %s, channel %c, network encrypted.
speech_unencrypted=New network detected, s.s.i.d. %s, channel %c, network open.

# Where do we get our manufacturer fingerprints from?  Assumed to be in the
# default config directory if an absolute path is not given.
ap_manuf=ap_manuf
client_manuf=client_manuf

# Use metric measurements in the output?
metric=false

# Do we write waypoints for gpsdrive to load?  Note:  This is NOT related to
# recent versions of GPSDrive's native support of Kismet.
waypoints=false
# GPSDrive waypoint file.  This WILL be truncated.
waypointdata=%h/.gpsdrive/way_kismet.txt
# Do we want ESSID or BSSID as the waypoint name ?
waypoint_essid=false

# How many alerts do we backlog for new clients?  Only change this if you have
# a -very- low memory system and need those extra bytes, or if you have a high
# memory system and a huge number of alert conditions.
alertbacklog=50

# File types to log, comma seperated
# dump    - raw packet dump
# network - plaintext detected networks
# csv     - plaintext detected networks in CSV format
# xml     - XML formatted network and cisco log
# weak    - weak packets (in airsnort format)
# cisco   - cisco equipment CDP broadcasts
# gps     - gps coordinates
logtypes=dump,network,csv,xml,weak,cisco,gps

# Do we track probe responses and merge probe networks into their owners?
# This isn't always desireable, depending on the type of monitoring you're
# trying to do.
trackprobenets=true

# Do we log "noise" packets that we can't decipher?  I tend to not, since 
# they don't have anything interesting at all in them.
noiselog=false

# Do we log corrupt packets?  Corrupt packets have enough header information
# to see what they are, but someting is wrong with them that prevents us from
# completely dissecting them.  Logging these is usually not a bad idea.
corruptlog=true

# Do we log beacon packets or do we filter them out of the dumpfile
beaconlog=true

# Do we log PHY layer packets or do we filter them out of the dumpfile
phylog=true

# Do we mangle packets if we can decrypt them or if they're fuzzy-detected
mangledatalog=true

# Do we do "fuzzy" crypt detection?  (byte-based detection instead of 802.11
# frame headers)
# valid option: Comma seperated list of card types to perform fuzzy detection 
#  on, or 'all'
fuzzycrypt=wtapfile,wlanng,wlanng_legacy,wlanng_avs,hostap,wlanng_wext,ipw2200,ipw2915

# Do we do forgiving fuzzy packet decoding?  This lets us handle borked drivers
# which don't indicate they're including FCS, and then do.
fuzzydecode=wtapfile,radiotap_bsd_a,radiotap_bsd_g,radiotap_bsd_bg,radiotap_bsd_b,pcapfile

# Do we use network-classifier fuzzy-crypt detection?  This means we expect 
# packets that are associated with an encrypted network to be encrypted too, 
# and we process them by the same fuzzy compare. 
# This essentially replaces the fuzzycrypt per-source option.
netfuzzycrypt=true

# What type of dump do we generate? 
# valid option: "wiretap" 
dumptype=wiretap
# Do we limit the size of dump logs?  Sometimes ethereal can't handle big ones.
# 0 = No limit
# Anything else = Max number of packets to log to a single file before closing
# and opening a new one.
dumplimit=0

# Do we write data packets to a FIFO for an external data-IDS (such as Snort)?
# See the docs before enabling this.
#fifo=/tmp/kismet_dump

# Default log title
logdefault=Kismet

# logtemplate - Filename logging template.
# This is, at first glance, really nasty and ugly, but you'll hardly ever
# have to touch it so don't complain too much.
#
# %n is replaced by the logging instance name
# %d is replaced by the current date as Mon-DD-YYYY
# %D is replaced by the current date as YYYYMMDD
# %t is replaced by the starting log time
# %i is replaced by the increment log in the case of multiple logs
# %l is replaced by the log type (dump, status, crypt, etc)
# %h is replaced by the home directory
# ie, "netlogs/%n-%d-%i.dump" called with a logging name of "Pok" could expand
# to something like "netlogs/Pok-Dec-20-01-1.dump" for the first instance and 
# "netlogs/Pok-Dec-20-01-2.%l" for the second logfile generated.
# %h/netlots/%n-%d-%i.dump could expand to
# /home/foo/netlogs/Pok-Dec-20-01-2.dump
#
# Other possibilities:  Sorting by directory
# logtemplate=%l/%n-%d-%i
# Would expand to, for example,
# dump/Pok-Dec-20-01-1
# crypt/Pok-Dec-20-01-1
# and so on.  The "dump", "crypt", etc, dirs must exist before kismet is run
# in this case.
logtemplate=%n-%d-%i.%l

# Where do we store the pid file of the server?
piddir=/var/run/

# Where state info, etc, is stored.  You shouldnt ever need to change this.
# This is a directory.
configdir=%h/.kismet/

# cloaked SSID file.  You shouldn't ever need to change this.
ssidmap=ssid_map

# Group map file.  You shouldn't ever need to change this.
groupmap=group_map

# IP range map file.  You shouldn't ever need to change this.
ipmap=ip_map

```

---

### Post by pytheas22 on 2008-09-15
Unless there's a reason that you compiled kismet from source instead of using the repositories, you should probably try just installing it using apt-get.  You can do that by typing:
```

sudo apt-get install kismet
```

You might need to reconfigure the configuration file afterwards.  But if you install from the repositories, you'll get a version built specifically for Ubuntu, which should help fix whatever is wrong.

---

### Post by mike22 on 2008-09-15
I uninstalled kismet from synaptic. The version in synaptic is 2007-10-R1 and the version I'm trying to install I believe is 2008-05-R1. I reinstalled on root using sudo apt-get install kismet, to no avail.

---

### Post by pytheas22 on 2008-09-15
hmmm, sorry it's still not working.  I installed kismet myself from Synaptic and it works fine when launched as root--the only thing parameter that I had to change in the configuration file was the source interface.  I apparently got version 2007.09.R1, so I'm not sure why yours was slightly different.  Are you running Ubuntu Hardy?

My configuration is below (note that I did not set the suiduser option at all):

```
# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
#suiduser=your_user_here

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_g,wifi0,AtherosG


# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource


# Automatically destroy VAPs on multi-vap interfaces (like madwifi-ng).
# Madwifi-ng doesn't work in rfmon when non-rfmon VAPs are present, however
# this is a fairly invasive change to the system so it CAN be disabled.  Expect
# things not to work in most cases if you do disable it, however.
vapdestroy=true


# Do we channelhop?
channelhop=true

# How many channels per second do we hop?  (1-10)
channelvelocity=5

# By setting the dwell time for channel hopping we override the channelvelocity
# setting above and dwell on each channel for the given number of seconds.
#channeldwell=10

# Do we split channels between cards on the same spectrum?  This means if 
# multiple 802.11b capture sources are defined, they will be offset to cover
# the most possible spectrum at a given time.  This also controls splitting
# fine-tuned sourcechannels lines which cover multiple interfaces (see below)
channelsplit=true

# Basic channel hopping control:
# These define the channels the cards hop through for various frequency ranges
# supported by Kismet.   More finegrain control is available via the 
# "sourcechannels" configuration option.
# 
# Don't change the IEEE80211<x> identifiers or channel hopping won't work.

# Users outside the US might want to use this list:
# defaultchannels=IEEE80211b:1,7,13,2,8,3,14,9,4,10,5,11,6,12
defaultchannels=IEEE80211b:1,6,11,2,7,3,8,4,9,5,10

# 802.11g uses the same channels as 802.11b...
defaultchannels=IEEE80211g:1,6,11,2,7,3,8,4,9,5,10

# 802.11a channels are non-overlapping so sequential is fine.  You may want to
# adjust the list depending on the channels your card actually supports.
# defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64,100,104,108,112,116,120,124,128,132,136,140,149,153,157,161,184,188,192,196,200,204,208,212,216 
defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64

# Combo cards like Atheros use both 'a' and 'b/g' channels.  Of course, you
# can also explicitly override a given source.  You can use the script 
# extras/listchan.pl to extract all the channels your card supports.
defaultchannels=IEEE80211ab:1,6,11,2,7,3,8,4,9,5,10,36,40,44,48,52,56,60,64

# Fine-tuning channel hopping control:
# The sourcechannels option can be used to set the channel hopping for 
# specific interfaces, and to control what interfaces share a list of 
# channels for split hopping.  This can also be used to easily lock
# one card on a single channel while hopping with other cards.
# Any card without a sourcechannel definition will use the standard hopping
# list.
# sourcechannels=sourcename[,sourcename]:ch1,ch2,ch3,...chN

# ie, for us channels on the source 'prism2source' (same as normal channel
# hopping behavior):
# sourcechannels=prism2source:1,6,11,2,7,3,8,4,9,5,10

# Given two capture sources, "prism2a" and "prism2b", we want prism2a to stay
# on channel 6 and prism2b to hop normally.  By not setting a sourcechannels 
# line for prism2b, it will use the standard hopping.
# sourcechannels=prism2a:6

# To assign the same custom hop channel to multiple sources, or to split the 
# same custom hop channel over two sources (if splitchannels is true), list
# them all on the same sourcechannels line:
# sourcechannels=prism2a,prism2b,prism2c:1,6,11

# Port to serve GUI data
tcpport=2501
# People allowed to connect, comma seperated IP addresses or network/mask
# blocks.  Netmasks can be expressed as dotted quad (/255.255.255.0) or as
# numbers (/24)
allowedhosts=127.0.0.1
# Address to bind to.  Should be an address already configured already on
# this host, reverts to INADDR_ANY if specified incorrectly.
bindaddress=127.0.0.1
# Maximum number of concurrent GUI's
maxclients=5

# Do we have a GPS?
gps=false
# Host:port that GPSD is running on.  This can be localhost OR remote!
gpshost=localhost:2947
# Do we lock the mode?  This overrides coordinates of lock "0", which will
# generate some bad information until you get a GPS lock, but it will 
# fix problems with GPS units with broken NMEA that report lock 0
gpsmodelock=false

# Packet filtering options:
# filter_tracker - Packets filtered from the tracker are not processed or
#                  recorded in any way.
# filter_dump    - Packets filtered at the dump level are tracked, displayed,
#                  and written to the csv/xml/network/etc files, but not 
#                  recorded in the packet dump
# filter_export  - Controls what packets influence the exported CSV, network,
#                  xml, gps, etc files.
# All filtering options take arguments containing the type of address and
# addresses to be filtered.  Valid address types are 'ANY', 'BSSID',
# 'SOURCE', and 'DEST'.  Filtering can be inverted by the use of '!' before
# the address.  For example,
# filter_tracker=ANY(!00:00:DE:AD:BE:EF)
# has the same effect as the previous mac_filter config file option.
# filter_tracker=...
# filter_dump=...
# filter_export=...

# Alerts to be reported and the throttling rates.
# alert=name,throttle/unit,burst/unit
# The throttle/unit describes the number of alerts of this type that are
# sent per time unit.  Valid time units are second, minute, hour, and day.
# Burst rates control the number of packets sent at a time
# For example:
# alert=FOO,10/min,5/sec
# Would allow 5 alerts per second, and 10 alerts total per minute.
# A throttle rate of 0 disables throttling of the alert.
# See the README for a list of alert types.
alert=NETSTUMBLER,10/min,1/sec
alert=WELLENREITER,10/min,1/sec
alert=LUCENTTEST,10/min,1/sec
alert=DEAUTHFLOOD,10/min,2/sec
alert=BCASTDISCON,10/min,2/sec
alert=CHANCHANGE,5/min,1/sec
alert=AIRJACKSSID,5/min,1/sec
alert=PROBENOJOIN,10/min,1/sec
alert=DISASSOCTRAFFIC,10/min,1/sec
alert=NULLPROBERESP,10/min,1/sec
alert=BSSTIMESTAMP,10/min,1/sec
alert=MSFBCOMSSID,10/min,1/sec
alert=LONGSSID,10/min,1/sec
alert=MSFDLINKRATE,10/min,1/sec
alert=MSFNETGEARBEACON,10/min,1/sec
alert=DISCONCODEINVALID,10/min,1/sec
alert=DEAUTHCODEINVALID,10/min,1/sec

# Known WEP keys to decrypt, bssid,hexkey.  This is only for networks where
# the keys are already known, and it may impact throughput on slower hardware.
# Multiple wepkey lines may be used for multiple BSSIDs.
# wepkey=00:DE:AD:C0:DE:00,FEEDFACEDEADBEEF01020304050607080900

# Is transmission of the keys to the client allowed?  This may be a security
# risk for some.  If you disable this, you will not be able to query keys from
# a client.
allowkeytransmit=true

# How often (in seconds) do we write all our data files (0 to disable)
writeinterval=300

# How old (and inactive) does a network need to be before we expire it?
# This is really only good for limited ram environments where keeping a
# total log of all networks is problematic.  This is in seconds, and should
# be set to a large value like 12 or 24 hours.  This is intended for use
# on stationary systems like an IDS
# logexpiry=86400

# Do we limit the number of networks we log?  This is for low-ram situations
# when tracking everything could lead to the system falling down.  This
# should be combined with a sane logexpiry value to flush out very old 
# inactive networks.  This is mainly for stationary systems like an IDS.
# limitnets=10000

# Do we track IVs?  this can help identify some attacks, but takes a LOT
# of memory to do so on a busy network.  If you have the RAM, by all
# means turn it on.
trackivs=false

# Do we use sound?
# Not to be confused with GUI sound parameter, this controls wether or not the
# server itself will play sound.  Primarily for headless or automated systems.
sound=false
# Path to sound player
soundplay=/usr/bin/play
# Optional parameters to pass to the player
# soundopts=--volume=.3
# New network found
sound_new=//usr/share/kismet/wav/new_network.wav
# Wepped new network
# sound_new_wep=${prefix}/com/kismet/wav/new_wep_network.wav
# Network traffic sound
sound_traffic=//usr/share/kismet/wav/traffic.wav
# Network junk traffic found
sound_junktraffic=//usr/share/kismet/wav/junk_traffic.wav
# GPS lock aquired sound
# sound_gpslock=//usr/share/kismet/wav/foo.wav
# GPS lock lost sound
# sound_gpslost=//usr/share/kismet/wav/bar.wav
# Alert sound
sound_alert=//usr/share/kismet/wav/alert.wav

# Does the server have speech? (Again, not to be confused with the GUI's speech)
speech=false
# Server's path to Festival
festival=/usr/bin/festival
# Are we using festival lite?  If so, set the above "festival" path to also
# point to the "flite" binary
flite=false
# Are we using Darwin speech? 
darwinsay=false
# What voice do we use?  (Currently only valid on Darwin)
speech_voice=default
# How do we speak?  Valid options:
# speech    Normal speech
# nato      NATO spellings (alpha, bravo, charlie)
# spell     Spell the letters out (aye, bee, sea)
speech_type=nato
# speech_encrypted and speech_unencrypted - Speech templates
# Similar to the logtemplate option, this lets you customize the speech output.
# speech_encrypted is used for an encrypted network spoken string
# speech_unencrypted is used for an unencrypted network spoken string
#
# %b is replaced by the BSSID (MAC) of the network
# %s is replaced by the SSID (name) of the network
# %c is replaced by the CHANNEL of the network
# %r is replaced by the MAX RATE of the network
speech_encrypted=New network detected, s.s.i.d. %s, channel %c, network encrypted.
speech_unencrypted=New network detected, s.s.i.d. %s, channel %c, network open.

# Where do we get our manufacturer fingerprints from?  Assumed to be in the
# default config directory if an absolute path is not given.
ap_manuf=ap_manuf
client_manuf=client_manuf

# Use metric measurements in the output?
metric=false

# Do we write waypoints for gpsdrive to load?  Note:  This is NOT related to
# recent versions of GPSDrive's native support of Kismet.
waypoints=false
# GPSDrive waypoint file.  This WILL be truncated.
waypointdata=%h/.gpsdrive/way_kismet.txt
# Do we want ESSID or BSSID as the waypoint name ?
waypoint_essid=false

# How many alerts do we backlog for new clients?  Only change this if you have
# a -very- low memory system and need those extra bytes, or if you have a high
# memory system and a huge number of alert conditions.
alertbacklog=50

# File types to log, comma seperated
# dump    - raw packet dump
# network - plaintext detected networks
# csv     - plaintext detected networks in CSV format
# xml     - XML formatted network and cisco log
# weak    - weak packets (in airsnort format)
# cisco   - cisco equipment CDP broadcasts
# gps     - gps coordinates
logtypes=dump,network,csv,xml,weak,cisco,gps

# Do we track probe responses and merge probe networks into their owners?
# This isn't always desireable, depending on the type of monitoring you're
# trying to do.
trackprobenets=true

# Do we log "noise" packets that we can't decipher?  I tend to not, since 
# they don't have anything interesting at all in them.
noiselog=false

# Do we log corrupt packets?  Corrupt packets have enough header information
# to see what they are, but someting is wrong with them that prevents us from
# completely dissecting them.  Logging these is usually not a bad idea.
corruptlog=true

# Do we log beacon packets or do we filter them out of the dumpfile
beaconlog=true

# Do we log PHY layer packets or do we filter them out of the dumpfile
phylog=true

# Do we mangle packets if we can decrypt them or if they're fuzzy-detected
mangledatalog=true

# Do we do "fuzzy" crypt detection?  (byte-based detection instead of 802.11
# frame headers)
# valid option: Comma seperated list of card types to perform fuzzy detection 
#  on, or 'all'
fuzzycrypt=wtapfile,wlanng,wlanng_legacy,wlanng_avs,hostap,wlanng_wext,ipw2200,ipw2915

# Do we do forgiving fuzzy packet decoding?  This lets us handle borked drivers
# which don't indicate they're including FCS, and then do.
fuzzydecode=wtapfile,radiotap_bsd_a,radiotap_bsd_g,radiotap_bsd_bg,radiotap_bsd_b,pcapfile

# Do we use network-classifier fuzzy-crypt detection?  This means we expect 
# packets that are associated with an encrypted network to be encrypted too, 
# and we process them by the same fuzzy compare. 
# This essentially replaces the fuzzycrypt per-source option.
netfuzzycrypt=true

# What type of dump do we generate? 
# valid option: "wiretap" 
dumptype=wiretap
# Do we limit the size of dump logs?  Sometimes ethereal can't handle big ones.
# 0 = No limit
# Anything else = Max number of packets to log to a single file before closing
# and opening a new one.
dumplimit=0

# Do we write data packets to a FIFO for an external data-IDS (such as Snort)?
# See the docs before enabling this.
#fifo=/tmp/kismet_dump

# Default log title
logdefault=Kismet

# logtemplate - Filename logging template.
# This is, at first glance, really nasty and ugly, but you'll hardly ever
# have to touch it so don't complain too much.
#
# %n is replaced by the logging instance name
# %d is replaced by the current date as Mon-DD-YYYY
# %D is replaced by the current date as YYYYMMDD
# %t is replaced by the starting log time
# %i is replaced by the increment log in the case of multiple logs
# %l is replaced by the log type (dump, status, crypt, etc)
# %h is replaced by the home directory
# ie, "netlogs/%n-%d-%i.dump" called with a logging name of "Pok" could expand
# to something like "netlogs/Pok-Dec-20-01-1.dump" for the first instance and 
# "netlogs/Pok-Dec-20-01-2.%l" for the second logfile generated.
# %h/netlots/%n-%d-%i.dump could expand to
# /home/foo/netlogs/Pok-Dec-20-01-2.dump
#
# Other possibilities:  Sorting by directory
# logtemplate=%l/%n-%d-%i
# Would expand to, for example,
# dump/Pok-Dec-20-01-1
# crypt/Pok-Dec-20-01-1
# and so on.  The "dump", "crypt", etc, dirs must exist before kismet is run
# in this case.
logtemplate=/var/log/kismet/%n-%d-%i.%l

# Where do we store the pid file of the server?
piddir=/var/run/

# Where state info, etc, is stored.  You shouldnt ever need to change this.
# This is a directory.
configdir=/var/lib/kismet/

# cloaked SSID file.  You shouldn't ever need to change this.
ssidmap=ssid_map

# Group map file.  You shouldn't ever need to change this.
groupmap=group_map

# IP range map file.  You shouldn't ever need to change this.
ipmap=ip_map
```

With this configuration, I can run kismet simply by typing 'sudo kismet.'  Can you do the same (obviously you'll have to change the 'source' line to rt73, but otherwise everything that worked for me should work for you)?

---

### Post by mike22 on 2008-09-16
nvm I got kismet working on backtrack. I really don't need it on ubuntu.

---

### Post by mike22 on 2008-09-17
Well I fixed the dump file error. I changed the logtemplate in the conf file to /home/usr/. The only problem now is I get this error.

```
FATAL:  Could not connect to localhost:2501.

```


Here is the terminal info when I type in sudo kismet.

```
root@ubuntu:/home# sudo kismet
Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to michael (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (rt73-gpl-cvs): Enabling monitor mode for rt73 source interface wlan1 channel 6...
Source 0 (rt73-gpl-cvs): Opening rt73 source interface wlan1...
Spawned channel control process 1653
Dropped privs to michael (1000) gid 1000
Will attempt to put networkmanager to sleep...
Allowing clients to fetch WEP keys.
Logging networks to /home/michael/Kismet-Sep-17-2008-15.network
Logging networks in CSV format to /home/michael/Kismet-Sep-17-2008-15.csv
Logging networks in XML format to /home/michael/Kismet-Sep-17-2008-15.xml
Logging cryptographically weak packets to /home/michael/Kismet-Sep-17-2008-15.weak
Logging cisco product information to /home/michael/Kismet-Sep-17-2008-15.cisco
Logging gps coordinates to /home/michael/Kismet-Sep-17-2008-15.gps
Logging data to /home/michael/Kismet-Sep-17-2008-15.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from /usr/local/etc/ap_manuf
Reading client manufacturer data and defaults from /usr/local/etc/client_manuf
Using network-classifier based data encryption detection
Not tracking duplicate IVs
Putting networkmanager to sleep...
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2008.05.R1 (Kismet)
Logging data networks CSV XML weak cisco gps
GPSD cannot connect: Connection refused
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Registering builtin client/server protocols...
Registering requested alerts...
Registering builtin timer events...
Gathering packets...
Launching kismet_client: /usr/local/bin/kismet_client
Launched client, pid 1732
FATAL: ** Could not connect to localhost:2501.**
Didn't capture any packets, unlinking dump file
Didn't see any weak encryption packets, unlinking weak file
Sending termination request to channel control child 1653...
Waiting for channel control child 1653 to exit...
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
         restart or reconfigure it for normal operation.
Trying to wake networkmanager back up...
Kismet exiting.
Done.
root@ubuntu:/home# 

 
```

---

### Post by pytheas22 on 2008-09-17
If you run this command:
```

echo '127.0.0.1 localhost.localdomain localhost' | sudo tee -a /etc/hosts
```

then start kismet again, does that fix it?

---

### Post by mike22 on 2008-09-17
I still get;"FATAL:  Could not connect to localhost:2501." Last time I got this error before I edited the logtemplate in kismet.conf, I sipply cd'ed to /home/, and that did the trick. However, when I edited the logtemplate to /home/michael/ then cd'ed to /home/ to start kismet, I get the localhost error. Well here's what my ifconfig looks like:

```
michael@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:72:37:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:b8:72:37:b7  
          inet addr:169.254.8.22  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:220 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91231 (89.0 KB)  TX bytes:91231 (89.0 KB)

wlan1     Link encap:Ethernet  HWaddr 00:21:29:6e:e2:e3  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:29ff:fe6e:e2e3/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:1047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1239573 (1.1 MB)  TX bytes:133416 (130.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-29-6E-E2-E3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by astjohn on 2008-09-19
@mike22

Did you manage to solve this problem?  I'm having similar trouble and have tried everything you have.

---

### Post by pytheas22 on 2008-09-19
Did either of you try googling for the error message, [Could not connect to localhost:2501]("http://www.google.com/search?q=%22Could+not+connect+to+localhost%3A2501.%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a").  There are a few solutions proposed that you might want to try.

(Please note that I'm not telling you to google to be rude or condescending; I just don't have time right now to write out the potential solutions here.)

---

### Post by astjohn on 2008-09-19
Unfortunately, I have tried most of the solutions google can feed me, and I am still waiting for some input from the kismet forums...

I don't want to hijack the thread, but here has been my experience...

Compiled from source.
Using Ubuntu:
2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Added the following to hosts:
```
127.0.0.1 localhost.localdomain localhost
```

Logs are fine.

When I run kismet and kismet_server, i receive the following respectively:

>>kismet

```
Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to adam (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (default): Enabling monitor mode for ipw2200 source interface eth1 channel 6...
Source 0 (default): Opening ipw2200 source interface eth1...
Spawned channel control process 8182
Dropped privs to adam (1000) gid 1000
Will attempt to put networkmanager to sleep...
Allowing clients to fetch WEP keys.
WARNING: Disabling GPS logging.
Logging networks to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-8.network
Logging networks in CSV format to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-8.csv
Logging networks in XML format to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-8.xml
Logging cryptographically weak packets to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-8.weak
Logging cisco product information to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-8.cisco
Logging data to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-8.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from /usr/local/etc/ap_manuf
Reading client manufacturer data and defaults from /usr/local/etc/client_manuf
Using network-classifier based data encryption detection
Not tracking duplicate IVs
Putting networkmanager to sleep...
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2008.05.R1 (Kismet)
Logging data networks CSV XML weak cisco
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Registering builtin client/server protocols...
Registering requested alerts...
Registering builtin timer events...
Gathering packets...
Launching kismet_client: /usr/local/bin/kismet_client
Launched client, pid 8284
FATAL: Could not connect to localhost:2501.
Didn't see any weak encryption packets, unlinking weak file
Sending termination request to channel control child 8182...
Waiting for channel control child 8182 to exit...
WARNING: Sometimes cards don't always come out of monitor mode
cleanly. If your card is not fully working, you may need to
restart or reconfigure it for normal operation.
Trying to wake networkmanager back up...
Kismet exiting.
Done.
```


>>kismet_server

```
Will drop privs to adam (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (default): Enabling monitor mode for ipw2200 source interface eth1 channel 6...
Source 0 (default): Opening ipw2200 source interface eth1...
Spawned channel control process 8727
Dropped privs to adam (1000) gid 1000
Will attempt to put networkmanager to sleep...
Allowing clients to fetch WEP keys.
WARNING: Disabling GPS logging.
Logging networks to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-9.network
Logging networks in CSV format to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-9.csv
Logging networks in XML format to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-9.xml
Logging cryptographically weak packets to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-9.weak
Logging cisco product information to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-9.cisco
Logging data to /home/adam/Documents/kismet-logs/Kismet-Sep-19-2008-9.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from /usr/local/etc/ap_manuf
Reading client manufacturer data and defaults from /usr/local/etc/client_manuf
Using network-classifier based data encryption detection
Not tracking duplicate IVs
Putting networkmanager to sleep...
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2008.05.R1 (Kismet)
Logging data networks CSV XML weak cisco
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Registering builtin client/server protocols...
Registering requested alerts...
Registering builtin timer events...
Gathering packets...
Fri Sep 19 09:51:00 2008 Found new network "SanJuan" bssid 00:1C:F0:F5:6B:F2 Crypt Y Ch 1 @ 11.00 mbit
FATAL: Reading packet from pcap failed, interface is no longer up. Usually this happens when a DHCP client times out and turns off the interface. See the Troubleshooting section of the README for more information.
Terminating.
Didn't see any weak encryption packets, unlinking weak file
Sending termination request to channel control child 8727...
Waiting for channel control child 8727 to exit...
WARNING: Sometimes cards don't always come out of monitor mode
cleanly. If your card is not fully working, you may need to
restart or reconfigure it for normal operation.
Trying to wake networkmanager back up...
Kismet exiting.

```

If I need to disable DHCP, I'm not sure how to.
My interfaces file reads:

```
auto lo
iface lo inet loopback

```


Any help is greatly appreciated.

---

### Post by pytheas22 on 2008-09-19
Have you seen [this page]("http://www.kismetwireless.net/Forum/General/Messages/1218121488.579438")?   It suggests that the error is not actually related to dhcp, but by unexpected behavior on Network Manager's part.  The solution is to open your /etc/kismet/kismet.conf file and change the option 'networkmanagersleep=true' (three or four sections from the top of the file) to 'networkmanagersleep=false'  Then try running kismet again.  Does it help (or at least change the error output at all)?

---

### Post by mike22 on 2008-09-19
Kismet is working. The only problem is that I don't see any networks listed. Appreciate the help.

---

### Post by pytheas22 on 2008-09-19
I've never used kismet that much so I can't really help with troubleshooting inability to see networks.  Are you sure the card is in monitor mode and that it's on the right channel (or hopping channels)?  Can you see networks with airodump-ng (part of the aircrack-ng suite) if you install it:
```

sudo apt-get install aircrack-ng
```

---

### Post by mike22 on 2008-09-19
> **pytheas22 said:**
> I've never used kismet that much so I can't really help with troubleshooting inability to see networks.  Are you sure the card is in monitor mode and that it's on the right channel (or hopping channels)?  Can you see networks with airodump-ng (part of the aircrack-ng suite) if you install it:
```

sudo apt-get install aircrack-ng
```

That's ok, I know what to do now.

---

### Post by Gordi73 on 2008-09-21
Sorry Mike22 i have the same message: 
FATAL: Dump file error: Unable to open dump file Kismet-Sep-21-2008-1.dump (Permission denied)

You say:

Well I fixed the dump file error. I changed the logtemplate in the conf file to /home/usr/. 

can u explain me what did u do? (sorry im a beginner :) )

thnks

---

### Post by mike22 on 2008-10-03
bump. Now I get an error that says that I don't have wlan1 interface

```
michael@ubuntu:~$ kismet
Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to michael (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (rt73-gpl-cvs): Enabling monitor mode for rt73 source interface wlan1 channel 6...
FATAL: GetIFFlags: interface wlan1: No such device
Done.
michael@ubuntu:~$ 



```

---

### Post by pytheas22 on 2008-10-03
Did you check iwconfig to see what your interface is named?  Maybe the name really did change.  If not, trying giving the interface name as 'rt73' instead of 'wlan*'.

---

### Post by mike22 on 2008-10-03
> **pytheas22 said:**
> Did you check iwconfig to see what your interface is named?  Maybe the name really did change.  If not, trying giving the interface name as 'rt73' instead of 'wlan*'.

My interface did change. Here is the iwconfig output:

```
michael@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan2     IEEE 802.11g  ESSID:"network2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:74:CE:BB   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=67/100  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

michael@ubuntu:~$ 


```

Is there any reason why the interface changed?

---

### Post by pytheas22 on 2008-10-03
I'm not sure why it changed, but you should have a file at /etc/modprobe.d/ralink that sets the alias for the device.  Perhaps something modified it for some reason.

---

