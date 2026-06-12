---
title: "mounting a ntfs hdd"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by boeding on 2008-04-28
Hello I have just installed ubuntu 8.04, and am trying to mount 3 hdd that i used in windows with about a terabyte of movies and music. I want to mount 3 hdd's and then shift the data around and format them to ext3. But I am having trouble mounting them. I have minimal terminal knowledge, and I think that 8.04 has ntfs-3g which is needed to do this.

Thanks,

Boeding

---

### Post by Teronap on 2008-06-17
Can you plese open a terminal, run ```
fdisk -l
``` and post the result here?

---

### Post by bumanie on 2008-06-17
To enable ntfs-3g > sudo apt-get install ntfs-3g then > sudo apt-get install ntfsconfig which is a gui frontend for mounting the ntfs drives with read/write privledges - Find the config gui under Applications --> System tools. With ntfsconfig, /etc/fstab is automatically updated. It works well with one ntfs drive, never tried three. Let us know how it goes.

---

### Post by Duck2006 on 2008-06-17
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

