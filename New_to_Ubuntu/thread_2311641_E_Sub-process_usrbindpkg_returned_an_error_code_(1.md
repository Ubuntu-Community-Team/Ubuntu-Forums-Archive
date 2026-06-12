---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1) when upgrading"
date: 2016-01-28
forum: New to Ubuntu
---

### Post by sey2 on 2016-01-28
I receive this error everytime I try
  ```

sudo apt-get upgrade

```
  It outputs:
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gir1.2-gnomekeyring-1.0 gir1.2-packagekitglib-1.0 gstreamer0.10-plugins-good
  libgnome-keyring0 libnih-dbus1 libnih1 libproxy-tools
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libsemanage1
  libwpd-0.10-10
The following packages will be upgraded:
  locales
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0 B/3.924 kB of archives.
After this operation, 6.998 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
(Reading database ... 217031 files and directories currently installed.)
Preparing to unpack .../locales_2.19-18_all.deb ...
Unpacking locales (2.19-18) over (2.13+git20120306-21) ...
dpkg: error processing archive /var/cache/apt/archives/locales_2.19-18_all.deb (--unpack):
 trying to overwrite '/usr/sbin/validlocale', which is also in package libc-bin 2.21-0ubuntu4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.19-18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```
   I tried
```
sudo apt-get install -f
``` 
already, just saying, that "12 [programs] not upgraded"

I hope you guys can help me, thank you in advance

---

### Post by steveo314 on 2016-02-01
Did you make any changes to your sources.list file?

The newest version of locales in the Ubuntu repositories for Stable('Wily') and Dev('Xenial') is 2.13+git20120306-21, but your system is pulling 2.19-18, which can only be found in Debian Stable('Jessie') at the moment.

---

