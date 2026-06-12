---
title: "Apt proxy gives problems"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by shoaibi on 2008-10-28
Following: [https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)
```

root@aptproxy:~# cat /etc/apt-proxy/apt-proxy-v2.conf 
[DEFAULT]
;; All times are in seconds, but you can add a suffix
;; for minutes(m), hours(h) or days(d)

;; Server IP to listen on
address = 192.168.40.51

;; Server port to listen on
port = 9999

;; Control files (Packages/Sources/Contents) refresh rate
;;
;; Minimum age of a file before it is refreshed
min_refresh_delay = 1h

;; Minimum age of a file before attempting an update (NOT YET IMPLEMENTED)
;min_age = 23h

;; Uncomment to make apt-proxy continue downloading even if all
;; clients disconnect.  This is probably not a good idea on a
;; dial up line.
complete_clientless_downloads = 1

;; Debugging settings.
;; for all debug information use this:
;; debug = all:9
debug = all:4 db:0

;; Debugging remote python console
;; Do not enable in an untrusted environment
;telnet_port = 9998
;telnet_user = apt-proxy
;telnet_password = secret

;; Network timeout when retrieving from backend servers
timeout = 15

;; Cache directory for apt-proxy
cache_dir = /var/cache/apt-proxy

;; Use passive FTP? (default=on)
passive_ftp = on

;; Use HTTP proxy?
;http_proxy = [username:password@]host:port

;; Limit download rate from backend servers (http and rsync only), in bytes/sec
;bandwidth_limit = 100000

;;--------------------------------------------------------------
;; Cache housekeeping

;; Time to perform periodic housekeeping:
;;  - delete files that have not been accessed in max_age
;;  - scan cache directories and update internal tables
cleanup_freq = 1d

;; Maximum age of files before deletion from the cache (seconds)
max_age = 30d

;; Maximum number of versions of a .deb to keep per distribution
max_versions = 3

;; Add HTTP backends dynamicaly if not already defined? (default=on)
dynamic_backends = on

;;---------------------------------------------------------------
;;---------------------------------------------------------------
;; Backend servers
;;
;; Place each server in its own [section]

[ubuntu]
;; Ubuntu archive
backends = http://archive.ubuntu.com/ubuntu
min_refresh_delay = 15m

[ubuntu-security]
;; Ubuntu security updates
backends = http://security.ubuntu.com/ubuntu
min_refresh_delay = 1m

[kubuntu-members-kde]
;; KDE 4 respository.
backends = http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu
min_refresh_delay = 1m

[virtualbox]
;; Virtualbox Repository
backends = http://download.virtualbox.org/virtualbox/debian
min_refresh_delay = 1m

[canonical]
;; Partner Repository
backends = http://archive.canonical.com/ubuntu 
min_refresh_delay = 1m


;[backports.org]
;; backports.org
;backends = http://backports.org/debian
min_refresh_delay = 1d

;[blackdown]
;; Blackdown Java
;backends = http://ftp.gwdg.de/pub/languages/java/linux/debian
min_refresh_delay = 1d

;[debian-people]
;; people.debian.org
;backends = http://people.debian.org

;[emdebian]
;; The Emdebian project
;backends = http://emdebian.sourceforge.net/emdebian

;[rsync]
;; An example using an rsync server.  This is not recommended
;; unless http is not available, becuause rsync is only more
;; efficient for transferring uncompressed files and puts much
;; more overhead on the server.
;backends = rsync://ftp.uk.debian.org/debian

```


[SIZE="3"]**Problem 1**[/SIZE]

Client:
```

shoaibi@paseo:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu-KDE4 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://aptproxy:9999/ubuntu/ hardy main restricted
deb-src http://aptproxy:9999/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://aptproxy:9999/ubuntu/ hardy-updates main restricted
deb-src http://aptproxy:9999/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://aptproxy:9999/ubuntu/ hardy universe
deb-src http://aptproxy:9999/ubuntu/ hardy universe
deb http://aptproxy:9999/ubuntu/ hardy-updates universe
deb-src http://aptproxy:9999/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://aptproxy:9999/ubuntu/ hardy multiverse
deb-src http://aptproxy:9999/ubuntu/ hardy multiverse
deb http://aptproxy:9999/ubuntu/ hardy-updates multiverse
deb-src http://aptproxy:9999/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://aptproxy:9999/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://aptproxy:9999/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://aptproxy:9999/ubuntu hardy partner
# deb-src http://aptproxy:9999/ubuntu hardy partner

deb http://aptproxy:9999/ubuntu/ hardy-security main restricted
deb-src http://aptproxy:9999/ubuntu/ hardy-security main restricted
deb http://aptproxy:9999/ubuntu/ hardy-security universe
deb-src http://aptproxy:9999/ubuntu/ hardy-security universe
deb http://aptproxy:9999/ubuntu/ hardy-security multiverse
deb-src http://aptproxy:9999/ubuntu/ hardy-security multiverse

deb http://aptproxy:9999/kubuntu-members-kde4/ubuntu hardy main
deb http://aptproxy:9999/virtualbox/debian hardy non-free

shoaibi@paseo:~$ cat /etc/apt/apt.conf
Aquire::Proxy "false";
shoaibi@paseo:~$ sudo apt-get update
Get:1 http://aptproxy hardy Release.gpg [189B]
Ign http://aptproxy hardy/main Translation-en_US
Ign http://aptproxy hardy/restricted Translation-en_US
Ign http://aptproxy hardy/universe Translation-en_US
Ign http://aptproxy hardy/multiverse Translation-en_US
Get:2 http://aptproxy hardy-updates Release.gpg [189B]
Ign http://aptproxy hardy-updates/main Translation-en_US
Ign http://aptproxy hardy-updates/restricted Translation-en_US
Ign http://aptproxy hardy-updates/universe Translation-en_US
Ign http://aptproxy hardy-updates/multiverse Translation-en_US
Get:3 http://aptproxy hardy-security Release.gpg [189B]
Ign http://aptproxy hardy-security/main Translation-en_US
Ign http://aptproxy hardy-security/restricted Translation-en_US
Ign http://aptproxy hardy-security/universe Translation-en_US
Ign http://aptproxy hardy-security/multiverse Translation-en_US
98% [Waiting for headers]                                                                                                                                   
shoaibi@paseo:~$ sudo apt-get update
Get:1 http://aptproxy hardy Release.gpg [189B]
Ign http://aptproxy hardy/main Translation-en_US
Ign http://aptproxy hardy/restricted Translation-en_US
Ign http://aptproxy hardy/universe Translation-en_US
Ign http://aptproxy hardy/multiverse Translation-en_US
Get:2 http://aptproxy hardy-updates Release.gpg [189B]
Ign http://aptproxy hardy-updates/main Translation-en_US
Ign http://aptproxy hardy-updates/restricted Translation-en_US
Ign http://aptproxy hardy-updates/universe Translation-en_US
Ign http://aptproxy hardy-updates/multiverse Translation-en_US
Get:3 http://aptproxy hardy-security Release.gpg [189B]
Ign http://aptproxy hardy-security/main Translation-en_US
Ign http://aptproxy hardy-security/restricted Translation-en_US
Ign http://aptproxy hardy-security/universe Translation-en_US
Ign http://aptproxy hardy-security/multiverse Translation-en_US
Err http://aptproxy hardy Release.gpg
  Bad header line
Err http://aptproxy hardy/main Translation-en_US
  Bad header line
Err http://aptproxy hardy Release.gpg
  Bad header line
Ign http://aptproxy hardy/non-free Translation-en_US
Ign http://aptproxy hardy Release
Ign http://aptproxy hardy-updates Release
Hit http://aptproxy hardy-security Release
95% [Waiting for headers] 

```
and then it takes years...
 and shows:
```

Hit http://aptproxy hardy-security/main Packages
Hit http://aptproxy hardy-security/restricted Packages
Hit http://aptproxy hardy-security/main Sources
Hit http://aptproxy hardy-security/restricted Sources
Hit http://aptproxy hardy-security/universe Packages
Hit http://aptproxy hardy-security/universe Sources
Hit http://aptproxy hardy-security/multiverse Packages
Hit http://aptproxy hardy-security/multiverse Sources
Ign http://aptproxy hardy/main Packages
Ign http://aptproxy hardy/non-free Packages
Err http://aptproxy hardy/main Packages
  Bad header line
Err http://aptproxy hardy/non-free Packages
  404 file not found on backend
Fetched 567B in 4min23s (2B/s)
W: Failed to fetch http://aptproxy:9999/kubuntu-members-kde4/ubuntu/dists/hardy/Release.gpg  Bad header line

W: Failed to fetch http://aptproxy:9999/kubuntu-members-kde4/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Bad header line

W: Failed to fetch http://aptproxy:9999/virtualbox/debian/dists/hardy/Release.gpg  Bad header line

W: Failed to fetch http://aptproxy:9999/kubuntu-members-kde4/ubuntu/dists/hardy/main/binary-i386/Packages.gz  Bad header line

W: Failed to fetch http://aptproxy:9999/virtualbox/debian/dists/hardy/non-free/binary-i386/Packages.gz  404 file not found on backend

E: Some index files failed to download, they have been ignored, or old ones used instead.
shoaibi@paseo:~$ 

```

[SIZE="3"]**Problem 2**[/SIZE]

```

root@aptproxy:~# apt-proxy-import -r /var/cache/apt/archives
2008/10/17 17:14 +0600 [-] Log opened.
2008/10/17 17:14 +0600 [-] [import] Importing packages from directory tree: /var/cache/apt/archives
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] initramfs-tools_0.85eubuntu39.2_all.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] apt-proxy_1.9.36.1ubuntu1_all.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] python-twisted-web_0.7.0-1build1_all.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] klibc-utils_1.5.7-4ubuntu4_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] python-twisted-core_2.5.0-2build2_all.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] mount_2.13.1-5ubuntu2_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] util-linux-locales_2.13.1-5ubuntu2_all.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] libdbus-1-3_1.1.20-1ubuntu3.1_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] python-twisted-bin_2.5.0-2build2_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] bsdutils_1%3a2.13.1-5ubuntu2_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] libldap-2.4-2_2.4.9-0ubuntu0.8.04.1_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] procps_1%3a3.2.7-5ubuntu3_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] python-apt_0.7.4ubuntu7_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] python-zopeinterface_3.3.1-5ubuntu2_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] libpam0g_0.99.7.1-5ubuntu6.1_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] python2.5_2.5.2-2ubuntu4.1_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] bash_3.2-0ubuntu18_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] logrotate_3.7.1-3_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] python-central_0.6.7ubuntu0.1_all.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] python2.5-minimal_2.5.2-2ubuntu4.1_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] iproute_20071016-2ubuntu2_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] eject_2.1.5-6ubuntu1_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] libgnutls13_2.0.4-1ubuntu2.1_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] pciutils_1%3a2.2.4-1.1ubuntu5_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] cron_3.0pl1-100ubuntu2_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] dpkg_1.14.16.6ubuntu4_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] libpam-modules_0.99.7.1-5ubuntu6.1_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [import] Ignoring (unknown file type):lock
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] libpam-runtime_0.99.7.1-5ubuntu6.1_all.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] base-files_4.0.1ubuntu5.8.04.2_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] libklibc_1.5.7-4ubuntu4_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] util-linux_2.13.1-5ubuntu2_i386.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2008/10/17 17:14 +0600 [-] [apt_pkg] No Packages files available for ubuntu backend
2008/10/17 17:14 +0600 [-] [import] tzdata_2008g-0ubuntu0.8.04_all.deb skipped - no suitable backend found
2008/10/17 17:14 +0600 [-] [log] Imported 0 files

```


PS:
If you think its a repost, read again, somethings have changed, plus there were no replies addressing this problem on previous thread.

---

### Post by shoaibi on 2008-11-03
no responses? strange, really strange...

---

### Post by corneil on 2008-11-03
:confused:
Experiencing same problem tried using previous version of apt and excluded apt-proxy entries from sources. All kinds of weird conditions.

---

### Post by Archmage on 2008-12-25
I seem to have the same problem. This someone find a solution for this?

---

### Post by m00ndancer on 2008-12-29
There are a few things you should make a few changes:

First comment out the ip number on your server so it  will listen to all connections to it;

```
;; Server IP to listen on
;; address = 192.168.40.51
```

It could be that the server have problems with the DNS.
Same thing with the client config. Do not use a computer name of the server, use the IP. It's a hassle if you dont have the server configured with a static ip. But other than that it should work.

I have a Apple G3 and a G4 configured like this and it should work.
I also added the closest backend server (sweden for me) in the apt-proxy config to make sure I have no timeouts:

```
[ubuntu]
;; Ubuntu archive
backends = http://se.archive.ubuntu.com/ubuntu
backends = http://archive.ubuntu.com/ubuntu
min_refresh_delay = 15m
```

---

### Post by nelskurian on 2009-03-18
I have the same problem in Intrepid with the latest updates. Anybody their...

---

### Post by shoaibi on 2009-03-18
@nelskurian
I diched aptproxy and went for aptcacher.

@kisi1227:
spammer? :P

---

### Post by nelskurian on 2009-03-18
> **shoaibi said:**
> @nelskurian
I diched aptproxy and went for aptcacher.

@kisi1227:
spammer? :P
need to check it..

---

### Post by shoaibi on 2009-03-18
@nelskurian:
Try it, it easy, and less buggy. Let me know if you get into problems with apt-cache, i have tore it inside out.

---

### Post by nelskurian on 2009-03-18
> **shoaibi said:**
> @nelskurian:
Try it, it easy, and less buggy. Let me know if you get into problems with apt-cache, i have tore it inside out.
thanks a lot dude..:popcorn:

---

### Post by matt.w.franzen on 2009-03-20
Don't know if you still are having problems or have moved to apt-catcher or not...  

I believe there is a bug with the import process to import your existing packages.  For me, not a huge deal, I just re-downloaded everything, though it does kinda seem silly!

Also looking at your 'failed to fetch' lines...  

(from your apt-proxy-v2.conf file)
[kubuntu-members-kde]
;; KDE 4 respository.
backends = [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)
min_refresh_delay = 1m

(from your sources.list file)
deb [http://aptproxy:9999/kubuntu-members-kde4/ubuntu](http://aptproxy:9999/kubuntu-members-kde4/ubuntu) hardy main

It looks like you are referring to the same place twice...  I think you would just need to change your sources.list file to read:
[http://aptproxy:9999/kubuntu-members-kde](http://aptproxy:9999/kubuntu-members-kde) hardy main

I dunno for sure.  I'm having problems getting some third-party sources to update, myself.  But you may luck out! :-)

---

### Post by nelskurian on 2009-03-20
> **matt.w.franzen said:**
> Don't know if you still are having problems or have moved to apt-catcher or not...  

I believe there is a bug with the import process to import your existing packages.  For me, not a huge deal, I just re-downloaded everything, though it does kinda seem silly!

Also looking at your 'failed to fetch' lines...  

(from your apt-proxy-v2.conf file)
[kubuntu-members-kde]
;; KDE 4 respository.
backends = [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)
min_refresh_delay = 1m

(from your sources.list file)
deb [http://aptproxy:9999/kubuntu-members-kde4/ubuntu](http://aptproxy:9999/kubuntu-members-kde4/ubuntu) hardy main

It looks like you are referring to the same place twice...  I think you would just need to change your sources.list file to read:
[http://aptproxy:9999/kubuntu-members-kde](http://aptproxy:9999/kubuntu-members-kde) hardy main

I dunno for sure.  I'm having problems getting some third-party sources to update, myself.  But you may luck out! :-)

I just moved to to apt-cacher,as it seems to be more easy.I go through many bug reports and forums referring the apt-proxy problem,i dont get any feasible solution.Now i seriously concern about your views...
  To  avoid the re-caching  i was looking for the import cache..It seems to more time taken as the ubuntu server is busy always.Changing the source.list is in client side.I am checking to import the previous apt-cache to the newly created apt-proxy.These are not huge deals...But lost good time by checking these.. :o

---

### Post by HankB on 2009-04-16
> **shoaibi said:**
> @nelskurian:
Try it, it easy, and less buggy. Let me know if you get into problems with apt-cache, i have tore it inside out.

Yes, in fact I do. I've installed apt-cacher 0.1 on an X86_64 6.06 LTS host and configured an 8.10 system to use it. It seems to pick up the packages just fine, but when it comes to actually fetching the files, the proxy seems not to be passing them along to the client. With debug turned on, I see in the server log:


```

Thu Apr 16 08:45:46 2009|127.0.1.1|debug [6317]: new filename with just basename: linux-image-2.6.27-14-generic_2.6.27-14.33_amd64.deb
Thu Apr 16 08:45:46 2009|127.0.1.1|debug [6317]: looking for /var/cache/apt-cacher/packages/linux-image-2.6.27-14-generic_2.6.27-14.33_amd64.deb
Thu Apr 16 08:45:46 2009|127.0.1.1|debug [6317]: Entering critical section : file download decission
Thu Apr 16 08:45:46 2009|127.0.1.1|debug [6317]: Exiting critical section
Thu Apr 16 08:45:46 2009|127.0.1.1|debug [6317]: checks done, can return now

```

The file actually exists in the cache from a previous execution. In the client, I get:
```
The following packages will be upgraded:
  fakeroot ghostscript ghostscript-x gs-common gs-esp gs-esp-x libgs8 libvolume-id0 linux-generic linux-headers-2.6.27-14
  linux-headers-2.6.27-14-generic linux-headers-generic linux-image-2.6.27-14-generic linux-image-generic linux-libc-dev
  linux-restricted-modules-generic nvidia-common tzdata tzdata-java udev
20 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.8MB of archives.
After this operation, 20.5kB disk space will be freed.
Do you want to continue [Y/n]? 
Err http://oak intrepid-proposed/main linux-image-2.6.27-14-generic 2.6.27-14.33
  500 (Internal Server Error) read timeout
```

Is this a known problem with the v 0.1 apt-cacher or is there the possibility that I have something misconfigured?

thanks,
hank

---

