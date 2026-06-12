---
title: "ubuntu  nautilus preferences don't stick"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by cmcanulty on 2013-06-27
Lately some machines ignore the preferences I have set up in nautilus. Particularly the delete option and the detailed list view. I run 10 Ubuntu 12.04 Classic laptops at our library and now 2 do this. I am starting to migrate to thunar which is faster and less buggy but would prefer a fix. I can set the preferences as I wish, close nautilus and reopen it and the boxes are not the way I checked them. Very irritating.

---

### Post by Cheesemill on 2013-06-27
Try setting them using dconf-editor instead, it may make a difference. You can find them at org.gnome.nautilus.

Also it may be worth checking permissions on your home folder, if you have ever used 'sudo nautilus' then you may have changed the ownership of the nautilus config files to root meaning you don't have permission to edit them anymore. A quick way of changing them back would be...
```
sudo chown -R user.user /home/user
```
replacing all 3 occurrences of user with your actual username.

---

### Post by cmcanulty on 2013-06-27
will try I just got home from work but I did already try from dconf editor -they were set correctly there it just isn't happening. I work sat and will post result of your script, thanks

---

