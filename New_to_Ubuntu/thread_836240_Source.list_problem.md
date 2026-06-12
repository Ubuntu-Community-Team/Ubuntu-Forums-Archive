---
title: "Source.list problem"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by KristofferAndreas on 2008-06-21
Hi

First sorry for my bad english!

Second I have a little problem with my updater and package manager...
for some time ago i added this recomended sources to my list [http://oshelpdesk.org/?page_id=355](http://oshelpdesk.org/?page_id=355)
(my current list is in the bottom of this post...)

everything worked fine, but yesterday i went into the source.list file and removed all the # before some off the sources... 
Now i get 
*[PHP]'E:Type 'sudo' is not known on line 111 in source list /etc/apt/sources.list, E:The list of sources could not be read.'[/PHP]*
when i start update manager and i get:
[I][PHP]defekt@zalo3:~$ sudo apt-get update
E: Type 'sudo' is not known on line 111 in source list /etc/apt/sources.list
defekt@zalo3:~$ [/PHP][/I]
when i try to refresh in console...

and one more thing the reason is because i want to install most off the programs from this list:
[I][PHP]#!/bin/sh
# SCRIPT TO AUTO DOWNLOAD AND UPDATE
# BACKTRACK TOOLS ON UBUNTU LINUX
# V1.0 TEST VERSION

#1 Tools Found on BackTrack 2.0 Final

#1.1 Information Gathering
apt-get install ***
apt-get install DMitry
apt-get install DNS-Ptr
apt-get install dnswalk
apt-get install dns-bruteforce
apt-get install dnsenum
apt-get install dnsmap
apt-get install DNSPredict
apt-get install Finger Google
apt-get install Firewalk
apt-get install Goog Mail Enum
apt-get install Google-search
apt-get install Googrape
apt-get install Gooscan
apt-get install Host
apt-get install Itrace
apt-get install Netenum
apt-get install Netmask
apt-get install Pirana
apt-get install Protos
apt-get install QGoogle
apt-get install Relay Scanner
apt-get install SMTP-Vrfy
apt-get install TCtrace

#1.2 Network Mapping
apt-get install Amap 5.2
apt-get install ***
apt-get install Autoscan 0.99_R1
apt-get install Fping
apt-get install Hping
apt-get install IKE-Scan
apt-get install IKEProbe
apt-get install Netdiscover
apt-get install Nmap
apt-get install NmapFE
apt-get install P0f
apt-get install PSK-Crack
apt-get install Ping
apt-get install Protos
apt-get install Scanrand
apt-get install SinFP
apt-get install Umit
apt-get install UnicornScan
apt-get install UnicornScan pgsql 0.4.6e module version 1.03
apt-get install XProbe2
apt-get install PBNJ 2.04
apt-get install OutputPBNJ
apt-get install ScanPBNJ
apt-get install Genlist

#1.3 Vulnerability Identification
apt-get install Absinthe
apt-get install Bed
apt-get install CIRT Fuzzer
apt-get install Checkpwd
apt-get install Cisco Auditing Tool
apt-get install Cisco Enable Bruteforcer
apt-get install Cisco Global Exploiter
apt-get install Cisco OCS Mass Scanner
apt-get install Cisco Scanner
apt-get install Cisco Torch
apt-get install Curl
apt-get install Fuzzer 1.2
apt-get install GFI LanGuard 2.0
apt-get install GetSids
apt-get install HTTP PUT
apt-get install Halberd
apt-get install Httprint
apt-get install Httprint GUI
apt-get install ISR-Form
apt-get install Jbrofuzz
apt-get install List-Urls
apt-get install Lynx
apt-get install Merge Router Config
apt-get install Metoscan
apt-get install Mezcal HTTP/S
apt-get install Mibble MIB Browser
apt-get install Mistress
apt-get install Nikto
apt-get install OAT
apt-get install Onesixtyone
apt-get install OpenSSL-Scanner
apt-get install Paros Proxy
apt-get install Peach
apt-get install RPCDump
apt-get install RevHosts
apt-get install SMB Bruteforcer
apt-get install SMB Client
apt-get install SMB Serverscan
apt-get install SMB-NAT
apt-get install SMBdumpusers
apt-get install SMBgetserverinfo
apt-get install SNMP Scanner
apt-get install SNMP Walk
apt-get install SQL Inject
apt-get install SQL Scanner
apt-get install SQLLibf
apt-get install SQLbrute
apt-get install Sidguess
apt-get install Smb4K
apt-get install Snmpcheck
apt-get install Snmp Enum
apt-get install Spike
apt-get install Stompy
apt-get install SuperScan
apt-get install TNScmd
apt-get install Taof
apt-get install VNC_bypauth
apt-get install Wapiti
apt-get install Yersinia
apt-get install sqlanlz
apt-get install sqldict
apt-get install sqldumplogins
apt-get install sqlquery
apt-get install sqlupload

#1.4 Penetration

apt-get install Framework3-MsfC
apt-get install Framework3-MsfUpdate
apt-get install Framework3-Msfcli
apt-get install Framework3-Msfweb
apt-get install Init Pgsql (autopwn)
apt-get install Milw0rm Archive
apt-get install MsfCli
apt-get install MsfConsole
apt-get install MsfUpdate
apt-get install OpenSSL-To-Open
apt-get install Update Milw0rm
apt-get install Privilege Escalation
apt-get install Ascend attacker
apt-get install CDP Spoofer
apt-get install Cisco Enable Bruteforcer
apt-get install Crunch Dictgen
apt-get install DHCPX Flooder
apt-get install DNSspoof
apt-get install Driftnet
apt-get install Dsniff
apt-get install Etherape
apt-get install EtterCap
apt-get install File2Cable
apt-get install HSRP Spoofer
apt-get install Hash Collision
apt-get install Httpcapture
apt-get install Hydra
apt-get install Hydra GTK
apt-get install ICMP Redirect
apt-get install ICMPush
apt-get install IGRP Spoofer
apt-get install IRDP Responder
apt-get install IRDP Spoofer
apt-get install John
apt-get install Lodowep
apt-get install Mailsnarf
apt-get install Medusa
apt-get install Msgsnarf
apt-get install Nemesis Spoofer
apt-get install NetSed
apt-get install Netenum
apt-get install Netmask
apt-get install Ntop
apt-get install PHoss
apt-get install PackETH
apt-get install Rcrack
apt-get install SIPdump
apt-get install SMB Sniffer
apt-get install Sing
apt-get install TFTP-Brute
apt-get install THC PPTP
apt-get install TcPick
apt-get install URLsnarf
apt-get install VNCrack
apt-get install WebCrack
apt-get install Wireshark
apt-get install Wireshark Wifi
apt-get install WyD
apt-get install XSpy
apt-get install chntpw

#1.6 Maintaining Access
apt-get install 1.6.1 3proxy

#1.6.2 Backdoors
apt-get install CryptCat
apt-get install HttpTunnel Client
apt-get install HttpTunnel Server
apt-get install ICMPTX
apt-get install Iodine
apt-get install NSTX
apt-get install Privoxy
apt-get install ProxyTunnel
apt-get install Rinetd
apt-get install TinyProxy
apt-get install sbd
apt-get install socat

#Covering Tracks
apt-get install Housekeeping

#1.8 Radio Network Analysis#
#1.8.1 802.11
apt-get install AFrag
apt-get install ASLeap
apt-get install Air Crack
apt-get install Air Decap
apt-get install Air Replay
apt-get install Airmon Script
apt-get install Airpwn
apt-get install AirSnarf
apt-get install Airodump
apt-get install Airoscript
apt-get install Airsnort
apt-get install CowPatty
apt-get install FakeAP
apt-get install GenKeys
apt-get install Genpmk
apt-get install Hotspotter
apt-get install Karma
apt-get install Kismet
apt-get install Load IPW3945
apt-get install Load acx100
apt-get install MDK2
apt-get install MDK2 for Broadcom
apt-get install MacChanger
apt-get install Unload Drivers
apt-get install Wep_crack
apt-get install Wep_decrypt
apt-get install WifiTap
apt-get install Wicrawl
apt-get install Wlassistant

#Bluetooth
apt-get install Bluebugger
apt-get install Blueprint
apt-get install Bluesnarfer
apt-get install Btscanner
apt-get install Carwhisperer
apt-get install CuteCom
apt-get install Ghettotooth
apt-get install HCIDump
apt-get install Ussp-Push

#1.9 VOIP & Telephony Analysis
apt-get install PcapSipDump
apt-get install PcapToSip_RTP
apt-get install SIPSak
apt-get install SIPcrack
apt-get install SIPdump
apt-get install SIPp
apt-get install Smap

#1.10 Digital Forensics
apt-get install Allin1
apt-get install Autopsy
apt-get install DCFLDD
apt-get install DD_Rescue
apt-get install Foremost
apt-get install Magicrescue
apt-get install Mboxgrep
apt-get install Memfetch
apt-get install Memfetch Find
apt-get install Pasco
apt-get install Rootkithunter
apt-get install Sleuthkit
apt-get install Vinetto

#1.11 Reverse Engineering
apt-get install GDB GNU Debugger
apt-get install GDB Console GUI
apt-get install GDB Server
apt-get install GNU DDD
apt-get install Hexdump
apt-get install Hexedit
apt-get install OllyDBG

#Services
apt-get install snort

#EXTRA NOT IN BACKTRACK
apt-get install tcpflow
apt-get install tcptrace
apt-get install tcpreplay
apt-get install tcpick
apt-get install ssldump
apt-get install aircrack-ng #alrady included[/PHP][/I]

i can copy the [http://oshelpdesk.org/?page_id=355](http://oshelpdesk.org/?page_id=355) list and do everything again exept the last part. 
and does anyone now where i can find the sources for this program list?


here is the source list im using now:
[I][PHP]
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://no.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://no.archive.ubuntu.com/ubuntu/ hardy universe
deb http://no.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://no.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://no.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://no.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse





##### Ubuntu 8.04 LTS &#8220;Hardy Heron&#8221;

### Ubuntu Standard-Quellen
deb http://de.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse

##### Zusätzliche Paketquellen
## Fremdpakete können das System beschädigen

## Canonical&#8217;s &#8216;partner&#8217; repository
deb http://archive.canonical.com/ hardy partner
deb-src http://archive.canonical.com/ hardy partner
deb http://archive.canonical.com/ hardy-backports partner
deb-src http://archive.canonical.com/ hardy-backports partner
deb http://archive.canonical.com/ hardy-proposed partner
deb-src http://archive.canonical.com/ hardy-proposed partner
deb http://archive.canonical.com/ hardy-security partner
deb-src http://archive.canonical.com/ hardy-security partner
deb http://archive.canonical.com/ hardy-updates partner
deb-src http://archive.canonical.com/ hardy-updates partner

## Ubuntu Debug Packages
# https://wiki.ubuntu.com/DebuggingProgramCrash
deb http://ddebs.ubuntu.com hardy main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-updates main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-proposed main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-security main restricted universe multiverse

## Medibuntu
# Please report any bug on https://bugs.launchpad.net/medibuntu/
# wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O-
# sudo apt-key add - && sudo apt-get update
deb http://packages.medibuntu.org/ hardy non-free free
deb http://packages.medibuntu.org/ hardy-staging non-free free
deb-src http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy-staging free non-free

## ubuntu.geole.info
sudo apt-get install geole-keyring
deb http://ubuntu.geole.info/ hardy universe multiverse
deb-src http://ubuntu.geole.info/ hardy universe multiverse
deb http://ubuntu.geole.info/ hardy-backports main restricted universe multiverse
deb-src http://ubuntu.geole.info/ hardy-backports main restricted universe multiverse

## Morgoth Repository
# wget http://morgoth.free.fr/files/morgoth-signkey.gpg.asc -O- | sudo apt-key add -
######## i386-Architecture only!!!
deb http://morgoth.free.fr/ubuntu hardy-backports main
deb-src http://morgoth.free.fr/ubuntu hardy-backports main

## The Ubuntu NLP Repository (GPG key: 8ABD1965)
wget http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg -O- | sudo apt-key add -
deb http://cl.naist.jp/~eric-n/ubuntu-nlp hardy all
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp hardy all

## Le dépomaniak repository (GPG key: 1D59E694)
wget http://ubuntu.davromaniak.eu/1D59E694.gpg -O- | sudo apt-key add -
deb http://ubuntu.davromaniak.eu hardy-depomaniak all
deb-src http://ubuntu.davromaniak.eu hardy-depomaniak all

## Iuculano&#8217;s debian packages (GPG key: AE3BE9AA)
wget http://ubuntu.iuculano.it/AE3BE9AA.gpg -O- | sudo apt-key add -
deb http://ubuntu.iuculano.it hardy all
deb-src http://ubuntu.iuculano.it hardy all

deb http://wicd.longren.org hardy all

## Upstream Scribus package repository
gpg &#8211;keyserver wwwkeys.eu.pgp.net &#8211;recv-keys EEF818CF && gpg &#8211;armor &#8211;export EEF818CF | sudo apt-key add -
deb http://debian.scribus.net/debian/ hardy main
deb-src http://debian.scribus.net/debian/ hardy main
deb http://debian.scribus.net/debian/ hardy non-free
deb-src http://debian.scribus.net/debian/ hardy non-free

## wxWidgets/wxPython repository at apt.wxwidgets.org
wget -q http://apt.wxwidgets.org/key.asc -O- | sudo apt-key add -
deb http://apt.wxwidgets.org/ hardy-wx main
deb-src http://apt.wxwidgets.org/ hardy-wx main

deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main restricted
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy universe multiverse

## 5-a-day
deb http://ppa.launchpad.net/5-a-day/ubuntu hardy main

## Audacious 1.5.0
deb http://ppa.launchpad.net/sebner/ubuntu hardy main
deb-src http://ppa.launchpad.net/sebner/ubuntu hardy main

# Bug-Helper
deb http://ppa.launchpad.net/bughelper-dev/ubuntu hardy main

## Jbbr Ubuntu repository, http://ubuntu.jbbr.net
wget -q http://ubuntu.jbbr.net/jbbr_ubuntu.asc -O- | sudo apt-key add -
deb http://ubuntu.jbbr.net/packages hardy main
deb-src http://ubuntu.jbbr.net/packages hardy main

## Swiftfox Browser
deb http://getswiftfox.com/builds/debian unstable non-free

## Bleeding edge wine packages
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main

## Opera
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera/ sid non-free
deb http://deb.opera.com/opera-beta/ sid non-free
deb http://deb.opera.com/opera/ stable non-free
deb http://deb.opera.com/opera/ testing non-free
deb http://deb.opera.com/opera/ unstable non-free

## Elisa Debian Packages
http://elisa.fluendo.com
wget http://elisa.fluendo.com/packages/philn.asc -O - | sudo apt-key add -
deb http://elisa.fluendo.com/packages hardy main

## Elbuntu
wget -O - http://lut1n.ifrance.com/repo_key.asc | sudo apt-key add -
deb http://e17.dunnewind.net/ubuntu hardy e17

## Gnome-Do
deb http://ppa.launchpad.net/do-core/ubuntu hardy main

## Amorok
deb http://ppa.launchpad.net/project-neon/ubuntu hardy main restricted multiverse universe

## Debian Multimedia
Key: sudo apt-get install debian-multimedia-keyring
deb http://www.debian-multimedia.org sid main
deb http://www.debian-multimedia.org lenny main
deb http://www.debian-multimedia.org experimental main
deb-src http://www.debian-multimedia.org sid main

## Schmidtke-Repository
## Inhalt: http://ubuntu.schmidtke-hb.de/
wget ubuntu.schmidtke-hb.de/aptrepository.asc
sudo apt-key add aptrepository.asc
deb http://apt.schmidtke-hb.de hardy main universe multiverse
deb-src http://apt.schmidtke-hb.de hardy main universe multiverse

## Cafuego&#8217;s Hardy Stuff(GPG key: 969F3F57)
# wget http://debian.cafuego.net/AF425CB5.gpg -O- | sudo apt-key add -
deb http://au.ubuntu.cafuego.net hardy-cafuego all
deb-src http://au.ubuntu.cafuego.net hardy-cafuego all

## CinnamonPirate.com Repository
wget http://repository.cinnamonpirate.com/arrr.gpg -O- | sudo apt-key add -
deb http://repository.cinnamonpirate.com/ hardy pirate

## gambas2
deb http://azores.linex.org/gambas-other hardy main

## My Media System
deb http://www.prodeia.de/mms/hardy binary/

deb http://hydr0g3n.free.fr/qbittorrent/hardy/ ./

# FreeNX-Server für Ubuntu Hardy
deb http://www.datakeylive.com/ubuntu hardy main

# Mugshot
wget -q http://www.nighton.net/nighton_key.asc -O- | sudo apt-key add -
deb http://www.nighton.net/ hardy main

### Google desktop
wget https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ testing non-free

deb http://packages.aaron-spettl.de hardy-pidgin/


##### Ubuntu 8.04 LTS &#8220;Hardy Heron&#8221;

### Ubuntu Standard-Quellen
deb http://de.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse

##### Zusätzliche Paketquellen
## Fremdpakete können das System beschädigen

## Canonical&#8217;s &#8216;partner&#8217; repository
deb http://archive.canonical.com/ hardy partner
deb-src http://archive.canonical.com/ hardy partner
deb http://archive.canonical.com/ hardy-backports partner
deb-src http://archive.canonical.com/ hardy-backports partner
deb http://archive.canonical.com/ hardy-proposed partner
deb-src http://archive.canonical.com/ hardy-proposed partner
deb http://archive.canonical.com/ hardy-security partner
deb-src http://archive.canonical.com/ hardy-security partner
deb http://archive.canonical.com/ hardy-updates partner
deb-src http://archive.canonical.com/ hardy-updates partner

## Ubuntu Debug Packages
# https://wiki.ubuntu.com/DebuggingProgramCrash
deb http://ddebs.ubuntu.com hardy main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-updates main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-proposed main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-security main restricted universe multiverse

## Medibuntu
# Please report any bug on https://bugs.launchpad.net/medibuntu/
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O-
sudo apt-key add - && sudo apt-get update
deb http://packages.medibuntu.org/ hardy non-free free
deb http://packages.medibuntu.org/ hardy-staging non-free free
deb-src http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy-staging free non-free

## ubuntu.geole.info
sudo apt-get install geole-keyring
deb http://ubuntu.geole.info/ hardy universe multiverse
deb-src http://ubuntu.geole.info/ hardy universe multiverse
deb http://ubuntu.geole.info/ hardy-backports main restricted universe multiverse
deb-src http://ubuntu.geole.info/ hardy-backports main restricted universe multiverse

## Morgoth Repository
wget http://morgoth.free.fr/files/morgoth-signkey.gpg.asc -O- | sudo apt-key add -
######## i386-Architecture only!!!
deb http://morgoth.free.fr/ubuntu hardy-backports main
deb-src http://morgoth.free.fr/ubuntu hardy-backports main

## The Ubuntu NLP Repository (GPG key: 8ABD1965)
wget http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg -O- | sudo apt-key add -
deb http://cl.naist.jp/~eric-n/ubuntu-nlp hardy all
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp hardy all

## Le dépomaniak repository (GPG key: 1D59E694)
wget http://ubuntu.davromaniak.eu/1D59E694.gpg -O- | sudo apt-key add -
deb http://ubuntu.davromaniak.eu hardy-depomaniak all
deb-src http://ubuntu.davromaniak.eu hardy-depomaniak all

## Iuculano&#8217;s debian packages (GPG key: AE3BE9AA)
wget http://ubuntu.iuculano.it/AE3BE9AA.gpg -O- | sudo apt-key add -
deb http://ubuntu.iuculano.it hardy all
deb-src http://ubuntu.iuculano.it hardy all

deb http://wicd.longren.org hardy all

## Upstream Scribus package repository
gpg &#8211;keyserver wwwkeys.eu.pgp.net &#8211;recv-keys EEF818CF && gpg &#8211;armor &#8211;export EEF818CF | sudo apt-key add -
deb http://debian.scribus.net/debian/ hardy main
deb-src http://debian.scribus.net/debian/ hardy main
deb http://debian.scribus.net/debian/ hardy non-free
deb-src http://debian.scribus.net/debian/ hardy non-free

## wxWidgets/wxPython repository at apt.wxwidgets.org
wget -q http://apt.wxwidgets.org/key.asc -O- | sudo apt-key add -
deb http://apt.wxwidgets.org/ hardy-wx main
deb-src http://apt.wxwidgets.org/ hardy-wx main

deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main restricted
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy universe multiverse

## 5-a-day
deb http://ppa.launchpad.net/5-a-day/ubuntu hardy main

## Audacious 1.5.0
deb http://ppa.launchpad.net/sebner/ubuntu hardy main
deb-src http://ppa.launchpad.net/sebner/ubuntu hardy main

# Bug-Helper
deb http://ppa.launchpad.net/bughelper-dev/ubuntu hardy main

## Jbbr Ubuntu repository, http://ubuntu.jbbr.net
wget -q http://ubuntu.jbbr.net/jbbr_ubuntu.asc -O- | sudo apt-key add -
deb http://ubuntu.jbbr.net/packages hardy main
deb-src http://ubuntu.jbbr.net/packages hardy main

## Swiftfox Browser
deb http://getswiftfox.com/builds/debian unstable non-free

## Bleeding edge wine packages
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main

## Opera
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera/ sid non-free
deb http://deb.opera.com/opera-beta/ sid non-free
deb http://deb.opera.com/opera/ stable non-free
deb http://deb.opera.com/opera/ testing non-free
deb http://deb.opera.com/opera/ unstable non-free

## Elisa Debian Packages
http://elisa.fluendo.com
wget http://elisa.fluendo.com/packages/philn.asc -O - | sudo apt-key add -
deb http://elisa.fluendo.com/packages hardy main

## Elbuntu
 wget -O - http://lut1n.ifrance.com/repo_key.asc | sudo apt-key add -
deb http://e17.dunnewind.net/ubuntu hardy e17

## Gnome-Do
deb http://ppa.launchpad.net/do-core/ubuntu hardy main

## Amorok
deb http://ppa.launchpad.net/project-neon/ubuntu hardy main restricted multiverse universe

## Debian Multimedia
Key: sudo apt-get install debian-multimedia-keyring
deb http://www.debian-multimedia.org sid main
deb http://www.debian-multimedia.org lenny main
deb http://www.debian-multimedia.org experimental main
deb-src http://www.debian-multimedia.org sid main

## Schmidtke-Repository
## Inhalt: http://ubuntu.schmidtke-hb.de/
wget ubuntu.schmidtke-hb.de/aptrepository.asc
sudo apt-key add aptrepository.asc
deb http://apt.schmidtke-hb.de hardy main universe multiverse
deb-src http://apt.schmidtke-hb.de hardy main universe multiverse

## Cafuego&#8217;s Hardy Stuff(GPG key: 969F3F57)
wget http://debian.cafuego.net/AF425CB5.gpg -O- | sudo apt-key add -
deb http://au.ubuntu.cafuego.net hardy-cafuego all
deb-src http://au.ubuntu.cafuego.net hardy-cafuego all

## CinnamonPirate.com Repository
wget http://repository.cinnamonpirate.com/arrr.gpg -O- | sudo apt-key add -
deb http://repository.cinnamonpirate.com/ hardy pirate

## gambas2
deb http://azores.linex.org/gambas-other hardy main

## My Media System
deb http://www.prodeia.de/mms/hardy binary/

deb http://hydr0g3n.free.fr/qbittorrent/hardy/ ./

# FreeNX-Server für Ubuntu Hardy
deb http://www.datakeylive.com/ubuntu hardy main

# Mugshot
wget -q http://www.nighton.net/nighton_key.asc -O- | sudo apt-key add -
deb http://www.nighton.net/ hardy main

### Google desktop
wget https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ testing non-free

deb http://packages.aaron-spettl.de hardy-pidgin/


##### Ubuntu 8.04 LTS &#8220;Hardy Heron&#8221;

### Ubuntu Standard-Quellen
deb http://de.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse

##### Zusätzliche Paketquellen
## Fremdpakete können das System beschädigen

## Canonical&#8217;s &#8216;partner&#8217; repository
deb http://archive.canonical.com/ hardy partner
deb-src http://archive.canonical.com/ hardy partner
deb http://archive.canonical.com/ hardy-backports partner
deb-src http://archive.canonical.com/ hardy-backports partner
deb http://archive.canonical.com/ hardy-proposed partner
deb-src http://archive.canonical.com/ hardy-proposed partner
deb http://archive.canonical.com/ hardy-security partner
deb-src http://archive.canonical.com/ hardy-security partner
deb http://archive.canonical.com/ hardy-updates partner
deb-src http://archive.canonical.com/ hardy-updates partner

## Ubuntu Debug Packages
# https://wiki.ubuntu.com/DebuggingProgramCrash
deb http://ddebs.ubuntu.com hardy main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-updates main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-proposed main restricted universe multiverse
deb http://ddebs.ubuntu.com hardy-security main restricted universe multiverse

## Medibuntu
# Please report any bug on https://bugs.launchpad.net/medibuntu/
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O-
# sudo apt-key add - && sudo apt-get update
deb http://packages.medibuntu.org/ hardy non-free free
deb http://packages.medibuntu.org/ hardy-staging non-free free
deb-src http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy-staging free non-free


## ubuntu.geole.info
sudo apt-get install geole-keyring
deb http://ubuntu.geole.info/ hardy universe multiverse
deb-src http://ubuntu.geole.info/ hardy universe multiverse
deb http://ubuntu.geole.info/ hardy-backports main restricted universe multiverse
deb-src http://ubuntu.geole.info/ hardy-backports main restricted universe multiverse

## Morgoth Repository
wget http://morgoth.free.fr/files/morgoth-signkey.gpg.asc -O- | sudo apt-key add -
######## i386-Architecture only!!!
deb http://morgoth.free.fr/ubuntu hardy-backports main
deb-src http://morgoth.free.fr/ubuntu hardy-backports main

## The Ubuntu NLP Repository (GPG key: 8ABD1965)
wget http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg -O- | sudo apt-key add -
deb http://cl.naist.jp/~eric-n/ubuntu-nlp hardy all
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp hardy all

## Le dépomaniak repository (GPG key: 1D59E694)
wget http://ubuntu.davromaniak.eu/1D59E694.gpg -O- | sudo apt-key add -
deb http://ubuntu.davromaniak.eu hardy-depomaniak all
deb-src http://ubuntu.davromaniak.eu hardy-depomaniak all

## Iuculano&#8217;s debian packages (GPG key: AE3BE9AA)
wget http://ubuntu.iuculano.it/AE3BE9AA.gpg -O- | sudo apt-key add -
deb http://ubuntu.iuculano.it hardy all
deb-src http://ubuntu.iuculano.it hardy all

deb http://wicd.longren.org hardy all

## Upstream Scribus package repository
gpg &#8211;keyserver wwwkeys.eu.pgp.net &#8211;recv-keys EEF818CF && gpg &#8211;armor &#8211;export EEF818CF | sudo apt-key add -
deb http://debian.scribus.net/debian/ hardy main
deb-src http://debian.scribus.net/debian/ hardy main
deb http://debian.scribus.net/debian/ hardy non-free
deb-src http://debian.scribus.net/debian/ hardy non-free

## wxWidgets/wxPython repository at apt.wxwidgets.org
wget -q http://apt.wxwidgets.org/key.asc -O- | sudo apt-key add -
deb http://apt.wxwidgets.org/ hardy-wx main
deb-src http://apt.wxwidgets.org/ hardy-wx main

deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main restricted
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy universe multiverse

## 5-a-day
deb http://ppa.launchpad.net/5-a-day/ubuntu hardy main

## Audacious 1.5.0
deb http://ppa.launchpad.net/sebner/ubuntu hardy main
deb-src http://ppa.launchpad.net/sebner/ubuntu hardy main

# Bug-Helper
deb http://ppa.launchpad.net/bughelper-dev/ubuntu hardy main

## Jbbr Ubuntu repository, http://ubuntu.jbbr.net
wget -q http://ubuntu.jbbr.net/jbbr_ubuntu.asc -O- | sudo apt-key add -
deb http://ubuntu.jbbr.net/packages hardy main
deb-src http://ubuntu.jbbr.net/packages hardy main

## Swiftfox Browser
deb http://getswiftfox.com/builds/debian unstable non-free

## Bleeding edge wine packages
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main

## Opera
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera/ sid non-free
deb http://deb.opera.com/opera-beta/ sid non-free
deb http://deb.opera.com/opera/ stable non-free
deb http://deb.opera.com/opera/ testing non-free
deb http://deb.opera.com/opera/ unstable non-free

## Elisa Debian Packages
# http://elisa.fluendo.com
wget http://elisa.fluendo.com/packages/philn.asc -O - | sudo apt-key add -
deb http://elisa.fluendo.com/packages hardy main

## Elbuntu
wget -O - http://lut1n.ifrance.com/repo_key.asc | sudo apt-key add -
deb http://e17.dunnewind.net/ubuntu hardy e17

## Gnome-Do
deb http://ppa.launchpad.net/do-core/ubuntu hardy main

## Amorok
deb http://ppa.launchpad.net/project-neon/ubuntu hardy main restricted multiverse universe

## Debian Multimedia
# Key: sudo apt-get install debian-multimedia-keyring
deb http://www.debian-multimedia.org sid main
deb http://www.debian-multimedia.org lenny main
deb http://www.debian-multimedia.org experimental main
deb-src http://www.debian-multimedia.org sid main

## Schmidtke-Repository
## Inhalt: http://ubuntu.schmidtke-hb.de/
wget ubuntu.schmidtke-hb.de/aptrepository.asc
sudo apt-key add aptrepository.asc
deb http://apt.schmidtke-hb.de hardy main universe multiverse
deb-src http://apt.schmidtke-hb.de hardy main universe multiverse

## Cafuego&#8217;s Hardy Stuff(GPG key: 969F3F57)
wget http://debian.cafuego.net/AF425CB5.gpg -O- | sudo apt-key add -
deb http://au.ubuntu.cafuego.net hardy-cafuego all
deb-src http://au.ubuntu.cafuego.net hardy-cafuego all

## CinnamonPirate.com Repository
wget http://repository.cinnamonpirate.com/arrr.gpg -O- | sudo apt-key add -
deb http://repository.cinnamonpirate.com/ hardy pirate

## gambas2
deb http://azores.linex.org/gambas-other hardy main

## My Media System
deb http://www.prodeia.de/mms/hardy binary/

deb http://hydr0g3n.free.fr/qbittorrent/hardy/ ./

# FreeNX-Server für Ubuntu Hardy
deb http://www.datakeylive.com/ubuntu hardy main

# Mugshot
wget -q http://www.nighton.net/nighton_key.asc -O- | sudo apt-key add -
deb http://www.nighton.net/ hardy main

### Google desktop
wget https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ testing non-free

deb http://packages.aaron-spettl.de hardy-pidgin/ [/PHP][/I]


TH U very much for help!

Kristoffer

---

### Post by Het Irv on 2008-06-21
If you go down your sources list there is a line in there under ubuntu.geole.info that I don't think should be there
```
sudo apt-get install geole-keyring
```
You should also comment out the wget lines, as they will cause errors also.

---

### Post by KristofferAndreas on 2008-06-21
thx duude!

im norwegian and my english isnt that good, 
Comment out does that mean that i must put a # so the program think of it as a comment:P sound rigth?

---

### Post by NilsE on 2008-06-21
> **KristofferAndreas said:**
> thx duude!

im norwegian and my english isnt that good, 
Comment out does that mean that i must put a # so the program think of it as a comment:P sound rigth?
Yes, 2 #'s to be consistent in front of the line.  Since the line will never work you can just delete it also.

---

### Post by Het Irv on 2008-06-21
Yeah, the lines that start with "sudo" and "wget" are supposed to be run in the terminal by themselves.

---

### Post by KristofferAndreas on 2008-06-21
every thing works again now! thanks guys!

Anybody who knows where to get sources i can use with the backtrack script*?:P

---

