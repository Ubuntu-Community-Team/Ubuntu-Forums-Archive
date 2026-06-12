---
title: "E: Unable to locate package for every package I try"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by daniel-oreilly on 2014-08-22
Fresh install of Ubuntu 14.04 server (not desktop).  No matter what package I attempt to install via apt-get, I always get something like this:

# apt-get install git
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package git

This is ludicrous I can't even do simple things like mount an NFS share.  Obviously I have some sort of configuration issue, but I've not been able to figure out what.

HELP!!!!!

---

### Post by Tadaen_Sylvermane on 2014-08-22
Is that an actual try? Git doesn't exist as a package. git-all does however and will install the whole thing. That being said if you should use apt-cache search "package or keyword" to get a command line list of packages with that name or description. Does the software center work? Probably should use that instead.

And for what its worth you need to do an apt-get update before you try to install anything.

---

### Post by ian-weisser on 2014-08-22
Well, git is indeed a real package.

```
$ rmadison -u ubuntu git
 git | 1:1.7.9.5-1 | precise | source, amd64, armel, armhf, i386, powerpc
 git | 1:1.9.1-1   | trusty  | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 git | 1:2.1.0-1   | utopic  | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

daniel-oreilly, 

What's the result of 'apt-get update'? Lots of 'Hit's (good), or lots of 'Ign's (bad).

If apt is not updating the dpkg database, then the next steps are to:

- Check /etc/apt/sources.list, and make sure all the Trusty repositories are listed and not commented out.
- Check your upstream router or proxy. Are they blocking?
- If you connect via a proxy, apt needs to be told about it. Separate setting from networking.

---

### Post by ibjsb4 on 2014-08-22
Easier on the eyes :D

[http://packages.ubuntu.com/trusty/git](http://packages.ubuntu.com/trusty/git)

---

### Post by Tadaen_Sylvermane on 2014-08-23
didnt show up on an apt-cache search : / else im blind. at any rate it was a thought :p

---

### Post by ibjsb4 on 2014-08-23
and

> What's the result of 'apt-get update'? Lots of 'Hit's (good), or lots of 'Ign's (bad).

If apt is not updating the dpkg database, then the next steps are to:

- Check /etc/apt/sources.list, and make sure all the Trusty repositories are listed and not commented out.
- Check your upstream router or proxy. Are they blocking?
- If you connect via a proxy, apt needs to be told about it. Separate setting from networking. 				

---

### Post by daniel-oreilly on 2014-08-25
I found the resolution to this.  The proxy setting in my apt.conf file wasn't complete.  Once I corrected that, I could do an apt-get clean, apt-key update and apt-get update, now I can install all the packages I need.

Thanks for the help on this!

---

### Post by ibjsb4 on 2014-08-25
Good show :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

