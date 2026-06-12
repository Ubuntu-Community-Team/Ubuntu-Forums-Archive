---
title: "Ubuntu 6.06 best FTP gui Server"
date: 2006-10-08
forum: Other OS Talk
---

### Post by SteffJay on 2006-10-08
I'm trying to find a good FTP server with a good graphical user interface, that is easy to administer. Anyone have any ideas ? :-k

---

### Post by bastiegast on 2006-10-08
I use vsftpd(its in the repo's: sudo apt-get install vsftpd) there are many howtos on it on the web. Actually it has no gui but the config file is really easy to edit. The whole thing is easy to setup and secure. You might wanna give it a try.

EDIT: Theres also filezilla considered one of the best(for windows and linux)  with GUI and stuff, but i found it more confusing than the simple config file of vsftpd

---

### Post by SteffJay on 2006-10-08
Hello **bastiegast**. Thanks for the quick reply ;)  I have looked for Filezilla but cannot find it anywhere in the repo's :(  I have used that before and got on with it ok. If you know where to find it, please let me know. Thanks  ;)

---

### Post by bastiegast on 2006-10-08
Hi, filezilla is on [http://filezilla.sourceforge.net/]("http://filezilla.sourceforge.net/") but I noitced it only has a beta version for linux, the current release is windows only :(  I dont know any other graphical ftp servers, but still, vsftpd is in the repos and fairly easy to configure. By the way GNOME/KDE may even have some sort of built in ftp server but i dont know about that, at least nautilus can function as a ftp client.

---

### Post by SteffJay on 2006-10-08
Hello **bastiegast**. I have just uninstalled the vsftpd as it totaly blew my mind....  I wanted to set it up to only allow certain people with passwords and only to their own folder with read/write permission's but i could not get my head around all of the commands. ](*,)  Never mind..  i'll struggle on....... Thanks anyway...  ;)

---

### Post by morningboat on 2006-10-23
Hi, you can have a look at this cross platform GUI ftp server: [http://crossftpserver.sourceforge.net/](http://crossftpserver.sourceforge.net/)

---

### Post by SteffJay on 2006-10-23
Thanks **morningboat** i'll give it a look.....  ;)

---

### Post by kopilo on 2006-10-25
I've found Firezilla to be fairly good. However I've also found [Fireftp]("http://fireftp.mozdev.org/") (plugin for firefox) to be very handy, easy to use and it is only 100k to download/install.

However I don't think it can do many security functions.

Edit: You might want to [ftpCube]("http://ftpcube.sourceforge.net/"), imo it looks fairly good.

---

### Post by SteffJay on 2006-10-25
Thanks for that **kopilo**. I'll give it a look, although, i looked for Filezilla but it was not available for Linux the last time i looked  :(

---

### Post by at0mic on 2006-10-26
glftpd is king of this hill.

[http://ubuntuforums.org/archive/index.php/t-87505.html](http://ubuntuforums.org/archive/index.php/t-87505.html)

---

### Post by Pipps on 2008-07-05
FireFTP definitely seems to be the easiest and the best. I had it set up in 2 minutes and now it's running really well. Thanks for recommending it! :)

---

