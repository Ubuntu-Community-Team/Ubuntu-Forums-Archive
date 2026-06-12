---
title: "Importing Apt-cache to apt-proxy-cache problem and crontab"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by shoaibi on 2008-10-17
I have an apt-proxy server, I just updated it. and then I ran the command to get archives from local /var/apt/cache, but it didn't import any thing, why? 
Here are the config files and the command with its output:

```

root@aptproxy:~# cat /etc/apt/sources.list
#
#  /etc/apt/sources.list
#
#
# hardy
#
deb     http://archive.ubuntu.com/ubuntu     hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu     hardy main restricted universe
deb     http://archive.ubuntu.com/ubuntu     hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu     hardy-updates main restricted universe
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe

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


Plus:
I have this crontab:
```

# m h  dom mon dow   command
0 3 * * * apt-get update && apt-get dist-upgrade
0 6 * * * apt-proxy-import -r /var/cache/apt/archives

```

is it right? (not syntax wise, logic wise, will it break down something?)

coz on irc i got:
> 
not a good idea to do, but you could set up a cron job to run apt-get update&&apt-get dist-upgrade,   you will break your system fast doing it


---

### Post by kpkeerthi on 2008-10-17
You can't put apt-get dist-upgrade in crontab coz this command will prompt for user input (Yes / No question) that cannot be answered when run from crontab.

Also performing an unattended system upgrade is risky and you will not know when caused the breakage, if any. 

I suggest you use ```
apt-get -d -y dist-upgrade
``` This will only download the updates to  /var/cache/apt/archives which you can later install using ```
apt-get dist-upgrade
```

-d Download only
-y Assume yes for questions prompted

---

### Post by shoaibi on 2008-10-17
okay, i have done that...
but whats the difference between
```

sudo apt-get upgrade

```
and
```

sudo apt-get dist-upgrade

```

plus i am getting this on some machines when i do apt-get update:
```

Err http://aptproxy hardy Release.gpg
  Bad header line
Err http://aptproxy hardy/main Translation-en_US
  Bad header line
Err http://aptproxy hardy Release.gpg
  Bad header line

Err http://aptproxy hardy/main Packages
  Bad header line
99% [Waiting for headers]
Err http://aptproxy hardy/non-free Packages
  Connection failed
Fetched 567B in 2min18s (4B/s)
W: Failed to fetch http://aptproxy:9999/kubuntu-members-kde4/ubuntu/dists/hardy/Release.gpg  Bad header line

W: Failed to fetch http://aptproxy:9999/kubuntu-members-kde4/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Bad header line

W: Failed to fetch http://aptproxy:9999/virtualbox/debian/dists/hardy/Release.gpg  Bad header line

W: Failed to fetch http://aptproxy:9999/kubuntu-members-kde4/ubuntu/dists/hardy/main/binary-i386/Packages.gz  Bad header line

W: Failed to fetch http://aptproxy:9999/virtualbox/debian/dists/hardy/non-free/binary-i386/Packages.gz  Connection failed

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

why is that?

for kubuntu-members-kde4 and virtual box, may be coz my apt-proxy conf file doesn't contain that, BUT i have dynamic_backends set to true, isn't it?

to adress "Bad Header" i used: [https://help.ubuntu.com/community/AptProxy#Problems%20with%20acquiring%20packages](https://help.ubuntu.com/community/AptProxy#Problems%20with%20acquiring%20packages) 's solution, but apt.conf didn't have anything.... still i added what the page suggested and facing same errors...


Plus the main question is there:
Why couldnt apt-proxy import apt cache files to its cache?

---

### Post by kpkeerthi on 2008-10-17
There was discussion in this forum about the difference between the two. Or ```
man apt-get
``` should give you more info on that.

No idea about the other problem.

---

### Post by shoaibi on 2008-10-27
Some one to address the other problem?

---

