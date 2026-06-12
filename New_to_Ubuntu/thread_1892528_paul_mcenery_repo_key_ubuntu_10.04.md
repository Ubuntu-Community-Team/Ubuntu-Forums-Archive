---
title: "paul mcenery repo key ubuntu 10.04"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by fattyz on 2011-12-08
Hi I had to take my acer laptop back to 10.04 because I got a black screen in 11.xx and never resolved it.

Anyway i need my iphone tether and I am stuck. I have done this before but I think something is wrong with the system due to a crash I had a few weeks ago.

I get a dialogue on startup saying "an application wants to use the keyring "default" but it is locked"

I don't know if this is related but I can not add the paul mcenry repo or install ipheth-utils from ubuntu software center or synaptic package manager and I am really frustrated!

When I try sudo add-apt-repository ppa:pmcenery/ppa I get the following,

 Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 3AE22276BF4F39C8D6117D7F4EA3A911D48B8E25
gpg: requesting key D48B8E25 from hkp server keyserver.ubuntu.com
gpg: key D48B8E25: "Launchpad PPA for Paul McEnery" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Then sudo apt-get update gets me

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppathen/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/pmcenery/ppathen/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

If I try to install ipheth-utils it won't work, synaptic asks for the install cd, ubuntu software center just keeps trying to install endlessly and locks the system so apt-get and synaptic won't work.

What am I doing wrong?

Thanks 

FattyZ

---

### Post by An Sanct on 2011-12-08
You are not doing anything wrong..

> **fattyz said:**
> 
W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppathen/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/pmcenery/ppathen/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found


Says it all, the file in the link is not present anymore.
The file, for the AMD64 architecture and lucid is available on this location
[http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)

So, you should open Software Center, select Edit>Software Sources, click the tab Other Software and find the incorrect entry.
The incorrect entry should be:
http://ppa.launchpad.net/pmcenery/ppa**then**/ubuntu/...
change it to:
http://ppa.launchpad.net/pmcenery/ppa/ubuntu/...

I don't know how you got that "then" there, but it should be the source of the problem.

---

### Post by fattyz on 2011-12-08
Oh, syntax and cutting and pasting errors, but the file was not where I was looking for it.  Well thanks, I've been working it for a few days and though I've done it more than once I never can quite remember how.

Although I can follow along fairly well, I still get mixed up easily when it is not doing what I expect it to do.

Thanks for the fast reply I'll get on that and mark the thread solved if I get it.

Yours, 

FattyZ

---

### Post by An Sanct on 2011-12-08
Okay :) if the problem still persists, feel free to tell me, I have other possible solutions :)

---

### Post by fattyz on 2011-12-09
It works thank God, now I can move my music files and downloading chores totally out of itunes/windows/ares into ubuntu.  What a relief.  One less reason to have to log back into Windows.

Thanks so much.

---

