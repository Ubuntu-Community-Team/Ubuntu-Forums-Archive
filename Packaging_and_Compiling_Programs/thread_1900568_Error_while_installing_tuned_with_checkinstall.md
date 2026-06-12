---
title: "Error while installing tuned with checkinstall"
date: 2011-12-26
forum: Packaging and Compiling Programs
---

### Post by kr0n1x on 2011-12-26
Hi, I wanted to install tuned (I wanted to try it since my battery, on Ubuntu, is 1 hour shorter or more :| ), I found it here: [https://fedorahosted.org/tuned/](https://fedorahosted.org/tuned/)

I downloaded it with git and I read the INSTALL file. It only tells me to do a make install. So I tried 'sudo checkinstall' but it gives me an error.

```
pasqoo@5742zg:~/tuned$ sudo checkinstall
[sudo] password for pasqoo: 

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           Questo software è rilasciato sotto i termini della licenza GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: n

*****************************************
**** Debian package creation selected ***
*****************************************

Il pacchetto verrà costruito con le seguenti caratteristiche: 

0 -  Maintainer: [ root@5742zg ]
1 -  Summary: [ A dynamic adaptive system tuning daemon
Disk and net statistic monitoring systemtap scripts ]
2 -  Name:    [ tuned ]
3 -  Version: [ 0.2.21 ]
4 -  Release: [ 1%{?dist} ]
5 -  License: [ GPL ]
6 -  Group:   [ System Environment/Daemons
Applications/System ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ tuned ]
9 -  Alternate source location: [  ]
10 - Requires: [ usermode ethtool udev
chkconfig
chkconfig
initscripts
initscripts
systemtap ]
11 - Provides: [ tuned ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Inserisci il corrispondente numero per cambiare una caratteristica (seguito da INVIO) oppure premere INVIO per continuare: 4               
Inserisci un nuovo numero di rilascio: 
>> 1

Il pacchetto verrà costruito con le seguenti caratteristiche: 

0 -  Maintainer: [ root@5742zg ]
1 -  Summary: [ A dynamic adaptive system tuning daemon
Disk and net statistic monitoring systemtap scripts ]
2 -  Name:    [ tuned ]
3 -  Version: [ 0.2.21 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ System Environment/Daemons
Applications/System ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ tuned ]
9 -  Alternate source location: [  ]
10 - Requires: [ usermode ethtool udev
chkconfig
chkconfig
initscripts
initscripts
systemtap ]
11 - Provides: [ tuned ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Inserisci il corrispondente numero per cambiare una caratteristica (seguito da INVIO) oppure premere INVIO per continuare: 

Installing with make install...

========================= Risultato installazione ===========================
mkdir -p /
# Install the binaries
mkdir -p //usr/sbin/
install -m 0755 tuned //usr/sbin/
install -m 0755 tuned-adm //usr/sbin/
# Install the consolehelper files
mkdir -p //etc/pam.d/
install -m 0644 tuned-adm.pam //etc/pam.d/tuned-adm
mkdir -p //etc/security/console.apps/
install -m 0644 tuned-adm.consolehelper //etc/security/console.apps/tuned-adm
mkdir -p //usr/bin/
ln -s consolehelper //usr/bin/tuned-adm
# Install the plugins and classes
mkdir -p //usr/share/tuned/
mkdir -p //usr/share/tuned/tuningplugins
mkdir -p //usr/share/tuned/monitorplugins
install -m 0644 tuned.py //usr/share/tuned/
install -m 0644 tuned_adm.py //usr/share/tuned/
install -m 0644 tuned_nettool.py //usr/share/tuned/
install -m 0644 tuned_logging.py //usr/share/tuned/
for file in tuningplugins/cpu.py tuningplugins/disk.py tuningplugins/net.py tuningplugins/__init__.py; do \
		install -m 0644 $file //usr/share/tuned/tuningplugins; \
	done
for file in monitorplugins/cpu.py monitorplugins/disk.py monitorplugins/net.py monitorplugins/__init__.py; do \
		install -m 0644 $file //usr/share/tuned/monitorplugins; \
	done
# Install contrib systemtap scripts
for file in contrib/diskdevstat contrib/netdevstat contrib/scomes contrib/varnetload; do \
		install -m 0755 $file //usr/sbin/; \
	done
# Install config file
mkdir -p //etc
ln -s /etc/tune-profiles/default/tuned.conf //etc/tuned.conf
mkdir -p //etc/tune-profiles/
# Install manpages
mkdir -p //usr/share/man/man8
install -m 0644 doc/tuned.8 //usr/share/man/man8
install -m 0644 doc/diskdevstat.8 //usr/share/man/man8
install -m 0644 doc/netdevstat.8 //usr/share/man/man8
install -m 0644 doc/scomes.8 //usr/share/man/man8
install -m 0644 doc/varnetload.8 //usr/share/man/man8
mkdir -p //usr/share/man/man5
install -m 0644 doc/tuned.conf.5 //usr/share/man/man5
mkdir -p //usr/share/man/man1
install -m 0644 doc/tuned-adm.1 //usr/share/man/man1
# Install ktune configuration
install -m 755 -d //etc
install -m 755 -d //etc/ktune.d
install -m 755 -d //etc/sysconfig
ln -s /etc/tune-profiles/default/ktune.sysconfig //etc/sysconfig/ktune
ln -s /etc/tune-profiles/default/sysctl.ktune //etc/ktune.d/tunedadm.conf
# Install tune-profiles
install -m 755 -d //etc/tune-profiles
cp -a tune-profiles/* //etc/tune-profiles
cp: preservati gli orari di "//etc/tune-profiles/default": File o directory non esistente
cp: preservati gli orari di "//etc/tune-profiles/desktop-powersave": File o directory non esistente
cp: preservati gli orari di "//etc/tune-profiles/enterprise-storage": File o directory non esistente
cp: preservati gli orari di "//etc/tune-profiles/laptop-ac-powersave": File o directory non esistente
cp: preservati gli orari di "//etc/tune-profiles/laptop-battery-powersave": File o directory non esistente
cp: preservati gli orari di "//etc/tune-profiles/latency-performance": File o directory non esistente
cp: preservati gli orari di "//etc/tune-profiles/server-powersave": File o directory non esistente
cp: preservati gli orari di "//etc/tune-profiles/spindown-disk": File o directory non esistente
cp: preservati gli orari di "//etc/tune-profiles/throughput-performance": File o directory non esistente
make: *** [install-base] Errore 1

****  Installazione fallita. Creazione del paccheto annullata.

Pulitura in corso...OK

Ciao.

pasqoo@5742zg:~/tuned$
```

What can I do to solve it?

Thanks

---

### Post by kr0n1x on 2011-12-29
up ;)

---

