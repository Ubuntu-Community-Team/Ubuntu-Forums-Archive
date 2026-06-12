---
title: "How to install varnish on ubuntu 16.04"
date: 2018-08-20
forum: New to Ubuntu
---

### Post by neovich on 2018-08-20
I tried install varnish6 by using this tutorial [https://packagecloud.io/varnishcache/varnish60/install#manual-deb](https://packagecloud.io/varnishcache/varnish60/install#manual-deb)
my file /etc/apt/sources.list.d/varnishcache_varnish60.list
```
deb https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04 LTS Xenial Xerus main
deb-src https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04 LTS Xenial Xerus main

```
and when do
sudo apt-get update
got the error
```
neo@neo:/tmp/varnish-cache$ sudo apt-get updateIgn:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://ppa.launchpad.net/chris-lea/redis-server/ubuntu xenial InRelease
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                                                                              
Hit:4 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu xenial InRelease                                                                   
Get:6 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease [23.9 kB]            
Get:7 http://ppa.launchpad.net/ondrej/php/ubuntu xenial/main amd64 Packages [51.1 kB]             
Get:8 http://ppa.launchpad.net/ondrej/php/ubuntu xenial/main i386 Packages [50.9 kB]                          
Hit:9 http://ua.archive.ubuntu.com/ubuntu xenial InRelease                             
Hit:10 http://ua.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                                              
Hit:11 http://ua.archive.ubuntu.com/ubuntu xenial-backports InRelease                                                                            
Hit:12 http://linux.teamviewer.com/deb stable InRelease                                                                     
Hit:13 http://security.ubuntu.com/ubuntu xenial-security InRelease                            
Hit:14 http://deb.playonlinux.com maverick InRelease                    
Hit:15 http://linux.teamviewer.com/deb preview InRelease
Ign:16 https://dl.bintray.com/rabbitmq/debian xenial InRelease
Hit:17 https://deb.opera.com/opera-stable stable InRelease
Hit:18 https://dl.bintray.com/rabbitmq/debian xenial Release                                                                                     
Ign:20 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04 InRelease                                                              
Ign:21 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04 Release                                                                
Ign:22 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Sources                                                            
Ign:23 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Sources
Ign:24 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Sources
Ign:25 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Sources
Ign:26 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 Packages
Ign:27 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS i386 Packages
Ign:28 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS all Packages
Ign:29 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en_US
Ign:30 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en
Ign:31 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 DEP-11 Metadata
Ign:32 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS DEP-11 64x64 Icons
Ign:33 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 Packages
Ign:34 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial i386 Packages
Ign:35 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial all Packages
Ign:36 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en_US
Ign:37 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en
Ign:38 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 DEP-11 Metadata
Ign:39 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial DEP-11 64x64 Icons
Ign:40 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 Packages
Ign:41 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus i386 Packages
Ign:42 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus all Packages
Ign:43 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en_US
Ign:44 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en
Ign:45 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 DEP-11 Metadata
Ign:46 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus DEP-11 64x64 Icons
Ign:47 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 Packages
Ign:48 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main i386 Packages
Ign:49 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main all Packages
Ign:50 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en_US
Ign:51 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en
Ign:52 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 DEP-11 Metadata
Ign:53 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main DEP-11 64x64 Icons
Ign:22 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Sources
Ign:23 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Sources
Ign:24 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Sources
Ign:25 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Sources
Ign:26 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 Packages
Ign:27 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS i386 Packages
Ign:28 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS all Packages
Ign:29 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en_US
Ign:30 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en
Ign:31 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 DEP-11 Metadata
Ign:32 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS DEP-11 64x64 Icons
Ign:33 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 Packages
Ign:34 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial i386 Packages
Ign:35 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial all Packages
Ign:36 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en_US
Ign:37 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en
Ign:38 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 DEP-11 Metadata
Ign:39 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial DEP-11 64x64 Icons
Ign:40 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 Packages
Ign:41 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus i386 Packages
Ign:42 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus all Packages
Ign:43 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en_US
Ign:44 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en
Ign:45 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 DEP-11 Metadata
Ign:46 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus DEP-11 64x64 Icons
Ign:47 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 Packages
Ign:48 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main i386 Packages
Ign:49 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main all Packages
Ign:50 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en_US
Ign:51 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en
Ign:52 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 DEP-11 Metadata
Ign:53 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main DEP-11 64x64 Icons
Ign:22 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Sources
Ign:23 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Sources
Ign:24 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Sources
Ign:25 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Sources
Ign:26 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 Packages
Ign:27 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS i386 Packages
Ign:28 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS all Packages
Ign:29 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en_US
Ign:30 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en
Ign:31 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 DEP-11 Metadata
Ign:32 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS DEP-11 64x64 Icons
Ign:33 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 Packages
Ign:34 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial i386 Packages
Ign:35 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial all Packages
Ign:36 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en_US
Ign:37 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en
Ign:38 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 DEP-11 Metadata
Ign:39 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial DEP-11 64x64 Icons
Ign:40 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 Packages
Ign:41 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus i386 Packages
Ign:42 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus all Packages
Ign:43 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en_US
Ign:44 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en
Ign:45 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 DEP-11 Metadata
Ign:46 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus DEP-11 64x64 Icons
Ign:47 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 Packages
Ign:48 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main i386 Packages
Ign:49 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main all Packages
Ign:50 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en_US
Ign:51 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en
Ign:52 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 DEP-11 Metadata
Ign:53 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main DEP-11 64x64 Icons
Ign:22 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Sources
Ign:23 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Sources
Ign:24 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Sources
Ign:25 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Sources
Ign:26 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 Packages
Ign:27 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS i386 Packages
Ign:28 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS all Packages
Ign:29 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en_US
Ign:30 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en
Ign:31 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 DEP-11 Metadata
Ign:32 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS DEP-11 64x64 Icons
Ign:33 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 Packages
Ign:34 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial i386 Packages
Ign:35 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial all Packages
Ign:36 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en_US
Ign:37 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en
Ign:38 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 DEP-11 Metadata
Ign:39 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial DEP-11 64x64 Icons
Ign:40 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 Packages
Ign:41 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus i386 Packages
Ign:42 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus all Packages
Ign:43 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en_US
Ign:44 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en
Ign:45 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 DEP-11 Metadata
Ign:46 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus DEP-11 64x64 Icons
Ign:47 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 Packages
Ign:48 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main i386 Packages
Ign:49 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main all Packages
Ign:50 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en_US
Ign:51 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en
Ign:52 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 DEP-11 Metadata
Ign:53 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main DEP-11 64x64 Icons
Ign:22 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Sources
Ign:23 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Sources
Ign:24 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Sources
Ign:25 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Sources
Ign:26 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 Packages
Ign:27 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS i386 Packages
Ign:28 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS all Packages
Ign:29 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en_US
Ign:30 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en
Ign:31 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 DEP-11 Metadata
Ign:32 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS DEP-11 64x64 Icons
Ign:33 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 Packages
Ign:34 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial i386 Packages
Ign:35 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial all Packages
Ign:36 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en_US
Ign:37 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Translation-en
Ign:38 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial amd64 DEP-11 Metadata
Ign:39 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial DEP-11 64x64 Icons
Ign:40 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 Packages
Ign:41 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus i386 Packages
Ign:42 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus all Packages
Ign:43 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en_US
Ign:44 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Translation-en
Ign:45 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus amd64 DEP-11 Metadata
Ign:46 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus DEP-11 64x64 Icons
Ign:47 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 Packages
Ign:48 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main i386 Packages
Ign:49 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main all Packages
Ign:50 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en_US
Ign:51 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Translation-en
Ign:52 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main amd64 DEP-11 Metadata
Ign:53 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main DEP-11 64x64 Icons
Err:22 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Sources
  404  Not Found
Ign:23 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xenial Sources
Ign:24 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/Xerus Sources
Ign:25 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/main Sources
Ign:26 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 Packages
Ign:27 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS i386 Packages
Ign:28 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS all Packages
Ign:29 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en_US
Ign:30 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS Translation-en
Ign:31 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS amd64 DEP-11 Metadata
Ign:32 https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04/LTS DEP-11 64x64 Icons
Fetched 126 kB in 54s (2,324 B/s)
Reading package lists... Done
W: The repository 'https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04 Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial/dists/16.04/LTS/source/Sources  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
neo@neo:/tmp/varnish-cache$ 

```

What is wrong?

---

### Post by Habitual on 2018-08-20
> **neovich said:**
> ```

W: The repository 'https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04 Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial/dists/16.04/LTS/source/Sources  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

What is wrong?

See [https://www.cyberciti.biz/faq/how-to-install-and-configure-varnish-cache-on-ubuntu-linux-16-04-lts/](https://www.cyberciti.biz/faq/how-to-install-and-configure-varnish-cache-on-ubuntu-linux-16-04-lts/)
for instructions that I trust. His whole site is a "Keeper". ;)

What/where are you getting your install instructions from?

---

### Post by Habitual on 2018-08-20
> **neovich said:**
> ```

W: The repository 'https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial 16.04 Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch https://packagecloud.io/varnishcache/varnish60/ubuntu/xenial/dists/16.04/LTS/source/Sources  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

What is wrong?

See [https://www.cyberciti.biz/faq/how-to-install-and-configure-varnish-cache-on-ubuntu-linux-16-04-lts/](https://www.cyberciti.biz/faq/how-to-install-and-configure-varnish-cache-on-ubuntu-linux-16-04-lts/)
for instructions that I trust. His whole site is a "Keeper". ;)

What/where are you getting your install instructions from?

---

