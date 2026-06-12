---
title: "rubygems problem"
date: 2008-06-04
forum: Programming Talk
---

### Post by danaild on 2008-06-04
Hi everybody,

I try to install ruby and its package manager system gems.

so, I go

sudo apt-get install rubygems

but this version is old, and so I have to

sudo gem update --system

this upgrades gem.
And this is the error I get:

ERROR:  While executing gem ... (URI::InvalidURIError)
    bad URI(is not URI?): [http://:8080/](http://:8080/)

Any help will be appreciated,
danail

---

### Post by danaild on 2008-06-04
Resolved!!!

System -> Preferences -> Network Proxy

Here, if you don't use proxy, check the "Direct Internet Connection" 

My configuration was set to "Manual Configuration" 
and "Http Proxy" was set to [http://:8080/](http://:8080/).

This was the problem. (I needed to restart, though, dunno how to do it without restart).

---

### Post by rye_ on 2008-06-04
installing a package manager (gems) as a package of another package manager (apt), can lead to issues when gem update is run.

The ubuntu wiki examples the other, more standard way of installing rubygems in the make, make install fashion such that apt is ignorant of it's activities. 

Ryan

---

### Post by danaild on 2008-06-06
10x, I'll install it the other way.

---

