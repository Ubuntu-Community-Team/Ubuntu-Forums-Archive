---
title: "problem creating local repository"
date: 2006-06-17
forum: Repositories &amp; Backports
---

### Post by jeroen2 on 2006-06-17
Hello,

I run kubuntu 5.10 breezy badger. I'd like to make a local repository in case I need to install in the absence of an internet connection.

I found the apt-move howto at:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

I followed the instructions succesfully and have a repository ready on my harddrive (I choose not to burn to cd). I've added the repository to my sources.list using adept to add the following line:

deb file:///home/username/local breezy main restricted non-free contrib

The problem:
The repo seems to mount fine in adept. But I'm missing some packages. Notably those in pool/contrib/. I also don't understand why there is a contrib folder under pool, but not under dists/breezy. I realized putting contrib in the sources.list entry was probably useless, but I tried it anyway: no luck. Even more strange: the packages in pool/non-free don't show up in adept, even though a dists/breezy/non-free exists.... I know I can install these packages by hand. No problem there. I'd just like to have it all at my command from adept....

Thanks for your time
Jeroen

---

