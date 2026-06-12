---
title: "Problem update"
date: 2018-01-18
forum: New to Ubuntu
---

### Post by mac187 on 2018-01-18
Hi, i updated yesterday bu running apt-get update, it went fine.

Today i got this:

```
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:3 [http://ppa.launchpad.net/fixnix/netspeed/ubuntu](http://ppa.launchpad.net/fixnix/netspeed/ubuntu) xenial InRelease         
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:5 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:9 [http://ppa.launchpad.net/fossfreedom/indicator-sysmonitor/ubuntu](http://ppa.launchpad.net/fossfreedom/indicator-sysmonitor/ubuntu) xenial InRelease
Hit:10 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial InRelease       
Hit:11 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease             
Get:6 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:8 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Hit:12 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial InRelease   
Hit:13 [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial InRelease
Hit:14 [https://deb.nodesource.com/node_8.x](https://deb.nodesource.com/node_8.x) xenial InRelease                    
Hit:15 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) xenial InRelease               
Hit:16 [http://ppa.launchpad.net/noobslab/indicators/ubuntu](http://ppa.launchpad.net/noobslab/indicators/ubuntu) xenial InRelease    
Hit:18 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                     
Hit:19 [http://ppa.launchpad.net/papirus/papirus/ubuntu](http://ppa.launchpad.net/papirus/papirus/ubuntu) xenial InRelease  
Hit:20 [http://ppa.launchpad.net/thebernmeister/ppa/ubuntu](http://ppa.launchpad.net/thebernmeister/ppa/ubuntu) xenial InRelease
Hit:21 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease       
Hit:22 [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) xenial InRelease
Ign:23 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
Ign:24 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages
Ign:25 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata
Ign:26 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons
Ign:27 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
Ign:28 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages
Get:29 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [231 kB]
Ign:30 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata
Ign:31 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons
Ign:32 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata
Get:23 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [700 kB]
Get:24 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [654 kB]
Get:25 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Err:25 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata
  Hash Sum mismatch
Get:26 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [224 kB]
Err:26 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons
  
Get:27 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [573 kB]
Get:28 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [534 kB]
Get:30 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [185 kB]
Err:30 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata
  
Get:31 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [268 kB]
Err:31 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons
  
Get:32 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5 888 B]
Err:32 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata
  
Ign:33 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata
Ign:34 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata
Get:33 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3 324 B]
Err:33 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata
  Hash Sum mismatch
Get:34 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4 712 B]
Err:34 [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata
  
Hit:35 [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial InRelease          
Hit:36 [https://packagecloud.io/slacktechnologies/slack/debian](https://packagecloud.io/slacktechnologies/slack/debian) jessie InRelease
Fetched 1 195 kB in 2s (466 kB/s)
Reading package lists... Done
E: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml.xz](http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml.xz)  Hash Sum mismatch
E: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dep11/icons-64x64.tar.gz](http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dep11/icons-64x64.tar.gz)  
E: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/universe/dep11/Components-amd64.yml.xz](http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/universe/dep11/Components-amd64.yml.xz)  
E: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/universe/dep11/icons-64x64.tar.gz](http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/universe/dep11/icons-64x64.tar.gz)  
E: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/multiverse/dep11/Components-amd64.yml.xz](http://no.archive.ubuntu.com/ubuntu/dists/xenial-updates/multiverse/dep11/Components-amd64.yml.xz)  
E: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/xenial-backports/main/dep11/Components-amd64.yml.xz](http://no.archive.ubuntu.com/ubuntu/dists/xenial-backports/main/dep11/Components-amd64.yml.xz)  Hash Sum mismatch
E: Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/xenial-backports/universe/dep11/Components-amd64.yml.xz](http://no.archive.ubuntu.com/ubuntu/dists/xenial-backports/universe/dep11/Components-amd64.yml.xz)  
E: Some index files failed to download. They have been ignored, or old ones used instead.
```


I have done anything , anyone can help me out ? or is it some problems with servers?

Any page where i can see status to the server i am connected to?

Thanks

---

### Post by Frogs Hair on 2018-01-18
You can select a different download server in software and updates under Ubuntu software. If this was a one time occurrence you could try again later. I see you have a Debian repository and this can also cause problems. It's generally not a good practice to add repositories from another distribution.

---

### Post by mac187 on 2018-01-18
Ok thanx a lot !

---

