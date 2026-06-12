---
title: "Mapping music folder across drives"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by tomster2300 on 2011-10-29
Hey guys.  I have my music on a separate drive and I want to point Ubuntu's default music folder to the music folder on the second drive.  Can I do that without making a folder shortcut?  I basically want to be able to open my default ubuntu music folder and have all my music.  

I'm also on 11.10 with Unity - if I can link the two, is there a way to get the music to populate the music tab?

Thanks!

---

### Post by CatKiller on 2011-10-29
Mounting your music drive at ~/Music should be sufficient. There are plenty of tutorials around on how to use fstab, or you could post more details about your setup here and someone can probably help you out.

---

### Post by nothingspecial on 2011-10-29
Yep this is indeed posible

What filesystem is the external drive?

---

### Post by mcduck on 2011-10-29
You can either mount the secondary drive to the desired location, or if it's using a Linux filesystem (like Ext4) a symbolic link will also do the trick.

(I use a symbolic link to add my removable hard drive to my laptop's music directory. That works fine, I can play the songs from the removable drive when it's connected, otherwise the player simply skips them. Of course updating the library without the drive connected would cause some problems...)

---

### Post by tomster2300 on 2011-10-29
Thanks for all the responses guys.  

The other hdd is ntfs (it's a Windows 7 install) and it shows up in  nautilus.  How would I map it?

---

### Post by tomster2300 on 2011-10-29
Hey guys, I worked with a friend of mine and we figured it out (based on your suggestions above).  Here's what we did in case this helps anyone else:

Apparently Nautilus displays all connected drives whether they're actually mounted or not. I mounted the drive, and specifically the music folder via terminal:

sudo mount /dev/sdb1 ~/Music

and then added this to the bottom of fstab: 

#Mount Windows ntfs drive for music
/dev/sdb1 ~/Music ntfs

This is now working like a charm, although I'm still not able to find my music in unity's dashboard search.  Is there something I need to do to rebuild its search index, or does it have trouble finding files on a mapped drive?  

Thanks again to everyone!

---

