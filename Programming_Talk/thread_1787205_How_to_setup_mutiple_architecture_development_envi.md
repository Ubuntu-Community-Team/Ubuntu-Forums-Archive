---
title: "How to setup mutiple architecture development environment under Ubuntu 11.04"
date: 2011-06-20
forum: Programming Talk
---

### Post by mirandien on 2011-06-20
I have installed Ubuntu 11.04 amd64 (64 bits) OS and I  try to take advantage of the new multiple architecture support of this  latest Ubuntu version to cross compile ia32 applications as well as  being able to develop amd64 (64 bits) applications. I have followed  these instructions to setup my multiple architecture environment :


  [http://wiki.debian.org/Multiarch/Implementation](http://wiki.debian.org/Multiarch/Implementation)
  
[LIST]
[*]add APT::Architectures { "amd64"; "i386"; }; to /etc/apt/apt.conf
[*]add foreign-architecture i386 to /etc/dpkg/dpkg.cfg
[*]run apt-get update to refresh the package cache with the newly added architecture
[/LIST]
  Now I try to use the synaptic package manager to update both the  current architecture (amd64) and the i386 architecture with development  packages. (I can see both package displayed by synaptic). However when I  try to install an i386 package then synaptic complains and says it will  remove the amd64 package because if conflict with the i386 package.  However I would expect that both can coexist to be able to cross  compile.


  For example I try to install both :


  libglog4cxx10-dev and libglog4cxx10-dev:i386


  How can I use synaptic to install both development package? If this is not possible how can I setup my development environment ?

---

