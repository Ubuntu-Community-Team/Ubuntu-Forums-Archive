---
title: "How to uninstall a program?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Oputres on 2008-06-08
Hi!

I installed a download manager for Emusic.com, namely EmusicJ ([http://www.kallisti.net.nz/EMusicJ/Download](http://www.kallisti.net.nz/EMusicJ/Download)). It was a tar.gz file that I installed in my user folder.

Now I want to delete that program but how do I uninstall it? It has no uninstall file and it is not shown under Add/Remove... As a former Windows XP user (god I love Ubuntu) I'm always have the registry in mind and I guess there is some resemblance in Ubuntu. Or is there not? Can I just delete the folder?

*neeeewwbiieee* :rolleyes:

---

### Post by Xerp on 2008-06-08
Yes, you can just delete it. There is no registry to go wrong.

---

### Post by crashsystems on 2008-06-08
Oputres, most programs have debian/ubuntu package files that you can download, if they are not already in the repository. Though Add/Remove wouldn't list one of these self-downloaded files, Synaptic would.

However, the program you downloaded is in a tar.gz file, which is basically the equivalent to a .zip file on Windows. So wherever you extracted it's contents, just delete them, and you're good to go. Unlike Windows, which saves software configuration in that horrible Registry, Linux saves software settings as simple text files in the /etc directory.

Anyways, welcome to Linux!

---

