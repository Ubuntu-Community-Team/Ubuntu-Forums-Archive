---
title: "Quick Apache Question"
date: 2006-08-04
forum: Programming Talk
---

### Post by mikesena on 2006-08-04
This will take someone about 2 secs to answer (i hope)...

Where is my public_html (so to speak) folder?!  I know i know have a lamp because localhost/phpmyadmin works (;)).  Now where are those files? :P

Someone pleasE?

---

### Post by scxtt on 2006-08-04
you'll have to make ~/public_html if you haven't already - even installing apache doesn't do that by default - and you'll have to allow the use of "users public_html folders" in your apache2.conf ...

---

### Post by mikesena on 2006-08-04
Where is that file

---

### Post by scxtt on 2006-08-04
/etc/apache2/apache2.conf

**sudo slocate -u** and **slocate apache2.conf** are your friends :)

---

### Post by mikesena on 2006-08-04
I can't edit it, it says its readonly.  Is there a way to stop apache while i change this setting, then restart it?

---

### Post by scxtt on 2006-08-04
you can edit it while apache is running, then you'll need to restart apache ...

1. sudo gedit /etc/apache2/apache2.conf
-- make your changes, look for this:
```
# UserDir is now a module
UserDir public_html
UserDir disabled root

<Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options Indexes SymLinksIfOwnerMatch IncludesNoExec ExecCGI
</Directory>
```2. sudo /etc/init.d/apache2 restart
-- might just be apache, can't remember - type apa and hit tab ...

---

### Post by mikesena on 2006-08-04
# UserDir is now a module
UserDir public_html
UserDir disabled root

<Directory /home/meo/public_html>
	AllowOverride FileInfo AuthConfig Limit
	Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>


This is what I now have.  I tried restarting, but when I type in 'localhost' in firefox, it still comes up with what it did b4.  I created a folder in public_html, and it didn't find that either

---

### Post by scxtt on 2006-08-04
what exactly are you typing into your browser?

i'd recommend using your local IP address instead of localhost ... **[http://192.168.1.100/~mikesenna](http://192.168.1.100/~mikesenna)** will give you the index.html file located at /home/mikesena/public_html/index.html ...

---

### Post by ifokkema on 2006-08-04
> **scxtt said:**
> 1. sudo gedit /etc/apache2/apache2.conf
Apache 2 works differently, you just have to run:
```
sudo a2enmod userdir
```
Much easier than messing with the config file...!
Oh yeah, don't forget to restart apache after that:)
```
sudo /etc/init.d/apache2 restart
```

---

### Post by mikesena on 2006-08-04
typuing my ip and username worked exactly thankyouvm

---

### Post by scxtt on 2006-08-04
[quote=ifokkema]Apache 2 works differently, you just have to run:```
sudo a2enmod userdir
```[/quote]you do it your way, i do it mine ... for me, it's "easier" to do it the way i mentioned instead of using some apache module enabler ...

---

### Post by ifokkema on 2006-08-04
> **scxtt said:**
> you do it your way, i do it mine ... for me, it's "easier" to do it the way i mentioned instead of using some apache module enabler ...
Hey, just as good, just figured it might be easier for someone who hasn't worked with Apache before. I thought it was a great improvement to 1.3.X anyway... Virtual hosting now works the same way as well.

---

