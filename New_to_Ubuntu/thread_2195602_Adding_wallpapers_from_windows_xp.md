---
title: "Adding wallpapers from windows xp"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by salezd on 2013-12-25
Hi, I have some wallpapers from windows xp on my lubuntu 12.04. and when I want them to put on the desktop it works fine, but when I do a reboot wallpaper disappears.How to solved that?

---

### Post by egeezer on 2013-12-25
Not sure, but what is the file extension on the Windows images?  Wallpaper should be .jpeg or .gif, and Windows sometimes gets picky and uses some kind of bitmap thing.

---

### Post by kostkon on 2013-12-25
You could copy the image you want to use as your wallpaper to your Ubuntu partition and specifically to your Pictures folder.

---

### Post by angry_johnnie on 2013-12-25
If these wallpapers are stored in your windows partition, and you did not specifically ask the installer to use or automatically mount this partition, then linux won't find them after a reboot.

You'd have two choices:

You can either edit /etc/fstab to automatically mount your windows partition and allow linux to always be able to read from it.

Or, you could, as it's been suggested before, copy the desired images to your linux partition.

---

### Post by salezd on 2013-12-27
I forgot to respond,I am sorry.Thank you very much for your help but in the meantime I deleted the windows partition so it doesn't matter anymore.Thank's anyway.

---

