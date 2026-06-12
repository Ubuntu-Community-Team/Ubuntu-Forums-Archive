---
title: "Find mac on LAN from Lubuntu"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by Driger on 2013-05-20
Hi all,

So I dont know where to look in Lubuntu to see computers that are connected to the same network I am.

for example, there are 3 macs in the house that are all connected to eachother. on those computers there is just a little side bar in the finder that shows other computers connected (my lubuntu netbook shows up but doesnt connect) so where can I see their computers?

---

### Post by MG&amp;TL on 2013-05-21
I don't know exactly how the apple communication protocol works, but I'm not sure whether it's supported in Ubuntu.

It depends on what you want to do with the computers once you can 'see' them. Share files, printers, remote access?

---

### Post by Driger on 2013-05-21
I am interested in sharing files. I tried using afpfs-ng to connect with the afp adress but I either entered it wrong or it didnt work.

---

### Post by sanderj on 2013-05-21
Maybe this helps: [http://www.raspberrypi.org/phpBB3/viewtopic.php?f=66&t=18207](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=66&t=18207)

---

### Post by Driger on 2013-05-26
[FONT=verdana]Sanderj that helped,[/FONT][FONT=Helvetica Neue][COLOR=#333333][FONT=verdana] I think I am closer to finally figuring this out.I tried to ping the macbook i want to acess but this is what I got[/FONT]
[/COLOR][/FONT]```
scott@netbookV2:~$ ping -c 4 Sanjas-MacBook.local
ping: unknown host Sanjas-MacBook.local

```[FONT=Helvetica Neue][COLOR=#333333]

[FONT=verdana]And when I type in "[/FONT][/COLOR][/FONT][COLOR=#333333][FONT=Helvetica Neue][FONT=verdana]avahi-discover" to the terminal I only see my own computer :([/FONT]


[/FONT][/COLOR]

---

### Post by Driger on 2013-05-26
[FONT=verdana]Oh I didn't notice but there was an error that happened when I put "sudo apt-get install libnss-mdns" to the terminal. 

Maybe that's why it isn't working?

[/FONT]```
scott@netbookV2:~$ sudo apt-get install libnss-mdns
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnss-mdns is already the newest version.
The following packages were automatically installed and are no longer required:
  libkcmutils4 libnepomukdatamanagement4 libclucene0ldbl gstreamer0.10-alsa
  libqca2 kde-l10n-de libkdegames5a libutempter0 libkdeclarative5 libkjsembed4
  mplayer-skins libsvga1 oxygen-icon-theme libkemoticons4 libkdecore5 phonon
  libkidletime4 docbook-xml docbook-xsl libx86-1 shared-desktop-ontologies
  libdlrestrictions1 kde-l10n-engb libntrack-qt4-1 libkatepartinterfaces4
  bluefish-plugins libsolid4 virtuoso-minimal bluefish-data libkde3support4
  libnepomuk4 libkdewebkit5 libsoprano4 libpolkit-qt-1-1 libkdnssd4 libkparts4
  libqapt1 kdoctools libvirtodbc0 libdbusmenu-qt2 kde-l10n-zhcn mythes-en-au
  katepart libthreadweaver4 libnepomukutils4 libkmediaplayer4
  openoffice.org-hyphenation libntrack0 libkfile4 libknewstuff3-4
  libqapt-runtime phonon-backend-gstreamer libkpty4 hyphen-en-us
  libnepomuksync4 libstreamanalyzer0 libphonon4 libknotifyconfig4 mythes-de-ch
  libkntlm4 xul-ext-ubufox libplasma3 kdelibs-bin libktexteditor4 sgml-data
  libkio5 libkjsapi4 libstreams0 libxml2-utils libattica0.3
  virtuoso-opensource-6.1-common plasma-scriptengine-javascript soprano-daemon
  libkhtml5 libkdeui5 libkdesu5 virtuoso-opensource-6.1-bin kate-data
  ntrack-module-libnl-0 libkrosscore4 libnepomukquery4a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by GuenterErde on 2013-05-26
have you tried using nslookup? Or i mean honestly, you could do ifconfig, get the default gateways ip address, log into it by pluging it's IP address as a URL in a browser, and checking there.

---

### Post by cariboo on 2013-05-26
You can find the other systems connected to you network, including ip and MAC addresses using nmap, it's in the repositories. Use the following command:

```
sudo nmap -sP 192.168.0.0/24
```

substitute your netblock for the one in the command give. The result should look similar to this:

```
sudo nmap -sP 192.168.0.0/24
[sudo] password for cariboo: 

Starting Nmap 6.00 ( http://nmap.org ) at 2013-05-26 19:49 PDT
Nmap scan report for 192.168.0.1
Host is up (0.00014s latency).
MAC Address: 00:00:00:00:00:00 (D-Link International)
Nmap scan report for 192.168.0.100
Host is up (0.21s latency).
MAC Address: 00:00:00:00:00:00 (Asustek Computer)
Nmap scan report for 192.168.0.101
Host is up (0.0025s latency).
MAC Address: 00:00:00:00:00:00 (Sling Media)
Nmap scan report for 192.168.0.102
Host is up.
Nmap scan report for willy (192.168.0.104)
Host is up (0.00011s latency).
MAC Address: 00:00:00:00:00:00 (Micro-star Int'l Co.)
Nmap scan report for 192.168.0.109
Host is up (0.00081s latency).
MAC Address: 00:00:00:00:00:00 (Brother Industries)
Nmap scan report for 192.168.0.113
Host is up (0.00030s latency).
MAC Address: 00:00:00:00:00:00 (VD Division, Samsung Electronics Co.)
Nmap done: 256 IP addresses (7 hosts up) scanned in 4.07 seconds
```

I've removed tha mac addresses to protect the innocent. :)

---

### Post by Driger on 2013-05-29
[SIZE=2][FONT=verdana]Okay I used nmap and I have something like what you got!!! (except devices all are (unknown))

This may be a very noob question but how do I access files from that computer now that I see it with nmap?

@GuenterErde; after I hit ifconfig what number is my default gateway ip address?
[/FONT][/SIZE]

---

