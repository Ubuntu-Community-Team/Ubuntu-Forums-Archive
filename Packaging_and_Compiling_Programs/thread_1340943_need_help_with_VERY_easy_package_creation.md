---
title: "need help with VERY easy package creation"
date: 2009-11-29
forum: Packaging and Compiling Programs
---

### Post by Axx83 on 2009-11-29
Hi guys. [Here]("http://ubuntuforums.org/showpost.php?p=8315253&postcount=1") I made a power saving guide. The problem is that I would prefer the 3 scripts that are included to be in a package for ease of use.

We're talking about a package with only these 3 little scripts that have to go in /usr/lib/pm-utils/power.d/ that's it, nothing else.

Should there be dependencies ? I guess it has to be karmic only.

Please help, I'm SO new to this

---

### Post by Locke_99GS on 2009-11-30
I use something called *epm* for packaging simple things that don't need to be compiled, like scripts, documents, images, things of that sort.

Any programs that your script uses should be added as a dependency, including the shell you used. Remember, a script written for zsh may not function in bash, and some installs (server for instance) will not include many utilites we take for granted.

Scripts should be packaged for all architectures. 

*epm* is available in the repos, and is very easy to use.

---

