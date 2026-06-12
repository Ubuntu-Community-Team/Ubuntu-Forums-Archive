---
title: "Apache permissions"
date: 2012-10-04
forum: Programming Talk
---

### Post by angus1964 on 2012-10-04
I have just set up Apache and got it working fine. I tried to add another folder to /var/www. but when i tried to open the file in chrome with [http://localhost/darts/index.html](http://localhost/darts/index.html). I got the message that Permission was denied as i dont have access to that file. Is there a way to allow permission or would i have to do what is in this wiki page.[http://help.ubuntu.com/community/ApacheMySQLPHP]("http://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by dwhitney67 on 2012-10-04
What are the permissions set to on the folder and file??

On my system, I set ownership to be root:root.  Permissions on the directory is 755, and the file(s) would be 644.

---

### Post by Lars Noodén on 2012-10-04
Are you talking about not having write permissions to the web server's document root?  That's easy to fix.

```

sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add angus1964 webmasters

```

Then log out and back in again for the group membership changes to take effect.

---

### Post by angus1964 on 2012-10-04
Thanks for quick reply, changing file permission to 644 made it work.

Cheers

---

