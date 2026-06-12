---
title: "Envy Help"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by 124C41+ on 2008-04-28
So I have finally taken the plunge tonight and I tried to run Envy to install  my ATI drivers. 

When i start up Envy there is red Text at the top that says the following. 
Error: Dependency is not satisfiable: debhelper 

Whats this mean? Whats my next course of action.
Thanks.

---

### Post by sam_delta on 2008-04-28
```
sudo apt-get install debhelper
```

but, it shoulnt happen if you installed envy directly from ubuntu repos. do you have EnvyNG (for ubuntu 8.04), from system>administration>synaptic? or you got it from external source???

if you got it from a external source, its fine, just intall debhelper, just make sure you have the envyNG for ubuntu 8.04

sam

---

### Post by 124C41+ on 2008-04-28
Im using Gusty.. I copied it 2 wweeks ago and only just remembered a new version has been released. I type that code in and get this in return.

Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package debhelper has no installation candidate

What now?

---

### Post by sam_delta on 2008-04-28
try installing it from ubuntu repositories , go into system>administration>synaptic and search for debhelper, if you cant find it, click on settings>repositories under synaptic, and checkbox every source of repos (cononical supported, third party software, etc etc), and serch for it a gain, if still cant find it, searchfor envy and install envy from synaptic

tell us if it works

---

