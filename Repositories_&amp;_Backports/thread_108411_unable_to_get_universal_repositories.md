---
title: "unable to get universal repositories"
date: 2005-12-26
forum: Repositories &amp; Backports
---

### Post by peevee on 2005-12-26
hi friends,
after installing new copy of ubuntu 5.10,
i enabled all repositories in synaptic package manager, and when i clicked ok,
it is updating, and when it tried to download, it couldnt succede,
my machine is connected to net, and its working completely fine,
can you ppl tell me what is the problem??

---

### Post by peevee on 2005-12-26
when synaptic manager is giving an error for an URI, 
i am typing the same in firefox and again running synaptic manager, and its working now,
if i restart its not working again..
why?

---

### Post by 23meg on 2005-12-26
Did you do a "sudo apt-get update"? What errors are you getting?

---

### Post by peevee on 2005-12-26
this is what i am getting if i am doing 
dudo apt-get update
36% [Connecting to in.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting to ca.archive.u.......

so on,,
you can see that its resolving the Domain as 1.0.0.0 which is wrong....
but it works if i am accessing the site, security.ubuntu.com in firefox and again trying this...
its giving like this

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg [189B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy Release
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release [30.9kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-updates/restricted Sources
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [28.5kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages [2304kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/multiverse Sources
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [8844B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [23.1kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [3722B]

---

