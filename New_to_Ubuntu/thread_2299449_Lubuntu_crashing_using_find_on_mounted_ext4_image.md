---
title: "Lubuntu crashing using find on mounted ext4 image"
date: 2015-10-18
forum: New to Ubuntu
---

### Post by buntunoob2 on 2015-10-18
Hi everybody,

I created an img of an ext4 partition using dd. I mount this to /Backup using 
sudo mount my.img /Backup

If I list the contents using find, all file names are printed - but if I use any parameter with find like
find -size +1M
find -type f

The system crashes - the screen becomes black with a cursor which cannot be moved around. 

Pretty weird: When I open a text file, save the text file and then use the find command to crash the system, the file is empty after a restart....

---

