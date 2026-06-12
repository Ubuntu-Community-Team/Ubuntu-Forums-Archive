---
title: "restoring previously installed ubuntu using LIVE CD"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by vamsibethapudy on 2008-08-15
how do i restore a previously installed ubuntu OS using a LIVE CD of the same version???
I think somehow I have made my OS unbootable.
It says its a bad name when I launch a kernel.
My windows XP works.pleaseeeee

---

### Post by OldGrey on 2008-08-15
Just re-install it over the top of the old installation. Its should be exactly the same process as your first attempt.

---

### Post by croniksoft on 2008-08-15
another way you can do this is by Backing up your Home Directory and re-install Ubuntu,after you have Re-install Ubuntu you can copy Back your home directory, 

because in reality thats all you need,all of your setting are store in your Home directory


NOTE:There is also a special way to put the home directory in a different partition then the &#8220;/&#8221; partition ,i can help you out doing this if you want.

---

### Post by vamsibethapudy on 2008-08-15
actually , my home folder is in a different partition.
so wont I be erasing any settings or programs if I reinstall the '/' partition??
the '/' partition almost took 8 GB. what will I be erasing then??

---

### Post by tahina on 2008-08-15
You'll be erasing everything, except for what is in /home and subdirectories of /home

If you have home dir on different partition and don't format it when you re-install ubuntu and use the same username, you will still have all you've put in your home dir and also your old settings, bookmarks, mail and so on, because they are all stored in hidden directories/files in your home directory.

You need to tell the installer to use the same partition as before for the mount point /home and make sure you don't format it.

You will have to reinstall all applications that you had added after installing the first time (but you will still have all settings you've made for those).

Backing up the home would be sensible anyway, though.

---

