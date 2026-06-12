---
title: "Tor install problems"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Paraphysicist on 2008-04-22
I noticed the version of Tor in synaptic was slightly out of date so I tried to use the instructions on torproject.org.  

I typed sudo gedit /etc/apt/sources.list and added 

deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) gutsy main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) gutsy main
 
to the end of the text file.

Then I typed in sudo apt-get update and at the end of the output I got: 

Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.bz2](http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: [http://packages.dfreer.org](http://packages.dfreer.org) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

When I check for updates, one of the "repository indexes" can't be downloaded.  This one:

[http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.bz2:](http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

This is the error why: 

W: GPG error: [http://packages.dfreer.org](http://packages.dfreer.org) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2

I also tried the instructions from [https://help.ubuntu.com/community/TOR#head-ccba4382b2ec0a1f923f783fdb6b0b9a1d57df3c](https://help.ubuntu.com/community/TOR#head-ccba4382b2ec0a1f923f783fdb6b0b9a1d57df3c) :  

sudo gpg --keyserver subkeys.pgp.net --recv 94C09C7F
sudo gpg --fingerprint 94C09C7F
sudo gpg --export 94C09C7F | sudo apt-key add -

I also tried all the coommands under "Verifying signatures with apt 0.6.x"

All of the commands seemed to work just fine, until:

sudo apt-get update

and I get the same errors as before.


I googled this for hours, but I still have no idea.  I think I need the repository key, but I'm not sure what to do.  It's probably something easy, but I'm a noob at linux.  Any advice would be greatly appreciated.

---

### Post by PinkFloyd102489 on 2008-04-22
You should be able to open the repo link in a browser and then manually download the package(s) you need, if you cant get the GPG key working. Then just dpkg them.

---

### Post by Paraphysicist on 2008-04-22
PinkFloyd, thanks for the reply.  I managed to get it working after restarting and installing a proxy.  It looks like the terminal output for sudo apt-get update might be unrelated (even though it happened the exact same time after I edited the sources.list file and installed tor).  It's a different repository, might just be down atm.

---

