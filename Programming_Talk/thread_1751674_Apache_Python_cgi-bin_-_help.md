---
title: "Apache Python cgi-bin - help"
date: 2011-05-06
forum: Programming Talk
---

### Post by Scattered on 2011-05-06
[COLOR=#000000][FONT=Verdana]I cannot seem to get my python files to execute under [COLOR=#FF0000]**Apache**[/COLOR]. 

Here is what I have so far:

[COLOR=#FF0000]**Apache**[/COLOR] works. The default page under /var/www renders in a browser.

Python is loaded and works under /etc/bin/python.

I have execute permissions set on /var/www/cgi-bin and my test.py file.
[/FONT][/COLOR] 
My /etc/apache2/sites-available/default file is this:
<VirtualHost *:80>
ServerAdmin webmaster@localhost
 
DocumentRoot /var/www
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>
 
ScriptAlias /cgi-bin/ /var/www/cgi-bin/
<Directory "/var/www/cgi-bin">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
AddHandler cgi-script .py
AddHandler default-handler .html .htm
</Directory>
 
ErrorLog ${APACHE_LOG_DIR}/error.log
 
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn
 
CustomLog ${APACHE_LOG_DIR}/access.log combined
 
Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
 
</VirtualHost>
 
When I execute this URL: "http://localhost/cgi-bin/test.py" I get this web error: 
Internal Server Error
 
The server encountered an internal error or misconfiguration and was unable to complete your request.
 
Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 
More information about this error may be available in the server error log.
 
The /var/log/apache2/error.log has this error:
[Fri May 06 14:48:08 2011] [error] (2)No such file or directory: exec of '/var/www/cgi-bin/test.py' failed
[Fri May 06 14:48:08 2011] [error] [client 127.0.0.1] Premature end of script headers: test.py
 
The contents of /var/www/cgi-bin/test.py:
#!/usr/bin/python
 
print "Content-type:text/html\r\n\r\n"
print '<html>'
print '<head>'
print '<title>Hello Word - First CGI Program</title>'
print '</head>'
print '<body>'
print '<h2>Hello Word! This is my first CGI program</h2>'
print '</body>'
print '</html>'

---

### Post by dwhitney67 on 2011-05-07
What are the file permissions on test.py?  Make sure it is 755.  For example:
```

sudo chmod 755 test.py

```

---

### Post by Scattered on 2011-05-07
I verified the permissions...

-rwxr-xr-x 1 root root 274 2011-05-06 09:10 test.py

---

### Post by gmargo on 2011-05-07
Your problem is almost certainly due to the file format of the **test.py** file.  

It is in DOS format (CR-LF line endings).  But it must be in UNIX format (LF line endings) to work properly.

Your example worked fine for me ... until I changed the test.py format to DOS.  Then I got the same error message you did.

File size seems to confirm this too:
```

-rwxr-xr-x 1 root root 274 2011-05-07 07:09 test-dos.py
-rwxr-xr-x 1 root root 263 2011-05-07 07:16 test-unix.py

```

---

### Post by Scattered on 2011-05-07
That was it! 

I had created the file with gedit which must use dos control characters instead of unix. I tested your assumption by recreating the test.py file with vi and it worked fine.

Thanks for the quick, accurate response.

---

### Post by gmargo on 2011-05-07
It's not really a **gedit** problem.  Normally, **gedit** uses UNIX line endings.  But this sort of thing even happens with **vim**, especially if cutting & pasting from some web resource.  The editors try to be good citizens and leave the text in the format it thinks you want.

If you use **gedit**'s "File->Save-As" dialog, you can specify the line-ending type.

---

### Post by Scattered on 2011-05-08
Again, your suggestion worked! I opened and saved test.py using gedit but switched the "Line Ending" setting from "Windows" to "Unix/Linux". Thanks.

---

