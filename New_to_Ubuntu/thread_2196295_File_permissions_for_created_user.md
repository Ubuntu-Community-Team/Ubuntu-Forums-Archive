---
title: "File permissions for created user?"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by ames909 on 2013-12-28
Hello! First post here and an absolute newbie re: Linux/Ubuntu, so please go easy on me.

I recently got myself an unmanaged VPS and have been trying to set up a FTP using PuTTY. I managed to create a user with a password that has access to the /var/www folder, and I am able to log into my VPS using Filezilla and access the folder. However, every time I attempt to upload anything I am met with a "550 permission denied" error. Am I doing something wrong? I've tried different chmod combinations to try and alter the permissions for /var/www to no success. Is it because I need to set file permissions for the specific user and not the folder?

(on that note, I think one article suggested altering a .conf file and while I'm able to get it to open in PuTTY, I don't even know what commands to use in order to save/exit it once I'm done adding a line of code...)

Please give me the specific codes to use if possible, I honestly am completely new to this!

Thank you in advance for reading. :)

---

### Post by conversationjames on 2014-01-02
Maybe?:
sudo chown -R "servername" /var/www

[UNIX commands]("http://people.rit.edu/msa6687/409/projects/IndividualMidterm/chown.html")

---

