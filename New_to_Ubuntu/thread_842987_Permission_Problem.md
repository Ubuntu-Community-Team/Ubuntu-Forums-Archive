---
title: "Permission Problem"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Eleventy3 on 2008-06-27
I've added 2 extra HDDs to my computer, one for music files and one for movies. I've updated the fstab so that they mount under my home folder as below

/dev/sda1	/home/steven/Music  ext3 defaults 0 0
/dev/sdc1	/home/steven/Videos  ext3 defaults 0 0

Its mounted ok but I can't write to them,I try to move files in or create a new folder and it says permission denied.

I have checked and steven is the owner of the folder so I don't know why I can't.

Any Ideas?

---

### Post by wak_wak on 2008-06-27
Try sudo chmod 777 /dir/filename

---

### Post by aktiwers on 2008-06-27
Try this:
```
sudo chown -R steven:steven /home/steven/Music
```
and
```
sudo chown -R steven:steven /home/steven/Videos
```

And you should be good to go :)

---

