---
title: "could not save file - do not have permission"
date: 2017-02-24
forum: New to Ubuntu
---

### Post by autocoder2 on 2017-02-24
would like to save a text file to /var/www/html.  But get message "do not have permission to save file".   Can I run gedit as administrator? How to run the file manager as root or admin so that I can grant permissions?

to clarify. I know how to change the owner on the command line. How to run the ubuntu file manager window as administrator?

thanks,

---

### Post by vanillasnake21 on 2017-02-24
you can run gedit as admin by doing "sudo gedit /var/www/html/file" if you still get errors, I usually just create the file in my local location and then move it over to the destimation using "sudo mv ~/localfile /var/www/html/file

---

### Post by Impavidus on 2017-02-25
Better make that```
sudo -H gedit /path/to/file
```The -H option sets the correct home directory. Else some files in your home directory may get owned by root, preventing login. For the file manager, use```
sudo -H nautilus
```I would make the file in my home directory, then copy it to /var/www/html/.

---

