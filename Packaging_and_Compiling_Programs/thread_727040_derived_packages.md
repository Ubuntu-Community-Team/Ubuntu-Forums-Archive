---
title: "derived packages"
date: 2008-03-17
forum: Packaging and Compiling Programs
---

### Post by jetsaredim on 2008-03-17
Ok, so, I'm not a total packaging n00b, but I've run into something I'm not sure how to solve.

I want to fix the issue with mozilla-mplayer that the mplayer plugins aren't showing up in Firefox 3 (pretty easy fix).  The problem is that after I've updated my source and added my entry to the changelog, when I go to run debuild to build the package, I end up with mplayerplug-in files, not mozilla-mplayer files.  

I'm pretty sure this has to do with the fact that mozilla-mplayer lists mplayerplug-in as the source package in debian/control.  Thing is, I can't seem to figure out how to get mozilla-mplayer built by itself.  I also debuild -S -sa to get the source.changes files (which were also named mplayerplug-in) to try and upload the package to my PPA and get it built to see if mozilla-mplayer would somehow come from the actual build.  Alas, this didn't work either.

Any suggestions?  I've been asking on #ubuntu-motu and #lanuchpad, but no one seems to understand or want to help.

Thanks,
Jared

---

