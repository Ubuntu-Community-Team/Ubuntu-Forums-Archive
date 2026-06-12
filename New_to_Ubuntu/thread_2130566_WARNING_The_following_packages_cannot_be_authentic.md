---
title: "WARNING: The following packages cannot be authenticated!"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by nestoru on 2013-03-29
This is happening to us in a server with the below signature:

```
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

We have run the commands presented here as well as many other tweaks we have found on the web without luck. Could you please help troubleshooting this issue? We want to keep installing the security patches automatically via CRON-APT but that is failing specifically:

$ sudo  /usr/bin/apt-get -o quiet=1 upgrade -u -y -o APT::Get::Show-Upgraded=true
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  accountsservice apparmor apport apport-symptoms apt apt-transport-https apt-utils aptitude base-files bind9-host busybox-initramfs
  busybox-static coreutils cron dbus dmsetup dnsutils dpkg gnupg gpgv grub-common grub-pc grub-pc-bin grub2-common hdparm
  initramfs-tools initramfs-tools-bin initscripts iptables isc-dhcp-client isc-dhcp-common krb5-locales landscape-common
  language-pack-en language-pack-en-base language-selector-common libaccountsservice0 libapt-inst1.4 libapt-pkg4.12 libbind9-80
  libdbus-1-3 libdbus-glib-1-2 libdevmapper1.02.1 libdns81 libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libexpat1 libgc1c2
  libgcrypt11 libglib2.0-0 libgnutls-openssl27 libgnutls26 libgssapi-krb5-2 libisc83 libisccc80 libisccfg82 libk5crypto3 libkrb5-3
  libkrb5support0 liblwres80 libneon27-gnutls libnih-dbus1 libnih1 libparted0debian1 libpciaccess0 libplymouth2 libpolkit-gobject-1-0
  libpython2.7 libsasl2-2 libsasl2-modules libsqlite3-0 libssl-dev libssl-doc libssl1.0.0 libtasn1-3 libudev0 libwbclient0 libxcb1
  libxml2 linux-firmware linux-libc-dev login lsb-base lsb-release man-db mountall multiarch-support ntfs-3g ntpdate openssl parted
  passwd perl perl-base perl-modules plymouth plymouth-theme-ubuntu-text psmisc python-apport python-crypto python-gi python-keyring
  python-problem-report python2.7 python2.7-minimal resolvconf rsyslog samba-common samba-common-bin sudo sysv-rc sysvinit-utils tzdata
  ubuntu-keyring ubuntu-minimal ubuntu-standard udev update-manager-core update-notifier-common upstart vim vim-common vim-runtime
  vim-tiny wpasupplicant xkb-data
128 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 88.4 MB of archives.
After this operation, 750 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  base-files sysvinit-utils sysv-rc libdbus-1-3 libdrm2 libpciaccess0 libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 hdparm libudev0
  libdevmapper1.02.1 initramfs-tools initramfs-tools-bin busybox-initramfs dmsetup libglib2.0-0 plymouth libplymouth2 mountall
  initscripts udev libnih-dbus1 libnih1 lsb-base passwd upstart cron dpkg coreutils login perl perl-base perl-modules libapt-pkg4.12
  ubuntu-keyring gpgv gnupg apt libssl-doc libssl-dev libssl1.0.0 libapt-inst1.4 libsqlite3-0 ntpdate resolvconf apparmor libpython2.7
  python2.7 python2.7-minimal libexpat1 dbus libdbus-glib-1-2 accountsservice libaccountsservice0 libpolkit-gobject-1-0
  language-selector-common libgcrypt11 libtasn1-3 libgnutls-openssl27 libgnutls26 libk5crypto3 libgssapi-krb5-2 libkrb5-3
  libkrb5support0 libparted0debian1 libsasl2-modules libsasl2-2 libxcb1 libxml2 ntfs-3g language-pack-en language-pack-en-base
  libwbclient0 update-notifier-common multiarch-support tzdata apt-utils isc-dhcp-client isc-dhcp-common lsb-release rsyslog sudo vim
  vim-tiny vim-runtime vim-common ubuntu-minimal xkb-data apt-transport-https dnsutils bind9-host libisc83 libdns81 libisccc80
  libisccfg82 liblwres80 libbind9-80 busybox-static iptables krb5-locales man-db openssl parted plymouth-theme-ubuntu-text psmisc
  python-gi ubuntu-standard update-manager-core python-problem-report python-apport apport apport-symptoms aptitude grub-pc grub-pc-bin
  grub2-common grub-common landscape-common libgc1c2 libneon27-gnutls linux-firmware linux-libc-dev python-crypto python-keyring
  samba-common samba-common-bin wpasupplicant
E: There are problems and -y was used without --force-yes
```


Thanks!
- Nestor

---

### Post by oldos2er on 2013-03-29
Post moved to its own thread.

---

### Post by msidnam on 2013-04-03
I am also interested if anyone has a solution.

---

### Post by ibjsb4 on 2013-04-03
Got some hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+following+packages+cannot+be+authenticated&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+following+packages+cannot+be+authenticated&sa=Search&cof=FORID:9)

---

### Post by wildmanne39 on 2013-04-03
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ibjsb4 on 2013-04-03
> **Wild Man said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

```
Ok
```

---

### Post by d0006 on 2013-04-04
This pretty much spells it out:
[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by schragge on 2013-04-04
Looks like some */var/lib/apt/lists/*_Release.gpg* files got corrupted. Remove them, then run *apt-get update*:
```

sudo rm -frv /var/lib/apt/lists
sudo mkdir -pv /var/lib/lists/partial
sudo apt-get update
sudo apt-key update

```

---

### Post by nestoru on 2013-04-04
Thank you all for your responses and specially @msidnam for bumping this thread.
 
@ibjsb4 I have gone through that search before. No proposed solutions have worked so far
@schragge That did not resolve the issue
@d0006  I am doing my homework now and will reply back when I have some feedback

---

### Post by nestoru on 2013-04-04
Upgrading Ubuntu to 12.04.2 from 12.04 solved my issue:
[PHP]$ sudo apt-get upgrade
$ cat /etc/lsb-release 
$ sudo  /usr/bin/apt-get -o quiet=1 upgrade -u -y -o APT::Get::Show-Upgraded=true
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
krfsadmin@ldap:~$ sudo  /usr/bin/apt-get -o quiet=1 upgrade -u -y -o APT::Get::Show-Upgraded=true
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.[/PHP]
I noticed the keys were kind of weird in 12.04:
[PHP]$ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>
[/PHP]
They look better in 12.04.2
[PHP]$ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>
[/PHP]

---

### Post by nestoru on 2013-04-09
This issue came back today and we learned that our Firewall was messing around with the packets. If you face this error I would recommend installing the same version of the OS in a same-subnetwork-machine and compare the results with an installation in a machine in a different network. You might have to run strace, tcpdump and God knows what else before you convince the Firewall admin that there is something funky going on with the Network.

---

### Post by RubyTuesdayDONO on 2014-01-06
> **nestoru said:**
> Upgrading Ubuntu to 12.04.2 from 12.04 solved my issue:
```
$ sudo apt-get upgrade
$ cat /etc/lsb-release 
$ sudo  /usr/bin/apt-get -o quiet=1 upgrade -u -y -o APT::Get::Show-Upgraded=true
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
krfsadmin@ldap:~$ sudo  /usr/bin/apt-get -o quiet=1 upgrade -u -y -o APT::Get::Show-Upgraded=true

```


i don't quite understand how this works, but it did the trick! thank you!

---

