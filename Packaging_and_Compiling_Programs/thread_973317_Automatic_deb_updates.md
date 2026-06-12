---
title: "Automatic deb updates?"
date: 2008-11-06
forum: Packaging and Compiling Programs
---

### Post by Tamalin on 2008-11-06
How could I make it so that when I release a new deb package for my Applications, users can be notified of an update?  Is there something special I have to do to my site?

Help much appreciated.

---

### Post by lukjad on 2008-11-06
Well, I think that what you need to do is make a repository. Then have the users at that to their list of repositories. Or you could set up an optional mailing list, telling people when the new version is out.

---

### Post by Tamalin on 2008-11-06
How exactly do I set up a repository, or is there a good tutorial somewhere to tell me how?

Also, how do I do mailing lists.  Is there a way to do that using PHP?

Thank you, I am glad to know it is possible.

---

### Post by lukjad on 2008-11-06
I'm not an expert on this. I just read a lot. If you are looking for answers, you may want to Google for something like "Repository creation" or "How to create a repository for linux". Sorry I can't give you a better answer. Maybe someone else can help you more.

---

### Post by DJ_Peng on 2008-11-07
You could probably set up a [PPA repo]("https://help.launchpad.net/Packaging/PPA") on Launchpad. I get software updates from a number of PPA's and all I have to do is leave the PPA enabled in my repo list and when an update is available Update Manager lets me know.

---

### Post by Tamalin on 2008-11-07
Yes, but I want the packages to be located on and downloaded from my site.  Thank you though, that idea could be useful in the future.

---

### Post by DJ_Peng on 2008-11-07
Ah, ok. You'd probably have to set up a repository or just settle for sending emails when there are updates.

---

### Post by Tamalin on 2008-11-10
I read this page [Debian Howto]("http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html"), but I found that it was confusing.  I'm not really sure how to implement the instructions in the Howto, and I need a simpler way to figure it out.  What I'm not really clear on is all the binary-arm, Packages.gz, etc...  Their explanation really lacks enough detail: > Each binary-* directory contains a Packages.gz and an optional Release file; each source directory contains a Sources.gz and an optional Release file. Notice that the packages do not have to be in the same directory as the index files, because the index files contain paths to the individual packages; in fact, they could be anywhere else in the repository. This makes it possible to create pools..  What is the purpose of all the binary-* files?  Why do I need them?  What is in Sources.gz?  What is a pool anyway...  I'm sure a better tutorial would answer my questions.  Is there a good tutorial anywhere?  Thanks.

---

