---
title: "phpbb3 problem"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-12
I installed phpbb3 via synaptic package manager. It created a database with all the tables in mysql. I moved the folder /usr/share/phpbb3 to /var/www/ but when I try to access the forums by going too [http://localhost/phpbb3](http://localhost/phpbb3) it brings me to the directory of phpbb3. Like if i had no index.html file would bring up index / with options to download whats in there. Do any of u have any suggestions as too what I should do to get my forum to show up. When i installed phpbb3 I didn't have php5 working yet. I relised afterwards I had to install since lamp missed it when installing. Now my [http://localhost/test.php](http://localhost/test.php) works so php5 is now working. But how to get my forums to show up now? Is it just something stupid i have to do or do i need to reinstall phpbb3 now that php5 is working. Any ideas would be great. I have to go  to work right now. I will be back in 6 hours to try any ideas u guys have for me. Thanks in advance for any help i receive.

---

### Post by Coreigh on 2008-11-12
When you moved the stuff to /var/www you forgot to tell Apache. You will need to edit your virtualhosts in /etc/apache2/sites-available/default (default is the file name) One of the lines there probably points to the old location, you will need to edit it to reflect the new location.
```
 sudo gedit /etc/apache2/sites-available/default
```

If you find there was no reference to the old location here you will have to determine where Apache was told to find the old location and change it.

Be careful editing that file, it is a good idea to save a copy as COPYOFdefault so you have a "fallback" position in case of trouble.

---

### Post by shanep-server on 2008-11-12
ok cool i'll give that a try when i get back. Thanks I'll let u know what happens.

---

### Post by shanep-server on 2008-11-13
ok I couldn't figure out how to do that. I didn't see anything in that file directing a path too phpbb3. 

I wonder am I supposed to keep my phpbb3 file in /usr/share/phpbb3 then create a symlink too var/www/ so that phpbb3 will show up in var/www/ as var/www/phpbb3? Right now I think I can get too the board going too var/www/phpbb3/www/index.php but thats not exactly what I had in mind.

Any suggestions guys?

I moved usr/share/phpbb3 to var/www/ using

sudo -a /usr/share/phpbb3 /var/www/

---

### Post by mk6032 on 2009-06-25
sudo apt-get install phpbb3

run through the setup...

cd /etc/apache2/sites-available/
nano default

add this line at the end:

Alias /forum /usr/share/phpbb3/www/

restart apache2

sudo /etc/init.d/apache2 restart

now point your browser to [http://www.yourdomain.com/forum](http://www.yourdomain.com/forum)


HTH,
Matt

---

