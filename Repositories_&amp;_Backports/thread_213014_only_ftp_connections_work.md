---
title: "only ftp connections work"
date: 2006-07-10
forum: Repositories &amp; Backports
---

### Post by samhamfast on 2006-07-10
i have been having difficulty connecting to repositories.
the default connections to the supported repositories failed until i edited them to be an ftp connection. the following is terminal output showing this situation.  notice the connection for main binary does not work but main source does the only difference is the http vs ftp definition in the file

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security Release.gpg
Get:1 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Get:2 [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security Release [30.9kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-updates Release.gpg
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports Release.gpg
Get:3 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper Release [34.8kB]
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/main Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/restricted Packages
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/main Sources
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/restricted Sources
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/universe Packages
Get:4 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [ftp://security.ubuntu.com](ftp://security.ubuntu.com) dapper-security/universe Sources
Get:5 [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper/main Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper/restricted Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper/universe Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper/universe Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-updates/main Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-updates/main Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports/main Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports/universe Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports/main Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports/universe Sources
Hit [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 116kB in 8s (13.2kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

