---
title: "Best way to prevent overwrite of patched or ppa version of a .deb on upgrades?"
date: 2010-06-02
forum: Packaging and Compiling Programs
---

### Post by vevel on 2010-06-02
This is probably very basic -- I'm trying to find the best way to keep a patched version of a package from being overwritten during upgrades.
I've decided to install a ppa version of .deb file (via 'dpkg -i'  ... thinking I would avoid having to manually run a patch against the code), but if I run an 'apt-get update' now, my ppa version will be overwritten by default.  Is there a better or a standard way to do this?
Thanks.

---

### Post by SevenMachines on 2010-06-03
i believe if you select a package with multiple versions in synaptic and choose package->force version you can do what you're looking for. if you want to do it manually you could add something to apt- preferences ( see man apt_preferences  for examples ) with a priority higher than 1001(?), something like
Package: <my-package>
Pin: origin <my-ppa>
Pin-Priority: 1001

though i cant remember ever doing that manually so i'm not sure quite what the entry should be :)

---

### Post by vevel on 2010-06-03
> **SevenMachines said:**
> 

Thanks!  That set me on the right track.   
Was looking at man apt_preferences, and somehow got the idea to check wajig, which got me to look for an analogous aptitude command.  (Since this is on a server, no synaptic as installed.)
I think this does what I need:
1) aptitude hold <pkg>
or, after apt-get install wajig ,
2) wajig hold <pkg>

To unhold, one can use 'unhold' as the arg instead of 'hold'.

I ended up using the wajig version, since aptitude (helpfully?) wanted to clear out my old linux headers. 

This works at least for apt-get upgrade, which will show the package in question as being kept back. 

I'm still looking into the apt-preferences -- it looks everything is assumed to be 'normal', so my /etc/apt/preferences.d directory and /etc/apt/preferences file are completely empty without doing any tinkering.   No changes are made there by the 'hold' methods above, so this is apparently tracked by a different mechanism.  

Thanks again, seven.

---

