---
title: "Updating through a proxy?"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Tanhauser08 on 2008-09-19
Hello, all.

I've been using Ubuntu at home for about six months now and have never had a reason to post on this board. However, I've been taking a computer class at my school, and am trying to get Ubuntu to work there. The school is behind a proxy, and it seems to be blocking aptitude. Here's the output of sudo apt-get update. The machine is running 7.10, by the way.

[SIZE="1"]> Ubuntu apluslinux update errors

apluslinux@apluslinux-desktop:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/SIZE]

I know that's really long, sorry. I wasn't sure which parts of it were essential and which weren't.

Is anybody able to help me out here? Thanks in advance.

---

### Post by kostkon on 2008-09-19
One easy way would be to set your proxy in *Gnome* from *System -> Preferences -> Network Proxy* and then check for updates using the *Update Manager* (*System -> Administration -> Update Manager*).


If you prefer to use the command line, i.e. use *apt-get*, then to set the proxy do:

open your *.bashrc* file, i.e. do in a terminal:
```
nano ~/.bashrc
```
and put at the end of this file the following lines
```
export HTTP_PROXY=http://yourproxyusername:yourproxypassword@yourproxy:port/
export FTP_PROXY=http://yourproxyusername:yourproxypassword@yourproxy:port/

```
and change the yourproxyusername, yourproxypassword etc. accordingly to match your own.

You may need to logout and login again in order for the above to work.

---

