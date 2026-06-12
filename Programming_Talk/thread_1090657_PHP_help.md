---
title: "PHP help"
date: 2009-03-08
forum: Programming Talk
---

### Post by bc040401056 on 2009-03-08
Hi friends,

Im new to ubuntu and my computer is a client of lan.

I have successfully installed php apache and mysql but when i write a php program in notepad and save it in .php format and when i open that file it shows no out put only the notepad opens can u please tell me which thing is im missing to configure or what i have to do please

---

### Post by namegame on 2009-03-08
You need to make the file executable.

Then you can run it from the command line with "php filename.php"

I've also send a request to the mods to get this moved to programming talk.

---

### Post by bapoumba on 2009-03-08
Moved to PT, thanks namegame :)

---

### Post by lapubell on 2009-03-08
php runs through the apache webserver, so double clicking on the file won't exectue it unless you have the command line php package installed and the file is executable.  otherwise, you can use firefox to view your localhost webserver.  just point your browser to [http://localhost](http://localhost) or [http://YOUR.IP.ADDRESS](http://YOUR.IP.ADDRESS) and run your file through the browser.

---

### Post by drubin on 2009-03-08
> **namegame said:**
> You need to make the file executable.

Then you can run it from the command line with "php filename.php"

I've also send a request to the mods to get this moved to programming talk.

If you run php file.php  file doesn't (And shouldn't have execute) permissions. it isn't the file.php that is executed but rather the php binary file that reads the file.php. Similar with  .sh files even if they aren't executable you can still run sh file.sh and it will execute file.sh.

This is also a duplicate of [http://ubuntuforums.org/showthread.php?t=1090663](http://ubuntuforums.org/showthread.php?t=1090663)

---

