---
title: "Can't install libunique-dev dependency"
date: 2010-11-26
forum: Packaging and Compiling Programs
---

### Post by kid-pro-quo on 2010-11-26
I'm running an up-to-date Lucid (10.04) 64-bit.

When I'm trying to compile Postler ([http://launchpad.net/postler](http://launchpad.net/postler)) it fails during the configure stage with this:

.```
..
Checking for gio-2.0 >= 2.16.0              : yes 
Checking for unique-1.0 >= 0.9              : Package unique-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `unique-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'unique-1.0' found 
/home/sam/Documents/Programming/postler/wscript:97: error: the configuration failed (see '/home/sam/Documents/Programming/postler/_build_/config.log')
```

If I try to install the libunique-dev dependency to resolve this it won't install. The error I get is this:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libunique-dev: Depends: libgtk2.0-dev (>= 2.11.0) but it is not going to be installed
E: Broken packages
```

Trying to install this dependency manually fails with this error:

```

...
The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.1-0ubuntu2) but 2.20.1-0ubuntu2+menuproxy11 is to be installed
E: Broken packages

```

Any ideas how I might solve this?

---

### Post by gmargo on 2010-11-27
It looks like you've installed the "menuproxy11" version of libgtk2.0-0, so you have to install the matching version of libgtk2.0-dev, but it looks like you're trying to install the standard repository version of libgtk2.0-dev.

---

### Post by kid-pro-quo on 2010-11-27
I'm pretty sure the -menuproxy11 package is from when I tried out Unity a while back. I can't seem to get rid of it. The PPA has been removed but synaptic etc still think that's the most recent version of libgtk2.0-0.

If I try to force the "older" (non -menuproxy11) version synaptic threatens to remove half my system.

Any ideas?

---

### Post by gmargo on 2010-11-27
To force the current repository version of libgtk2.0-0, try this:
```

$ aptitude -s -V install libgtk2.0-0=2.20.1-0ubuntu2

```(-s says only show what would happen, remove the -s to make it so.)

**aptitude** might make a suggestion as to what to do - that's what I like about **aptitude** over **apt-get**.  

If you have other menuproxy11 packages, you'll probably have to replace them all simultaneously with additional "package=version" arguments.

And make sure that the menuproxy11 ppa is removed from your software sources (/etc/apt/sources.list or through the gui), and that you do a normal update/upgrade first.

---

### Post by kid-pro-quo on 2010-11-28
Thankyou. That solved my problem perfectly.

I've still got problems of missing vapi files but that's probably more suited to a separate thread.

Thanks again gmargo.

---

