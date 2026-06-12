---
title: "apt-get and synaptic package manager not working in Jaunty or intrepid"
date: 2009-04-22
forum: Repositories &amp; Backports
---

### Post by Geoffzx6r on 2009-04-22
Hi, I'm having an unusual problem for me. I just setup a new system today and popped in an old hard drive. The system ended up booting off the old hdd from another system. It had ubuntu 8.1 and apt-get wasn't working for some strange reason. I didn't think anything of it, so I formatted that drive and did a fresh install of jaunty jackalope 32bit rc and it isn't working with the fresh install. 

I loaded up synaptic package manager and it only shows packages already installed on the system. searching for new packages brings me no results. I've tried sudo apt-get install "some random package I know that's in the repositories" and it just says couldn't find package.

I have no clue what's causing this since the Internet is working just fine for me. I'm writing this up on the current computer.

shoot, well I just tried selecting the best server and than I reload synaptic package manager and it says it failed to fetch

Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://mirror.math.ucdavis.edu/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://mirror.math.ucdavis.edu/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://mirror.math.ucdavis.edu/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://mirror.math.ucdavis.edu/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I tried selecting the main server this time and rteloaded synaptic and it worked this time. False alarm I guess. I'm used to apt-get working straight out of the getgo

---

### Post by mod_cheetos on 2009-12-13
Hello Geoff, did you ever find out the problem with apt-get that prevented it from downloading new packages? I have just set up a new VPS with Ubuntu 9.10 and I am having the exact same problem as you. I've added the lastest repo to sources.list and done an apt-clean, but for some reason the proggie still refuses to retrieve any new packages from the internet.

Any info you can supply will be greatly appreciated. Thanks.

---

