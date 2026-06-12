---
title: "Git advices?"
date: 2007-08-14
forum: Programming Talk
---

### Post by aks44 on 2007-08-14
I'm willing to migrate my projects from Subversion to Git (mainly because one of them is becoming a branches hell, it seems that Git can really help with that).

Has anyone around here some experience with Git, who could advise me a good SCM front-end?

All the front-ends I know of (Cogito, StGit, Git-gui, gitk, qgit) are (apparently, from what I read) lacking many features, but I'd be glad to hear your experiences with them anyway.

For the record, concerning Subversion: I am used to Tortoise on Windows (the best out there IMHO, mainly due to the shell integration), and KdeSvn on Linux.

---

### Post by pmasiar on 2007-08-14
23 views and no help...

I know next to nothing about distributed SCM, but IIRC Ubuntu's Launchpad uses bazaar-NG for a reason, so bzr would be *my* first choice for a ubuntu-related (and developed in ubuntu) project. I would expect bzr be more user-friendly, or at least ubuntu-developer-friendly :-) 

But then, your project might be closer to kernel, and so learning git could make more sense...

---

### Post by aks44 on 2007-08-14
> **pmasiar said:**
> 23 views and no help...
What a shame... is everybody out there using SVN, or worse using no SCM at all? ;)

> **pmasiar said:**
> I know next to nothing about distributed SCM, but IIRC Ubuntu's Launchpad uses bazaar-NG for a reason, so bzr would be *my* first choice for a ubuntu-related (and developed in ubuntu) project. I would expect bzr be more user-friendly, or at least ubuntu-developer-friendly :-) 

But then, your project might be closer to kernel, and so learning git could make more sense...

Well, both projects I currently work on are neither close to the kernel, nor to Ubuntu itself (apart that I use Ubuntu to develop them).

One is a cross-compiled (Linux/Windows) Qt GUI application, the other one is a CGI web site. Both are *at least* distro-agnostic (thanks to KDevelop I use auto-tools, I would have had hard time setting this up by hand), the Qt GUI is even fully cross-platform for now. Well, the CGI web site will have to run on Debian for now, but this may evolve when/if I redistribute it.

I elected Git over other alternatives mainly because of its advertised branching/merging capabilities (which are a pain in the *** as far as SVN is concerned, I don't even dare to imagine how CVS handles this). Revision signing will also be a great feature as soon as those projects will come public.

Anyway I'll have a closer look to Bazaar, and I'll report here when I have more info on it.


Thanks for the suggestion. Keep'em coming... :)


EDIT: be it Git, Bazaar or whatever else, the thing is: I'm doing this on my spare time so I'd really like not to bother with "cryptic" command lines. Not that I'm terminal-relunctant, but anyone who ever used Tortoise will easily guess what I mean. ;)

---

### Post by aks44 on 2007-08-16
*Bump* (just in case...)

---

### Post by psusi on 2007-08-16
I use tortoiseSVN at work where I am forced to use windows.  I have been playing with git though to track the kernel development and it seems really nice.  I just use the command line tools, and gitk, which is a python based gui history browser.  I tried to use cogito a bit but aside from colorizing the log output, I couldn't find that it did anything that git itself doesn't.

---

### Post by aks44 on 2007-08-16
> **psusi said:**
> I use tortoiseSVN at work where I am forced to use windows.
Same here. Not that I am fond of Windows but so far Tortoise is one of the best SCM front-ends I dealt with (Eclipse's SVN is a bit better IMHO). Too bad SVN itself sucks for branching/merging.

> **psusi said:**
> I have been playing with git though to track the kernel development and it seems really nice.  I just use the command line tools, and gitk, which is a python based gui history browser.  I tried to use cogito a bit but aside from colorizing the log output, I couldn't find that it did anything that git itself doesn't.

Thanks for the feedback. This seems to confirms what I read, ie. Cogito is not quite useful.

Granted, Tortoise gave me "bad habits" due to its thight integration with the shell. I guess I'll have hard time finding an equivalent product for such a young SCM as Git.

---

