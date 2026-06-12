---
title: "Opening Gnome-Do source code in MonoDevelop"
date: 2012-04-05
forum: Programming Talk
---

### Post by pt123 on 2012-04-05
I was wondering how do you open the gnome-do src code as a solution/project in mono develop, I only have experience with Visual Studio, so I have no idea how it's done in the Linux world.

The src code is here, I cannot find a .sln file
[https://launchpad.net/do/trunk/0.8.5/+download/gnome-do-0.8.5.tar.gz](https://launchpad.net/do/trunk/0.8.5/+download/gnome-do-0.8.5.tar.gz)

---

### Post by CynicRus on 2012-04-06
[https://answers.launchpad.net/do/]("https://answers.launchpad.net/do/") - I think it is a chance to get an answer to your question above.

---

### Post by directhex on 2012-04-06
The sln and csproj files are not shipped in tarball releases.

If you grab the source from version control, they are included.

---

### Post by pt123 on 2012-04-08
> **CynicRus said:**
> [https://answers.launchpad.net/do/]("https://answers.launchpad.net/do/") - I think it is a chance to get an answer to your question above.
Thanks I have now posted a question there.

> **directhex said:**
> The sln and csproj files are not shipped in tarball releases.

If you grab the source from version control, they are included.

I downloaded using bzr and there was no .sln file.

---

### Post by directhex on 2012-04-08
> **pt123 said:**
> Thanks I have now posted a question there.



I downloaded using bzr and there was no .sln file.

[http://bazaar.launchpad.net/~do-core/do/trunk/view/head:/Do.sln](http://bazaar.launchpad.net/~do-core/do/trunk/view/head:/Do.sln) ?

---

### Post by pt123 on 2012-04-09
> **directhex said:**
> [http://bazaar.launchpad.net/~do-core/do/trunk/view/head:/Do.sln](http://bazaar.launchpad.net/~do-core/do/trunk/view/head:/Do.sln) ?

Ok I went and downloaded the 0.8 version
[http://bazaar.launchpad.net/~do-core/do/0.8/files](http://bazaar.launchpad.net/~do-core/do/0.8/files)

as Ubuntu ships with 12.04 ships with 0.85

that has no .sln file. 

But the Trunk version as you pointed has it.

---

