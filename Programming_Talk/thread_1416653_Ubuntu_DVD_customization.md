---
title: "Ubuntu DVD customization"
date: 2010-02-26
forum: Programming Talk
---

### Post by Shnatsel on 2010-02-26
I'm developing an Ubuntu remix, and it's far too large to fit into a CD. Ubuntu DVD images have both text-based and graphical installers, I'd like to have both of them in my remix too. Unfortunately, if I remove language extra language packs and apply the patches from my remix, I get a 3.8 Gb image - more than 2 Gb disappear into nowhere. I googled for a while and found that DVD image is so huge because it contains mirrors of Main and Restricted repos. Is there any way to remove those mirrors from the image?

---

### Post by Shnatsel on 2010-03-19
Hmm... that's a pity. I've written a [simple sh script]("http://dl.dropbox.com/u/5279564/DVD_cleanup_script_relative") which removes all packages which aren't included in CD image except proprietary nvidia drivers (removing them crashes Jockey). Everything works fine except for debian-installer - it fails to load installer components. What can that be caused by? Is there any log created on installation attempt that I can examine?

---

