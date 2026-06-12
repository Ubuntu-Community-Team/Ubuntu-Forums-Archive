---
title: "update problem"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by bob58523 on 2012-02-21
Greetings,

I have a netbook running ubuntu 10.10 that has been running flawlessly. Recently I began to have a problem that I hope someone can help me with. I have been using linux for a while, but I am not by any means an export. Here is the error I get:

*W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>*

[I]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 5A5366B134BA7AE9 Launchpad GMA500 PPA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

It does not effect the computer and how it runs, but I continuously get a yellow triangle for update manager saying update information is outdated.

Any help would be greatly appreciated.

Bob

---

### Post by cortman on 2012-02-21
Hi, Try the methods given in [this thread]("http://ubuntuforums.org/showthread.php?t=1865223") to fix your signature errors.

---

### Post by thirnick on 2012-02-21
go to ubuntu community search   fix broken

first entry should be synaptic fix broken packages

there is other links there

the command line is the preferred method for instalations it does many things automatic

---

### Post by wildmanne39 on 2012-02-21
Hi, actually I believe you need to do it this way, you have to put in your error numbers and not the ones in the other thread.
```
sudo apt-get clean
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192 34BA7AE9 0624A220
sudo apt-get update
```
Thanks

---

