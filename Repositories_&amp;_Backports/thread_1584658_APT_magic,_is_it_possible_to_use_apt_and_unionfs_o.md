---
title: "APT magic, is it possible to use apt and unionfs overlays?"
date: 2010-09-29
forum: Repositories &amp; Backports
---

### Post by Erwin Van de Velde on 2010-09-29
Hi all,

I have to maintain several system images which are almost the same, except for a few files and/or packages.
I decided to try not to maintain the images separately, but together using unionfs-fusion:
I created a shared platform with a base Ubuntu installed and then I created several overlays and mounted the different images as unionfs-fuse directories:
e.g. for image1, I mounted platform (ro) and image1_overlay (rw) using a unionfs-fuse, so when i change something in the image1 directory, it gets written to the image1_overlay and when I change something in the platform directory, it also changes image1.

This solutino works great for configuration files etc, but now I am wondering how I can make this work for packages. I could only do aptitude update in the platform (chrooted), so the repository lists stay the same for all the images, but what happens when I install packages? I found /var/lib/apt/extended_states and I think it is rather easy to keep that one okay by using diffs for the different images and concatenating these diffs to the extended_states of the base platform, but is this enough? Are there other files I should worry about? Better solutions to this problem?

Do not hesitate to ask for more clarification as it may seem quite complicated.

Thanks for reading all this and hopefully also for your brilliant reply!!! :)

---

