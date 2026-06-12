---
title: "Synaptic: Can't update Mozilla"
date: 2006-04-06
forum: Repositories &amp; Backports
---

### Post by cosmolee on 2006-04-06
I'm having problems updating Mozilla.  I currently have 1.7.11 installed.  

I try to mark Mozilla for installation w/in Synaptic (it doesn't indicate that Mozilla is already installed, so I get the "mark for installation" option, not "mark for upgrade".  

The package that I choose is labeled version:  "2:1.7.12-0ubuntu2" and the description is "The Mozilla Internet application suite - meta package"

When I try to mark the package for installation, I get this error:

mozilla:
  Depends: mozilla-browser (=2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
 Depends: mozilla-mailnews but it is not going to be installed
  Depends: mozilla-psm (=2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed


If I'm reading this correctly, it's trying to install 2:1.7.12-1ubuntu1 instead of 2:1.7.12-0ubuntu2.  Why is this the case?

Fixes??

Thanks. ](*,)

---

### Post by aysiu on 2006-04-06
Those kinds of dependency problems usually stem from conflicting repositories list.

Get a clean list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by cosmolee on 2006-04-06
I tried the sources.list you suggested, that's not the problem: I get the same exact error message using that .list.

Thanks for trying, though...](*,)

---

