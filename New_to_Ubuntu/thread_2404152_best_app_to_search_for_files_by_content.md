---
title: "best app to search for files by content"
date: 2018-10-20
forum: New to Ubuntu
---

### Post by otlichnik73 on 2018-10-20
Hi there, everyone! I am on a quest to find THE MOST NEWBIE-FRIENDLY way to search BY CONTENT the files of the following types: .txt, .doc., .pdf, .odf, .html
So far, my solution is Recoll with "helpers" installed - definitely does the job, but the installation and running of it is not very newbie frienly.
Tried Catfish - can only search content of .txt files. Same in Mate-search-tool someone recommended.

I need to find a solution for not-so-tech-minded colleagues in the office switching from Windows to Linux.
They miss the easy search in the Windows Explorer...
Any suggestions?:KS
(Using Linux Mint 18 and Ubuntu 18)

---

### Post by TheFu on 2018-10-21
I waited a day .... 
I use recoll, but with a different CLI front-end.  Most end-users wouldn't like the shell interface that I use.

You can  search for alternatives on AlternativeTo.net  [https://alternativeto.net/software/recoll/](https://alternativeto.net/software/recoll/)

---

### Post by otlichnik73 on 2018-10-22
YES!! Docfetcher is the winner!! Installation is a bit tedious, must install Runtime Java, then install from a .zip archive. It does not add itself to applications menu, you have to launch it from a .sh file, and the help menu is hidden in the folder in the archive. But, once you sort it all out - 
you don't have to worry about installing any "helpers" as with Recoll, it searches ALL formats [IMG]https://forums.linuxmint.com/images/smilies/icon_biggrin.gif[/IMG]
website: [http://docfetcher.sourceforge.net/en/download.html](http://docfetcher.sourceforge.net/en/download.html)
how to install java: [https://www.pcsteps.com/5492-how-to-ins ... nt-ubuntu/]("https://www.pcsteps.com/5492-how-to-install-java-linux-mint-ubuntu/")

---

### Post by TheFu on 2018-10-22
I would urge caution using any tools that require a manual installation.  Signing up to manually maintain a package like this isn't fun.  Add a reoccurring reminder to check for and install updates at least monthly.  This is VERY, VERY important for java runtimes and java libraries.

---

