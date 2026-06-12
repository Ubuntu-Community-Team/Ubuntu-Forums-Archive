---
title: "error with sudo-ldap package"
date: 2023-04-15
forum: Packaging and Compiling Programs
---

### Post by tuxor2 on 2023-04-15
Hi,
I am new to the forum but not a totally beginner of Ubuntu.
I just installed a minimized Ubuntu server 22.04 to make an LDAP directory for centralized authentication with sudoers.

I have a problem with the sudo-ldap package. The installation does not  work and there seem to be missing files, especially the **schema.OpenLDAP**  file needed to manage sudoers with openldap.

I specify that I temporarily PermitRootLogin with SSH and put a password on root account.


```

root@SL120:~# apt-get install sudo-ldap
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  sudo
The following NEW packages will be installed:
  sudo-ldap
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 859 kB of archives.
After this operation, 86.0 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://fr.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 sudo-ldap amd64 1.9.9-1ubuntu2.4 [859 kB]
Fetched 859 kB in 1s (880 kB/s)         
debconf: delaying package configuration, since apt-utils is not installed
dpkg: sudo: dependency problems, but removing anyway as you requested:
 ubuntu-server-minimal depends on sudo.

(Reading database ... 67185 files and directories currently installed.)
Removing sudo (1.9.9-1ubuntu2.4) ...
Selecting previously unselected package sudo-ldap.
(Reading database ... 67124 files and directories currently installed.)
Preparing to unpack .../sudo-ldap_1.9.9-1ubuntu2.4_amd64.deb ...
Unpacking sudo-ldap (1.9.9-1ubuntu2.4) ...
Setting up sudo-ldap (1.9.9-1ubuntu2.4) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78.)
debconf: falling back to frontend: Readline
Scanning processes...                                                                                                                                                   
Scanning linux images...                                                                                                                                                

Running kernel seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.

```


and to illustrate my point
```

root@SL120:~# dpkg -V sudo-ldap
missing     /usr/share/doc/sudo-ldap/CONTRIBUTING.md
missing     /usr/share/doc/sudo-ldap/CONTRIBUTORS.md.gz
missing     /usr/share/doc/sudo-ldap/HISTORY.md
missing     /usr/share/doc/sudo-ldap/NEWS.Debian.gz
missing     /usr/share/doc/sudo-ldap/NEWS.gz
missing     /usr/share/doc/sudo-ldap/OPTIONS
missing     /usr/share/doc/sudo-ldap/README.LDAP.md.gz
missing     /usr/share/doc/sudo-ldap/README.md
missing     /usr/share/doc/sudo-ldap/SECURITY.md
missing     /usr/share/doc/sudo-ldap/TROUBLESHOOTING.md.gz
missing     /usr/share/doc/sudo-ldap/UPGRADE.md.gz
missing     /usr/share/doc/sudo-ldap/examples/cvtsudoers.conf
missing     /usr/share/doc/sudo-ldap/examples/pam.conf
missing     /usr/share/doc/sudo-ldap/examples/sudo.conf
missing     /usr/share/doc/sudo-ldap/examples/sudo_logsrvd.conf
missing     /usr/share/doc/sudo-ldap/examples/sudoers
missing     /usr/share/doc/sudo-ldap/examples/sudoers.dist
missing     /usr/share/doc/sudo-ldap/examples/syslog.conf
missing     /usr/share/doc/sudo-ldap/schema.ActiveDirectory.gz
missing     /usr/share/doc/sudo-ldap/schema.OpenLDAP
missing     /usr/share/doc/sudo-ldap/schema.iPlanet
missing     /usr/share/doc/sudo-ldap/schema.olcSudo
missing     /usr/share/man/man1/cvtsudoers.1.gz
missing     /usr/share/man/man5/sudo.conf.5.gz
missing     /usr/share/man/man5/sudo_logsrv.proto.5.gz
missing     /usr/share/man/man5/sudo_logsrvd.conf.5.gz
missing     /usr/share/man/man5/sudoers.5.gz
missing     /usr/share/man/man5/sudoers.ldap.5.gz
missing     /usr/share/man/man5/sudoers_timestamp.5.gz
missing     /usr/share/man/man8/sudo.8.gz
missing     /usr/share/man/man8/sudo_logsrvd.8.gz
missing     /usr/share/man/man8/sudo_plugin.8.gz
missing     /usr/share/man/man8/sudo_root.8.gz
missing     /usr/share/man/man8/sudo_sendlog.8.gz
missing     /usr/share/man/man8/sudoreplay.8.gz
missing     /usr/share/man/man8/visudo.8.gz
missing     /usr/share/man/man8/sudoedit.8.gz

```


An idea ??

Thanks by advance :)

---

### Post by tuxor2 on 2023-04-16
I'm not a newbie but i need to learn read !!!

```

...
debconf: delaying package configuration, since apt-utils is not installed
dpkg: sudo: dependency problems, but removing anyway as you requested:
 ubuntu-server-minimal depends on sudo.
...

```


I fresh install a new Ubuntu server (not minimized) and my sudo-ldap package is correctly installing.



SHAME !! :-?

APOLOGIZE :p

---

