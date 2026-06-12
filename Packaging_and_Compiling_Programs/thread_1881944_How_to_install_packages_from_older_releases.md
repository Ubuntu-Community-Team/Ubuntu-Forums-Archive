---
title: "How to install packages from older releases?"
date: 2011-11-16
forum: Packaging and Compiling Programs
---

### Post by searchfgold6789 on 2011-11-16
Hi,
I'd appreciate if anyone could help me with this: I'm compiling a program, and one of its dependencies is from an old release of Ubuntu. As Ubuntu developed, the package (libgtkmm2.0-dev) was no longer offered, of course. The package in turn depends on many other "-dev" packages. I don't want to go off and find the source code and go on a literally endless compiling spree! Is there some way I could add the source of these packages (e.g. a ppa) to my sources.list or something? Are the Ubuntu mirrors of any use? Could I just download them all from somewhere? :confused:
Thank you for the help. I'm very glad to be a part of this great community!

---

### Post by hwttdz on 2011-11-16
You should be able to just add the old repositories to your /etc/apt/sources.list, though I'd do it in a maverick_sources.list in sources.list.d (whatever the .d in /etc/apt/ is named).  Then it will prefer the newer version, but if you need the older version you can easily use that.

---

### Post by searchfgold6789 on 2011-11-16
Thank you for the response! I have a couple questions still though; a) how do I do that and b) what are the locations of the old repositories?
Thanks again!
 - search

---

### Post by hwttdz on 2011-11-16
Looking at my /etc/apt/sources.list I see I have a 

```
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ natty-security multiverse
```

line, which says a few things.  
1) the deb tells apt-get this is a deb repo (tells it to look here for certain types of things, and to expect to find .deb packages)
2) it tells you where the repo lives, living in nyc I use one that lives at columbia.edu
3) natty-security, tells you 
  a) that this is a natty repo, and 
  b) that it's security, which relates to when these updates get installed
4) this is multiverse code, so that what the last bit is, i.e. only use this repo if the user has the "multiverse" box checked in synaptic.

So if I wanted older packages from this repo, I'd add a similar line, but replace natty with maverick.  But like I said I find it easier if I keep what I'm doing and what the os is doing separate, so you have the /etc/apt/sources.list.d folder, and I'd make a file in there and call it something like old_repos.list (must end in .list), and put essentially the contents of /etc/apt/sources.list in it, but replace all occurrences of oneric/natty/whatever with the older one you want to use.

Small print: you'll be using sudo to add the old repos, and of course to install packages, so there is the possibility of breaking your system. This is another advantage of doing it in a separate file, if things go south, move the old_repos.list to old_repos.not_list and update & upgrade and that should pull you back to the current versions.

---

### Post by searchfgold6789 on 2011-11-16
Thank you so much! Thanks to you I have it all figured out.
 - search

---

### Post by searchfgold6789 on 2011-11-16
Hi,
I'm trying to compile a program... and it says it needs gtkmm-2.0, gthread-2.0, and gstreamer-0.6.
```
checking for gtkmm-2.0 gthread-2.0 gstreamer-0.6... Package gtkmm-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtkmm-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtkmm-2.0' found Package gthread-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gthread-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gthread-2.0' found Package gstreamer-0.6 was not found in the pkg-config search path. Perhaps you should add the directory containing `gstreamer-0.6.pc' to the PKG_CONFIG_PATH environment variable No package 'gstreamer-0.6' found
configure: error: Library requirements (gtkmm-2.0 gthread-2.0 gstreamer-0.6) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```I can't find them or the -dev packages in synaptic, how do I install them?
If they are found in an older version of Ubuntu I could always add the source to my sources.list, and I tried it with the Hardy sources but they didn't work :(
 - search

---

### Post by jonobr on 2011-11-16
Hey

What are you trying to install?

---

### Post by oldos2er on 2011-11-16
Moved to Packaging & Compiling Programs.

You might want to mention what program you're trying to compile.

Edit: Threads merged. Please don't start more than one thread per issue.

---

### Post by searchfgold6789 on 2011-11-17
OK... I have no idea what just happened but... (thanks mods for your invaluable cleanup work on my behalf!)

The program I'm compiling is Liar Liar 0.5.2 - I plan on making a tutorial for compiling and using this program under 11.10, if it turns out to be possible, later.

---

### Post by searchfgold6789 on 2011-11-17
OK, I found out that the reason I couldn't install it from the old sources is because it was deleted. So... is there any hope at all?

---

### Post by searchfgold6789 on 2011-11-23
OK back to square one. >.< I have tried adding several things to my sources.list, many of which I have found online from old ubuntu package archives. But none of them worked. If anyone knows how to install libgtkmm2.0-dev I would appreciate the help.
My exact error message is this:
```
checking for gtkmm-2.0 gthread-2.0 gstreamer-0.6... Package gtkmm-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtkmm-2.0.pc' to the PKG_CONFIG_PATH environment variable 
No package 'gtkmm-2.0' found 
Package gthread-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gthread-2.0.pc' to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found 
Package gstreamer-0.6 was not found in the pkg-config search path. Perhaps you should add the directory containing `gstreamer-0.6.pc' to the PKG_CONFIG_PATH environment variable 
No package 'gstreamer-0.6' found
configure: error: Library requirements (gtkmm-2.0 gthread-2.0 gstreamer-0.6) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```
 - search

---

### Post by searchfgold6789 on 2011-11-23
SOLVED.
I looked up someone on these forums who had installed the same package, libgtkmm2.0-dev, and they had posted in August 2006. So I added the edgy repos from old-releases.ubuntu.com/ubuntu and BAM it worked!
 - search

---

