---
title: "tar.gz?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-06-20
Hi ya'll, okay, I download a new look from Gnome-Look, and it is sitting here in a tar.gz box? What do i do with it?

---

### Post by yragrelluf on 2008-06-20
right click on it, and select extract here. then you need to move the extracted file to /usr/share/themes. that should do it, let me know if you need more help, because to move the file, you might need root permissions, and need to do it from the terminal. (sudo mv "extracted file path" /usr/share/themes) once it is moved, you should be able to right click the desktop, select change desktop background, select the theme tab, and select your new theme.Then you can delete the tar.gz. Which theme did you pick? I reccomend earthy and lux.
PS, you should remove the darklooks theme, because there is something wrong with it and it messes up your desktop every time you reboot.

---

### Post by Andrew79 on 2008-06-20
uhh...actually it was a darklooks, elegence. it looked really cool on the screenshot. i got one of the wallpapers to work, AllDayLong, they look pretty cool. Is there a way to make my wallpapers automaticaly change every so often? I like to change my wallpapers, cause th ecomputer will sit, and people dig seeing my backrounds.

---

### Post by tjwoosta on 2008-06-20
yea the program is called Wallpapoz (should be in synaptic i think)

---

### Post by kk0sse54 on 2008-06-20
There is a screenlet that will change your wallpaper automatically ever so often just go into Synaptic and install Screenlets. In order to get that particular screenlet called Wallpaper Changer though I think you need to download it from [http://screenlets.org/index.php/Wallpaper_Changer_Screenlet](http://screenlets.org/index.php/Wallpaper_Changer_Screenlet) and install it because it's not among the default screenlets.

---

### Post by yragrelluf on 2008-06-20
LUX is very similar to darklooks, just without the bugs.

---

### Post by wootah on 2008-06-20
.tar = Tape ARchive. This is a file format that basically combines a whole bunch of files in to one file. It's basically like storing one file right after the next.

.gz = gzip. This is a compression type.

Thus,

.tar.gz (or .tgz) = a gzip tar file, aka, a tarball :)

To Create compressed tar:
tar -cvvfz new_tar.tar ./the_tar_folder
Options: create verbose verbose filename compress

To Extract compressed tar:
tar -xvvfz tarfile.tar.gz

Good luck! :)

---

