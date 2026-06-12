---
title: "Problem installing perl modules"
date: 2007-06-29
forum: Programming Talk
---

### Post by tr333 on 2007-06-29
Whenever I try to install a perl module, i get an error saying
```
[ERROR] Unable to create a new distribution object for 'module::whatever' -- cannot continue
```
What is this error telling me?

---

### Post by mzar on 2007-06-30
You using souce code to compile or what?
How about **sudo apt-cache search mod_perl**. Hope that will solve your problem.

---

### Post by tr333 on 2007-06-30
I am installing modules using the cpanplus shell.  The problem seems to occur when installing some modules, but not others :?
Here is some sample output from cpanplus when it failed:
```
[MSG] [Sun Jul  1 13:18:07 2007] Checking if source files are up to date
[MSG] [Sun Jul  1 13:18:07 2007] Updating source file '01mailrc.txt.gz'
[MSG] [Sun Jul  1 13:18:07 2007] Trying to get 'http://mirror.cse.unsw.edu.au/pub/CPAN/authors/01mailrc.txt.gz'
[MSG] [Sun Jul  1 13:18:24 2007] Updating source file '03modlist.data.gz'
[MSG] [Sun Jul  1 13:18:24 2007] Trying to get 'http://mirror.cse.unsw.edu.au/pub/CPAN/modules/03modlist.data.gz'
[MSG] [Sun Jul  1 13:18:26 2007] Updating source file '02packages.details.txt.gz'
[MSG] [Sun Jul  1 13:18:26 2007] Trying to get 'http://mirror.cse.unsw.edu.au/pub/CPAN/modules/02packages.details.txt.gz'
[MSG] [Sun Jul  1 13:18:29 2007] Rebuilding author tree, this might take a while
[MSG] [Sun Jul  1 13:18:32 2007] Rebuilding module tree, this might take a while
[MSG] [Sun Jul  1 13:19:16 2007] Writing compiled source information to disk. This might take a little while.
[MSG] [Sun Jul  1 13:19:19 2007] Trying to get 'http://mirror.cse.unsw.edu.au/pub/CPAN/authors/id/G/GA/GAAS/CHECKSUMS'
[MSG] [Sun Jul  1 13:19:20 2007] Checksum matches for 'Tkx-1.04.tar.gz'
[MSG] [Sun Jul  1 13:19:20 2007] Extracted 'Tkx-1.04/'
[MSG] [Sun Jul  1 13:19:20 2007] Extracted 'Tkx-1.04/Tkx.pm'
[MSG] [Sun Jul  1 13:19:20 2007] Extracted 'Tkx-1.04/t/'
[MSG] [Sun Jul  1 13:19:20 2007] Extracted 'Tkx-1.04/t/mega-config.t'
[MSG] [Sun Jul  1 13:19:20 2007] Extracted 'Tkx-1.04/t/utf8.t'
[MSG] [Sun Jul  1 13:19:20 2007] Extracted 'Tkx-1.04/t/LabEntry.t'
[MSG] [Sun Jul  1 13:19:20 2007] Extracted 'Tkx-1.04/t/mega.t'
[MSG] [Sun Jul  1 13:19:20 2007] Extracted 'Tkx-1.04/t/nul-char.t'
[MSG] [Sun Jul  1 13:19:20 2007] Extracted 'Tkx-1.04/t/tcl.t'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/t/tk.t'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/tkx-ed'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/Tkx/'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/Tkx/MegaConfig.pm'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/Tkx/Tutorial.pod'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/Tkx/LabEntry.pm'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/Changes'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/MANIFEST'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/META.yml'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/menu'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/tkx-prove'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/README'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx-1.04/Makefile.PL'
[MSG] [Sun Jul  1 13:19:21 2007] Extracted 'Tkx' to '/Users/tom/.cpanplus/5.8.6/build/Tkx-1.04'
[ERROR] [Sun Jul  1 13:19:22 2007] Could not run '/usr/bin/perl Makefile.PL': Checking if your kit is complete...
Looks good
 -- cannot continue
[ERROR] [Sun Jul  1 13:19:22 2007] Unable to create a new distribution object for 'Tkx' -- cannot continue
```

---

