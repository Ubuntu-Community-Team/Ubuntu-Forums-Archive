---
title: "symbolic link?"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by wlraider70 on 2013-01-30
I have a website in apache2 that I want to back to dropbox.

I would like to syslink /var/www/chuchinfo/*  to ~/Dropbox/backup
Can I make linked files with the same name and data in destination as the target.

The idea is that if the server went up in smoke I could download to a new webserver and be running again.

---

### Post by kanikilu on 2013-01-30
Apparently some people have had problems doing this:

[http://stackoverflow.com/questions/2953517/set-apache-documentroot-to-symlink-for-easy-deployment](http://stackoverflow.com/questions/2953517/set-apache-documentroot-to-symlink-for-easy-deployment)

[http://www.mikebrittain.com/blog/2009/05/12/case-against-using-symlinks-for-code-promotion/](http://www.mikebrittain.com/blog/2009/05/12/case-against-using-symlinks-for-code-promotion/)

I've never tried it, so this is just me thinking out loud here, but I wonder if the easier solution would be to simply set the DocumentRoot in the apache config to point to the Dropbox folder?

---

### Post by zeljkojagust on 2013-01-30
A solution with symlink could easily backfire on you; for instance you urgently need space on your Dropbox account, you are not looking and you delete complete content of your website. Much smarter solution would be to place rsync job in cron that would run every let's say 10 minutes.

So open your crontab on server:
crontab -e

Go to the end of file and enter something like this:
*/10 * * * * rsync -a /var/www/chuchinfo/. /home/yourusername/Dropbox/backup/.

rsync with -a option will sync all files from /var/www/chuchinfo/ to /home/yourusername/Dropbox/backup/ with right ownership and permissions.

---

### Post by wlraider70 on 2013-02-04
> **zeljkojagust said:**
> 

rsync with -a option will sync all files 


should that be -r ?

Solution is working great, I'm adding a "~/bin/dropbox.py start" line just make sure.


How the permissions work with crontab?

---

### Post by Cheesemill on 2013-02-04
> **wlraider70 said:**
> should that be -r ?
-a implies -r.

From 'man rsync'...
> -a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)

---

### Post by wlraider70 on 2013-02-04
thanks.

I ran the command manually and the trailing . seemed to cause an issue. I went with * so this is my final line


*/10 * * * * -r /var/www/churchinfo/* /home/server/Dropbox/backup


It appears that cron runs as root and that the sync is in both directions. ie from backup to the live folder. 


Thanks all

---

