---
title: "Local repository on Local Harddisk on Windows"
date: 2009-01-09
forum: Repositories &amp; Backports
---

### Post by dutch2005 on 2009-01-09
well I saw a tutorial on how to download the full repository to the harddisk...

Problem: the Pc's with ubuntu are 

1) (very) Old 
2) Only have Local network access

My "own" pc I work with has vista installed, and 2 others use this pc aswell, this one DOES have enough space left to download the repository, and I can simply install IIS7 so i can share the repo though HTTP (I could even install the FTP service so it is shared though HTTP & FTP should stuff go wrong)

I am however also on this pc kind of limited on how to download the full download and keep it up2date...

As far as I know off, only port 80 is available (the rest is closed for security)

Running it in a VMware kind of way is not an option.. as this pc only has 1Gb of ram, and such a option would need more ram..

Installing ubuntu on this pc is also no option, for various reason, like special programs running on it.

Any idea's ?:popcorn:

---

### Post by SSTwinrova on 2009-01-11
I am by no means an expert on your question, but I don't think that what you want is possible under Windows (at least not without a large amount of manual work). That said, here are my two suggestions:

**1. Use ICS to share the internet connection from your Vista box to the computers running Ubuntu**

*or*

**2. Install Ubuntu using Wubi ([http://wubi-installer.org/](http://wubi-installer.org/)) so that you can keep Windows. Then, use apt-mirror from inside Ubuntu to mirror the Ubuntu repository and let your computers update from it.**

The latter method will probably waste a ton of your bandwidth downloading unneeded packages, but it sounds like you were willing to make that sacrifice anyway. :)

---

