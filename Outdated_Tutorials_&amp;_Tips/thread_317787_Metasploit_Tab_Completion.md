---
title: "Metasploit Tab Completion"
date: 2006-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by upidivl on 2006-12-13
I recently installed Metasploit and wanted to install the tab completion capability but was getting this error from this command:

```
perl Makefile.PL

Could not find neither libtermcap.a, libncurses.a, or libcurses.
```

After a *very* long time spent Googling, I discovered that you need to install these two packages to get the correct library files:

```
sudo apt-get install libreadline5-dev libncurses5-dev
```

I also ran into a permission error when running make install.  Just be root when running make install and everything will be fine!

Hope this helps some people.

---

### Post by H-ideas on 2010-04-30
> **upidivl said:**
> Hope this helps some people.
It did, thanks for posting!

---

