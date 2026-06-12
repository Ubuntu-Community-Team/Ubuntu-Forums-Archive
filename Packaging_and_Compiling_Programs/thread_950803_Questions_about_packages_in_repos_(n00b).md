---
title: "Questions about packages in repos (n00b)"
date: 2008-10-17
forum: Packaging and Compiling Programs
---

### Post by BrentNewland on 2008-10-17
I've never done a line of regular programming in my life (I'm an HTML/PHP kinda guy); the only thing I've done with source code is compile and install.

Anyways, some of the programs I use often are either not in the repositories, or they're outdated. I've read the Ubuntu Wiki on how to update a package (except it doesn't say what to do once you have all the files, where to upload it and what to upload). So that's my first question, what files do I need to upload and where do they go to get a program updated.

My second question pertains to new packages. Alot of my favorite packages are just not in the repos (most importantly moblock and qbittorrent). Is it okay to upload those to the repos? Do I do that through [http://revu.ubuntuwire.com/?](http://revu.ubuntuwire.com/?) How exactly do I upload through that website (I see no links or forms for uploading - is it closed because of Intrepid?)? If it's upstream in Debian how long does it take to get put in the repos if I file a bug report?

---

### Post by Pro-reason on 2008-10-18
The problem with adding to the official Ubuntu repos is not the lack of packagers (there are plenty of us), but the lack of trusted people to approve those packages.  There is therefore not much you can do.  You just have to hope they will eventually do it.

If you want a package to do available to people, then learn how to maintain your own PPA on Launchpad.  It will then be immediately available to anyone who wants to add it.  You can then file a “needs packaging” bug on Ubuntu Launchpad, pointing out your PPA as an example of that code being successfully packaged for Ubuntu.  It will then be done when they feel like doing it.

---

### Post by jre on 2008-10-19
The packaging request is here: [https://bugs.launchpad.net/ubuntu/+bug/109822](https://bugs.launchpad.net/ubuntu/+bug/109822)

On moblock-deb.sourceforge.net I already offer packages for:
moblock
moblock-control
mobloquer

---

### Post by snova on 2008-10-19
Look into backports if you need newer versions of packaged software.

And I think PHP counts as programming. I don't personally think HTML does though, unless you add a little Javascript or something. But that's not technically HTML, so...

---

### Post by InfinityCircuit on 2008-10-20
[http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php)

Ubuntu packages exist for this as well.  It's a pretty complex process to get something into Ubuntu.

---

