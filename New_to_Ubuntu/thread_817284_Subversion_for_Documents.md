---
title: "Subversion for Documents?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Awayne on 2008-06-03
I'm very very new to Subversion. The only thing I really know about revision systems is the standard "co http://url.tld/dir/trunk/" etc. I'm about to start a huge project I would like synced over a few different systems. I was considering trying to use Subversion to sync all documents, pdfs, .docs and other files belonging to them. But I'm not sure if this is the best way to go. I have to be able to use this from my central server and be able to get the latest revised documents on Windows XP, Ubuntu and another Linux system. Is this possible with Subversion? I know how well it does with code and I know a lot of big projects use it as it is the best for what they use. But I thought I would gather opinions and help over this since I'm still new. Any help and or opinions are always appreciated.
Thanks.

---

### Post by neurostu on 2008-06-03
So some documents will sync well with subversion and others wont.  Subversion does  a line by line comparison of the documents and merges the differences, this is great for coding, but some documents like .pdf, .svg, .doc  don't necessarily  merge well, sometimes they do but a lot of times they don't.    In this case you would want to completely replace the current file with a new one, which keeping track of the old file. It will take more time and space but at least it will track all your versions.

It is totally possible to set up subversion on a server, in fact the majority of people do it that way.  If your not to server savy its really easy to use subversion over ssh. 

This way you setup the repo on one computers, and then the other computer's access the repo over ssh.  I've done it this way a couple times and it was pretty easy to setup.

---

### Post by The Cog on 2008-06-03
Subversion is able to handle binary files, so it will do the job for you. It may well just end up effectively keeping a copy of each version - I doubt it will be able to calculate smallish differences to store for hte changes in compressed files such as OpenOffice docs. So expect the storage requirements to match accordingly.

---

### Post by Awayne on 2008-06-04
Thanks for the replies. I've setup Subversion and I have WebSVN running on it to provide web access to it. Keeping track of every change, be it small or large is critical to what I'm doing. Subversion seems to work okay, I just need to learn how to use it now. As with anything new, always takes some time to learn.
[quote=neurostu]some documents like .pdf, .svg, .doc don't necessarily merge well, sometimes they do but a lot of times they don't.[/quote]
Well mainly open documents like text files should be dealt with accordingly shouldn't they? I know how well it handles source code and heard it does documents too. It really would streamline everything and save hours.
[quote=The Cog]Subversion is able to handle binary files, so it will do the job for you.[/quote]
Thanks, good to know. I will probably end up storing binary files on it for some reason or another. :)

---

### Post by neurostu on 2008-06-04
> 
Well mainly open documents like text files should be dealt with accordingly shouldn't they? I know how well it handles source code and heard it does documents too. It really would streamline everything and save hours.

Yes it will do a fine job with text documents.

---

