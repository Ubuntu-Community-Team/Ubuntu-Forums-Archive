---
title: "trying to install xbmc but installing beta in error?"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by nephilimelly on 2012-02-09
I'm sorry if this is the wrong place but I am still learning Ubuntu and consider myself a beginner (I know a couple of things based on trial and error). 

XBMC is a program I enjoy to view movies and the like. I used to have it on my system here some time ago but I recently reinstalled Ubuntu. That being said, I had to re-install XBMC. However, when trying the instructions provided on XBMC's site to get the Version 10, ([http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux](http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux)) I keep on getting booted up to the version 11 beta (which is unstable). 

I also noticed some errors when trying to go through the command lines, specifically when it comes to the PPA.  I don't know of an alternate way to clean up or get the PPA installed correctly. Here's the error I'm getting:

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


I searched around the web a bit and found a variety of instructions and suggestions on removing the program and then trying to re-install through different command lines. Unfortunately, all have resulted in the beta version which I did not want at all.

Any thoughts or suggestions which you kind folks could offer would be greatly appreciated. If there are any other pieces of information which I could offer that would help in figuring out this puzzle, please let me know and I will certainly do my best to provide them.

---

### Post by cariboo on 2012-02-09
Change the distribution in software sources to Maverick, as there are no Oneiric packages in that ppa.

---

### Post by nephilimelly on 2012-02-11
cariboo907, thanks so much for the help and sorry for not posting back sooner!

This did help and now I'm able to get the program installed and the desired version.

Again, thank you very much for your time and insight! :)

---

