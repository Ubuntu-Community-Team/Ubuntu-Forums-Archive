---
title: "PHP and error logging"
date: 2012-03-18
forum: Programming Talk
---

### Post by drhiii on 2012-03-18
I just had a partner ask me to find out how to do the following.  We are moving from BSD to Ubuntu (yay).

Question is, he was able to have PHP errors write to a log file *in* a directory that he was testing/executing scripts.  

Anyone know how to tweak this?  So error logs can be written into the working directory one is testing in?

Make sense?

Tx for any guidance on this.

---

### Post by drhiii on 2012-03-19
Here is a blurb from a forum that articulates this better:   


"... but I can't seem to find out how to let PHP create an error_log file in the same directory as the script that throws the errors.

I would like this to happen without me having to add a line of code to each .php file. In Cpanel this works out of the box somehow"


This says it better than I did.  One thing I did find is that it appears it is an Apache directive, not PHP.  Ideas anyone?

---

### Post by dharmavir on 2012-03-24
If you're using standard lamp-server setup or have installed php/apache from ubuntu official package repo you should be able to find your php errors in apache log files under following path:

/var/log/apache2/error.log

above file includes both apache and php script errors.

I hope this is what you wanted. 

[http://blogs.digitss.com](http://blogs.digitss.com)

---

### Post by SeijiSensei on 2012-03-24
If you run "ls -l /var/log" you'll see that the parent directory for Apache's files, /var/log/apache2, is only visible to the root user and members of the adm group.  In order to make this file readable by an ordinary user, you have to subvert these permissions as follow:

```

sudo chmod 755 /var/log/apache2
sudo chmod 644 /var/log/apache2/error.log

```

Then you can create a symlink in the user's home directory to the error log like this:

```

cd /home/username
sudo ln -s /var/log/apache2/error.log 

```

Now you can view the log as /home/username/error.log.

However a better solution is to modify /etc/php5/apache2/php.ini and change the "[error_log]("http://us.php.net/manual/en/errorfunc.configuration.php#ini.error-log")" directive to point to a file in the user's home directory.  You'll have different permission problems here, though, since the webserver runs as the "www-data" user which, by default, cannot write into another user's home directory.  Give this a try:

```

cd /home
sudo chmod 0770 username
sudo chgrp www-data username

```

Then in php.ini set

```
error_log = /home/username/phperrors.log
```

Restart Apache with "sudo service apache2 restart" and see what happens.

---

