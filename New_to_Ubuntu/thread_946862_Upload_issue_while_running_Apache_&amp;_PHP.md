---
title: "Upload issue while running Apache &amp; PHP"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2008-10-13
Hi all --
I installed the LAMP stack in Ubuntu so I could use my comp as a dev. server.  I'm writing an app in PHP and it uses file uploading.  Apache uses the /tmp directory to store uploads, and then I call 

move_uploaded_file($_FILES[$name]['tmp_name'], $location

However, it seems that the permissions are off.  I get these errors:
Warning: move_uploaded_file(/var/www/newsite/images/photos/6.jpg) [function.move-uploaded-file]: failed to open stream: Permission denied in /var/www/newsite/includes/classes/upload.php on line 117

Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/phpoR3NaM' to '/var/www/newsite/images/photos/6.jpg' in /var/www/newsite/includes/classes/upload.php on line 117

Any ideas on what I need to do to correct the permissions ??  Thanks!
Chuck

---

