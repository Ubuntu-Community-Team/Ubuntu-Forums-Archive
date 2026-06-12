---
title: "mount --bind"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by balkrishna on 2008-04-22
Problems with mount --bind:
while sharing files over ftp we copy files to /home/ftp
however an another way is to bind the folder i want to share with /home/ftp. This erases the contents in the bound folder.
I sthis a bug with ftp or am i using it wrongly.

---

### Post by RealPSL on 2008-04-23
Just to make sure I I am clear on the scenario. If I have the files I want to share via ftp in /home/wcoyote/acme I would mount them as follows

```
sudo mount --bind /home/wcoyote/acme /home/ftp
```

Are you saying that the original files in /home/wcoyote/acme disappear because that should not be the case? The original files in /home/ftp should be replaced by the files in /home/wcoyote/acme for the duration of the mount. That is until you run  

```
sudo umount /home/ftp
```

Which removes the mount over the existing files but the original files will be there.

---

