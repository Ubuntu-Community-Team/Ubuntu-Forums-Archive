---
title: "Question: sources.list"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by rgriffiths on 2008-07-14
Hi All

I have a simple question on the ubuntu sources list file.  Does the order of the repositories listed in the file have an effect?  For example, if two repositories offer the same software, but one offers the older version, do I need to list the repository with the newer version first, or will ubuntu automatically look in all repositories for the newest version?

Thanks,
R

---

### Post by Valsodar on 2008-07-14
I believe ubuntu will look for the newest version.

---

### Post by bumanie on 2008-07-14
Order doesn't matter, all repositories on the /etc/apt/sources.list is checked for the latest 'officially' available software/updates via the canonical/mirror servers.

---

### Post by aysiu on 2008-07-14
I think you can specify in the Synaptic Package Manager or Software Sources what preference you have for versions, but generally the package manager will go with the newest version unless you specify otherwise.

The only cases in which you should have two sources with the same software are enabling backports or proposed updates.

Do not mix and match with newer and older versions of Ubuntu (for example, a mix of Gutsy and Hardy repositories) or with Debian repositories. Mixing and matching is a quick way to break your system or end up in dependency hell.

---

