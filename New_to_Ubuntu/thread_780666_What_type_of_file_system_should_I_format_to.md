---
title: "What type of file system should I format to?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by sithpigeon on 2008-05-03
Hi,
I'm new to the forums here but have been working with Ubuntu for about 3 weeks. I just installed xubuntu onto a reconstructed (meaning I took three old computers and made one OK computer) that used to have windows nt: workstation on it. I only had to small (7 gb) hard drives so I slaved one to the other. The slave was set to an ntfs filesystem and still is but the other one has xubuntu installed on it. I'm going to reformat the ntfs and was wondering what filesystem I should make it so that it fits in with the master drive. This is more of an opinion question, I just want to know what people think. Thanks

---

### Post by MockY on 2008-05-03
Ext3 is the default filesystem for Ubuntu, so I would go with that for the boot disk. All of my slaves however, are formatted with RaiserFS since it works the best for me in terms of speed and space utilization.

---

