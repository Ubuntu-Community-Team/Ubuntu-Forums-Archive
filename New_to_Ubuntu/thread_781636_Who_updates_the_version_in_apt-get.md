---
title: "Who updates the version in apt-get"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by omerb on 2008-05-04
Hi all,

Netbeans 6.1 version is out now, and when I install the netbeans via apt-get, the Netbeans version 6.0.1 is installed. I installed the 6.1 version, but I just wonder who updates these packages? How can I follow which version will be uploaded when?

---

### Post by macaholic on 2008-05-04
Well, depending on what repositories you have enabled, the main ubuntu repositories are maitained by the developers and see updates based on when they deem them necessary. 3rd party repositories are maintained by whoever set it up, usually has their name in it, ie shame's compiz fusion repository.

---

### Post by omerb on 2008-05-04
Unbelievable quick reply. :) And how can I learn from which repository it downloaded the netbeans? And what happens if there are two repositories both having the netbeans but one serves v6.1 and the other one servers v6.0.1? How does it decide from which repository to download the package?

---

### Post by macaholic on 2008-05-04
> **omerb said:**
> Unbelievable quick reply. :) And how can I learn from which repository it downloaded the netbeans? 
Good question, You can always tell what repository a package is from by going into synaptic, searching for the pacakage, right-clicking, select properties, and then versions, you can also see the maintainer, what section it is from, and other useful info on the common page. 
> **omerb said:**
> And what happens if there are two repositories both having the netbeans but one serves v6.1 and the other one servers v6.0.1? How does it decide from which repository to download the package?
Also a very good question, you can set what you want ubuntu to do in stnaptic under settings > Updates, along with what mirror you want to download stuff from. It even will let you test for the fastest mirror.

---

### Post by omerb on 2008-05-04
Thanks for the replies.

I did what you said. The maintainer is "Ubuntu MOTU Developers". I googled and found that page [1]. But I couldn't find a page where I can search for package versions (netbeans). Anyway I just wondered, and learned new things :)  


[1] [https://wiki.ubuntu.com/MOTU/Teams/Java](https://wiki.ubuntu.com/MOTU/Teams/Java)

---

### Post by RequinB4 on 2008-05-04
If you wish to download a version of a program that is not in the repositories, the safest bet is to use the repository of the specific program devs.  Instructions on doing this are usually on the website of the project.

The second choice would be to download a compiled package directly from the source (this would be something.deb for a package or a something.sh shell script installer - note - only install software or run scripts from sources you trust). ([http://download.netbeans.org/netbeans/6.1/final/](http://download.netbeans.org/netbeans/6.1/final/))

If you want to compile from source, projects usually have a git, cvs, or svn repository for the lastest bleeding edge product, though it might not be stable. ([http://www.netbeans.org/community/sources/hg.html](http://www.netbeans.org/community/sources/hg.html))

---

