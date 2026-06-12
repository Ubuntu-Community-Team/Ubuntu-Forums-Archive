---
title: "What repository to add to get new stuff"
date: 2005-02-21
forum: Repositories &amp; Backports
---

### Post by mbourd25 on 2005-02-21
Hi folks, which repository I should add to my source.list to get the latest builds of software? Right, I used the ones that are displayed at the ubuntuguide.org under add estra repository, but some links are still pointing to openoffice at version 1.1.2 when it's at version 1.1.4 and so one.

Any info would be great, thanks.

---

### Post by kassetra on 2005-02-21
[QUOTE=mbourd25]Hi folks, which repository I should add to my source.list to get the latest builds of software? Right, I used the ones that are displayed at the ubuntuguide.org under add estra repository, but some links are still pointing to openoffice at version 1.1.2 when it's at version 1.1.4 and so one.

Any info would be great, thanks.[/QUOTE]

If you want anything newer than the extra repositories, there are three methods: warty-backports, hoary repositories, or debian repositories.

Hoary is in development, but here is how you add hoary repositories:
Copy all of the repositories that say "warty" in your sources.list and change warty to hoary.

Warty-Backports are stable releases of software for warty from the hoary archive.
Here is the list of [repositories]("http://backports.ubuntuforums.org/").

As for debian archives, you'll have to go to [http://www.debian.org]("http://www.debian.org") to find them.

---

### Post by mbourd25 on 2005-02-22
Thanks Kassetra, that's the info I was looking for.

Also, where can I find the info to explain to me what do the extensions mean when you enter a repository?

Ex: deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted

What does the main, universe, multiverse and restricted do?

Thanks.

---

### Post by lao_V on 2005-02-22
[QUOTE=mbourd25]

What does the main, universe, multiverse and restricted do?

Thanks.[/QUOTE]

That information you will find over here

[http://www.ubuntulinux.org/ubuntu/components/document_view](http://www.ubuntulinux.org/ubuntu/components/document_view)

---

