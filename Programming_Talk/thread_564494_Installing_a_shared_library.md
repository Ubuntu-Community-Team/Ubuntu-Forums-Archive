---
title: "Installing a shared library"
date: 2007-10-01
forum: Programming Talk
---

### Post by bcw on 2007-10-01
Hello,

I'm writing an input system for tablet computers (for linux).  I've done some experiments to verify I can basically do what I want, and now it's time to back up, and set up the proper infrastructure for developing software that can be installed, un-installed, not conflict, etc.

A bit of background so you can gauge your answers...

I write Java for a living, so I'm technical enough, but I haven't written C for 9 years, and even then it wasn't much.  I have a cursory understanding of make, gcc, and I've read a bit about linking.

I've run 'make && make install' many times, but not much more than that.

What I'm writing now is a couple of libraries to be called from client programs.  I am using kdevelop, which has provided me with a project skeleton for shared libraries - I used that for my experiments.  The project uses Cmake, which looks nice enough, and I may use that as I pull this out to be stand-alone.

Some questions:

1) I tried (manually) putting the library I made into /usr/local/lib and running ldconfig.  This did not make the library available system-wide.  I thought /usr/local/lib was the place for non-system libraries (not-Ubuntu-approved-yet) and that it would be included for 'aftermarket' packages like mine.  Is this not the case, or is my system not set up properly?

2) Most libraries have version numbers appended.  Mine does not by default.  How is that done?  Is it a make setting (forced), or handled by ldconfig, or?

3) I can search the web and find many pages about programming Linux, libraries, etc., so I don't need general recommendations.  But that's a lot of reading to winnow through, so if you know of some resources that are tightly appropriate to Ubuntu development/setup practices that would cut through my reading burden, please recommend them.

4) (delicately - intending no disrespect)  There isn't as much in this forum as I expected.  This makes me wonder if there is another place Ubuntu programmers hang out, and if I should ask my questions there?

In a while, I will announce this as a project, and then I imagine I'll get help from people to sort out issues for other distros, etc. but for now it's just me and I need to do the work to get to where I have something release-able, so I need to get to the 'make && make install' milestone.  The programming isn't a problem, but I don't want to do a lot more (now I know it's feasible) without that infrastructure.

Thanks for your answers,
Bret

---

### Post by scruff on 2007-10-01
Sounds like /usr/local/lib may not be in your PATH. Try this:

```

sudo ldconfig -v <some_path>

```

---

### Post by bcw on 2007-10-01
> **scruff said:**
> Sounds like /usr/local/lib may not be in your PATH.

Thanks.  I will try your suggestion.

I'm particularly interested in knowing, however, is /usr/local/lib **supposed** to be in my path, as I need to know if I can target that for a standard [X,K]ubuntu install?  Is my own system broken (non-standard), or do all [X,K]ubuntu systems **not** include /usr/local/lib by default?

I'll be releasing this as a package in time, so I want to know what to set up for, rather than just how I might hack things on my own system.

Thanks for your help,
Bret

---

### Post by scruff on 2007-10-01
I just checked on my home machine, and no - it isn't there by default. 

So - sometime during the application installation you can drop a .conf file into /etc/ld.so.conf.d/ containing the string /usr/local/lib then run ldconfig.

Seems odd that /usr/local/lib isn't there by default though. I'm new to 'buntu (gentoo user for 4 years) so I'm not sure what there standard convention is. I know on Gentoo and red hat-like OS's /usr/local/lib is included by default.

It's easy enough though to check what distro it's being installed on and set up configuration accordingly if necessary, then have the install run ldconfig.

---

