---
title: "Local File Repository Problem"
date: 2009-10-04
forum: Repositories &amp; Backports
---

### Post by linuxeverywhere on 2009-10-04
**I setup an automatic local file repository for my local packages.**

**I followed the repository guide:**  [http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html)

**I setup my repo tree like this:**
/home/greno/packages/archives/dists/stable/main/binary-i386
/home/greno/packages/archives/dists/stable/main/binary-i386/Packages.gz
/home/greno/packages/archives/dists/stable/main/binary-i386/myapp_1-1_all.deb

**I generated my Packages.gz file like this:**
cd /home/greno/packages/archives
"dpkg-scanpackages /home/greno/packages/archives /dev/null | gzip -9c > dists/stable/main/binary-i386/Packages.gz

**I add the following to /etc/apt/sources.list:**
deb file:/home/greno/packages/archives stable main

**But when I run an update it gives an error:**
$ sudo apt-get update
Ign file: stable Release.gpg
Ign file: stable/main Translation-en_US                                     
Ign file: stable Release                                                    
Ign file: stable/main Packages                                               
Err file: stable/main Packages                                               
  File not found

I searched the internet and found many many references to this type of error for local file repositories.  So is this some known bug and how do I work around it so that I can get local file repository working?

---

### Post by ermeyers on 2009-10-04
> **linuxeverywhere said:**
> [B]
I setup an automatic local file repository for my local packages.[/B]

**I followed the repository guide:**  [http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html)


Ubuntu is not Debian.  Debian is not Ubuntu.  So Ubuntu:
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by linuxeverywhere on 2009-10-04
Well strictly speaking that's true but the repository mechanism is about the same since both use 'apt' as the package manager.

And here's a link for a very simple (too simple) ubuntu personal repository:  [https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

What I was trying to do what to setup an "automatic" repository but filesystem-based.

You should be able to setup just about any heirarchy you want and if you put it into sources.list it should work.  But for whatever reason it is not working for me (or for many others for that matter judging by all the problem posts I see about this).

So there seems to be something about it being "file-based" coupled with the "automatic" type of repository that is causing problems here and I was hoping that someone had managed to solve that issue or knew for sure if it was a bug.

BTW, I have about 15 years linux experience but I am recent to debian/ubuntu distros.

---

### Post by ermeyers on 2009-10-04
I've done both the Personal for "other" deb files, and the Offline for the repos, and they both worked directly.  Ubuntu has got it's own thing going, so you can't go directly from Debian help instructions.  That's all.  Good luck!

---

### Post by ermeyers on 2009-10-04
/root/myrepo_update.sh:
```

#!/bin/sh                                                               
##                                                                      

CODE=jaunty
ARCH=i386  
cd /root   
mkdir myrepo
mkdir myrepo/dists
mkdir myrepo/dists/$CODE
mkdir myrepo/dists/$CODE/main
mkdir myrepo/dists/$CODE/restricted
mkdir myrepo/dists/$CODE/multiverse
mkdir myrepo/dists/$CODE/universe  
cd /root/myrepo/dists/$CODE        
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/Release
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/Release.gpg
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/Contents-$ARCH.gz
COMPONENT=main                                                        
cd /root/myrepo/dists/$CODE/$COMPONENT/binary-$ARCH                   
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Release                                                                            
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Packages.gz                                                                        
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Packages.bz2                                                                       
COMPONENT=restricted                                                            
cd /root/myrepo/dists/$CODE/$COMPONENT/binary-$ARCH                             
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Release
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Packages.gz
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Packages.bz2
COMPONENT=multiverse
cd /root/myrepo/dists/$CODE/$COMPONENT/binary-$ARCH
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Release
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Packages.gz
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Packages.bz2
COMPONENT=universe
cd /root/myrepo/dists/$CODE/$COMPONENT/binary-$ARCH
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Release
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Packages.gz
wget http://us.archive.ubuntu.com/ubuntu/dists/$CODE/$COMPONENT/binary-$ARCH/Packages.bz2

```

/etc/apt/source.list
```

#Local repos
deb file:///root/myrepo jaunty main restricted universe multiverse

```

---

### Post by linuxeverywhere on 2009-10-04
There is something strange that happens because of the path.

When I setup a local repository using a simple path then it works fine.
> #tree
/tmp/testrepo
# sources.list
deb file:/tmp/testrepo ./But when I use the paths that I setup as in my first post then it no longer works.
> #tree
/home/greno/packages/archives/dists/stable/main/binary-i386
# sources.list
deb file:/home/greno/packages/archives/dists/stable/main/binary-1386 ./
OR deb file:/home/greno/packages/archives stable main
(either should work if dpkg-scanpackages run from the proper root)So there is definite bug somewhere.  My only solution for now is to create a local repo 'root' with a shorter path.

---

### Post by ermeyers on 2009-10-04
It appears to me that you are mixing/complicating things.  With the link that I gave you for "Offline Repository", you can download a local copy of the online repos.  Otherwise you can use the Personal repository method to create a repository for your non-standard deb files.  What you are doing is something in between, and over complicated.  That's why you're having problems.  For the Offline repo the statement was simple compared to your entry:

deb file:///root/myrepo jaunty main restricted universe multiverse

---

### Post by linuxeverywhere on 2009-10-04
I'm not trying to establish an offline copy of ubuntu repos.  That is not part of the issue here.  Leave it out.

I'm setting up a local repo for my own debs that I have created.

And nothing is overly complicated.  This is standard repo setup type stuff.

Yes I find that the local repo works in the case where I have a very short path to the repo root such as /tmp/testrepo.  

However, this case is not sufficient and a longer root path is needed such as I had originally /home/greno/packages/archive.   

This longer root path breaks the local repo.  And that is most likely a bug.

So for now I am forced to use a shorter root path and it works.

---

### Post by ermeyers on 2009-10-04
So your doing the Personal repo version.  I put deb files in /root/myrepo, a short path.  Like you said probably a bug.

/root/update-mydebs.sh :
```

#!/bin/sh
cd /root/mydebs
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

```

/etc/apt/sources.list :
```

#Local repos
deb file:///root/myrepo jaunty main restricted universe multiverse

```I hope this helps.

---

