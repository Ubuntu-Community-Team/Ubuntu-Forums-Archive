---
title: "PHP exec to run soffice"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by stwschool on 2008-10-19
Just wondering if you guys could help a newbie out here. I'm a linux noob but php veteran so I'm wondering why this doesn't work.


<?
  exec("soffice") or die ('It went wrong');
?>

Just outputs 'It went wrong'. I've tried using system, shell_exec, using the headless option for soffice, using the full absolute path (though the command as given works ok in the console), all sorts, still the same problem. Any ideas?

---

### Post by -grubby on 2008-10-19
Remove the "or die" and see what went wrong?

---

### Post by stwschool on 2008-10-19
The problem there is that without or die it just sits there and does nothing. At least with or die it's telling me that something cocked up. Btw extra info.. I'm on Hardy, standard ubuntu, and the usual download from synaptic to get the packages in. PHP in general is working well, as is apache and mysql.

---

### Post by stwschool on 2008-10-19
The problem there is that without or die it just sits there and does nothing. At least with or die it's telling me that something cocked up. Btw extra info.. I'm on Hardy, standard ubuntu, and the usual download from synaptic to get the packages in. PHP in general is working well, as is apache and mysql. Also these exec commands work ok with more mundane tasks like ls or pwd.

---

### Post by run1206 on 2008-10-19
i'm not too familiiar with PHP, but you might wanna message LaRoza about it in the programming forums 
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by stwschool on 2008-10-19
Ok well I'll try one last workaround before I bother someone. Basically what I'm trying to achieve is to get soffice to print a document, so it's soffice -headless -p <file_location> in the command line. Easy. However, I'm wondering if copying the files to be printed to a particular directory and doing a cron job to soffice -headless -p /home/me/printthis/*.* every 2 minutes might be the solution?

---

### Post by stwschool on 2008-10-19
Just a quickie, in case anyone else is having the same problem. My solution was to use php to copy the files to be printed into a folder. I then wrote a small script saying 
/opt/openoffice3.0/program/soffice -p /var/www/tmpstore/*.*
rm /var/www/tmpstore/*.*

I set permissions to make it executable and installed scheduled tasks gui thingy and used that to execute once a minute. When I tried editing crontab I made a hash of it so decided to leave that. Job done.

---

