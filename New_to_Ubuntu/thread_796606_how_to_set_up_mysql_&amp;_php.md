---
title: "how to set up mysql &amp; php?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by ubroshan on 2008-05-16
Hi evrybody,

Im a new user for Ubuntu.I wanted to try Php in ubuntu environment.But i have no idea of how to set up such.I checked that by typing localhost  in the browser address bar to verify for apache and it works.but now im in a trouble       to install mysql and php. Can anybody guide me how to configure it? I will be grateful for that.

Thanks in advance.

Roshan.

---

### Post by kellemes on 2008-05-16
> **ubroshan said:**
> Hi evrybody,

Im a new user for Ubuntu.I wanted to try Php in ubuntu environment.But i have no idea of how to set up such.I checked that by typing localhost  in the browser address bar to verify for apache and it works.but now im in a trouble       to install mysql and php. Can anybody guide me how to configure it? I will be grateful for that.

Thanks in advance.

Roshan.

[Installing a LAMP-server]("https://help.ubuntu.com/community/ApacheMySQLPHP").

And another link.. section 9 and 10 is what you're interested in..
[https://help.ubuntu.com/8.04/serverguide/C/index.html]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

---

### Post by housam on 2008-05-16
Look at [[COLOR="Red"]_this guide_[/COLOR]]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html#7") section 8

---

### Post by cb951303 on 2008-05-16
```
sudo tasksel
```
select LAMP Server

---

### Post by ubroshan on 2008-05-16
I figured out the location of apache server.but the wiered thing is i cannot create or  copy and past any files in /etc/apache2 folder and its sub folders.also i noticed a padlock icon is displayd on the 'File system' folder and 2 more other partioned of my hard disk.I remember when i install ubuntu it asked me about monting/unmountig partitions.but at that time i wasnt sure what to do so i just selected some drive to unmount.

So then how do i enable these folders to be able to edit?

---

### Post by cb951303 on 2008-05-16
in linux world everything is build around users, groups and permissions.
your user doesn't have write access to /etc and its subfolders.
to upload your pages to web server, copy them to "/var/www".but in order to do that you must have root privileges. the command "sudo" will do it... or you can setup a local folder in your home directory like "/home/my_user_name/public_html" and make apache aware of it so that you don't bother with permissions and just drag and drop your files...

PS: I know I'm not clear to you but there isn't enough room here to explain all that. I gave you the outline it's up to you to search and learn the rest :lolflag:

---

### Post by ubroshan on 2008-05-16
Yep!

I got it! it works fine now. Thanks for evry one for your time and contributions.

Roshan.

---

