---
title: "Using PHP and phpmyadmin"
date: 2014-08-27
forum: Programming Talk
---

### Post by AleksaK on 2014-08-27
On Windows it was so simple. I just had to install XAMPP or WAMP or whatever, run apache, put my index.php in the htdocs folder and everything worked smooth. Here it's so complicated. I installed whole bunch of stuff using sudo apt-get, including mysql, php, phpmyadmin all that stuff. Then I went into /var/www/html and found an index.php file there which claims to be readonly and at first I could do nothing. Then I deleted it with sudo rm. The I created a new one with sudo nano index.php but the only way I can edit it is if I open it via Terminal, and that's not what I want. I want to be able to open it with normal text editor like everything else. So I open it with text editor, write some stuff then click save and get a message saying file can't be saved 'cause it's readonly.
PS: The file actually works in localhost/index.php but I want to be able to edit it normally.

 I got different problem with phpmyadmin. I installed (followed some YT tutorial) and made a shortcut to it in www folder, but localhost/phpmyadmin gets me to 'not found' page. So...any ideas?

Thanks

---

### Post by SeijiSensei on 2014-08-27
I usually place web sites under user directories to avoid these kinds of permission issues.  Create a directory called /home/username/web, then change the directives for DocumentRoot and its corresponding <Directory> stanza in /etc/apache2/sites-available/000-default.conf to point to the directory you created.  Put the files in there and restart Apache. 

And, remember, Linux is not Windows.  Permissions are very different in the *nix world and usually more restrictive than in Windows.

I can't help with phpmyadmin.  I usually just run command-line SQL clients or use something like LibreOffice Base or Microsoft Access to communicate with databases.

---

### Post by AleksaK on 2014-08-27
Thanks for replying.
But... 000-default.conf is read only as well.. bummer

---

### Post by SeijiSensei on 2014-08-27
Use sudo:

```
sudo nano /etc/apache2/sites-available/000-default.conf
```

---

### Post by AleksaK on 2014-08-27
Worked, thanks!

---

