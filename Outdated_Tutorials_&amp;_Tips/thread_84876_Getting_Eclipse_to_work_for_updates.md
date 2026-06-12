---
title: "Getting Eclipse to work for updates"
date: 2005-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by jmeadows111 on 2005-11-01
I installed Eclipse in Breezy via the Add Applications program, but would get errors when trying to run the software update / plug-in install portion of Eclipse. I found a useful page that give the step by step on how to get around the issues:

[http://www.intertwingly.net/blog/2005/10/26/RadRails-Eclipse-on-Breezy-take-1](http://www.intertwingly.net/blog/2005/10/26/RadRails-Eclipse-on-Breezy-take-1)

The distilled version is:

sudo apt-get install eclipse-source
sudo mkdir /usr/local/lib/eclipse/plugins
sudo mkdir /usr/local/lib/eclipse/features
sudo chown `id -un`:`id -gn` /usr/local/lib/eclipse/*

I tried these four steps and now update is running properly!:p

---

