---
title: "Configuring Python for Apache"
date: 2011-08-20
forum: Programming Talk
---

### Post by ifben on 2011-08-20
Hello,

I'm trying to get my server to recognize python scripts instead of just spitting them out as text files. My OS is Ubuntu 10.04 LTS.

[This thread]("http://ubuntuforums.org/showthread.php?t=1751674") was not able to help me.

Right now I am getting an internal server error.

I am trying to get the python script to run on my website [mydomain.com]. Here is what /etc/apache2/sites-enabled/mydomain.com looks like:

----------------------------- Start of File ---------------------------

<VirtualHost [IP Address]:80>
        ServerAdmin [email]info@mydomain.com[/email]
        ServerName mydomain.com
        ServerAlias mydomain.com *.mydomain.com
        DocumentRoot /srv/www/mydomain.com/public_html/
        ErrorLog /srv/www/mydomain.com/logs/error.log
        CustomLog /srv/www/mydomain.com/logs/access.log combined

</VirtualHost>

ScriptAlias /cgi-bin/ /srv/www/mydomain.com/public_html/cgi-bin/
<Directory "/srv/www/mydomain.com/public_html/cgi-bin">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
AddHandler cgi-script .py
AddHandler default-handler .html .htm
</Directory>

----------------------------- End of File ---------------------------

I made sure to restart apache after I added the CGI ScriptAlias to the above file. /etc/apache2/sites-enabled/mydomain.com and /etc/apache2/sites-available/mydomain.com are linked so that they are the same.

The .py file I'm trying to run is was created with vim, is located at /srv/www/mydomain.com/public_html/cgi-bin/test.py, and looks like this:

----------------------------- Start of File ---------------------------

print "Content-Type: text/html"

print 'hi'

----------------------------- End of File ---------------------------

I get the following errors from /srv/www/mydomain.com/logs/error.log:

Exec format error: exec of '/srv/www/mydomain.com/public_html/cgi-bin/test.py' failed
Premature end of script headers: test.py

I have also edited test.py so that "print "Content-Type: text/html"" is not there or so that it stands alone without being printed. I have also given it two newlines after "text/html" (\n\n). I have also included the following imports:

import cgitb; cgitb.enable()
import cgi
import pybel,openbabel
import random

This was done to no avail.

When I run the script from the command line by typing, "python test.py", it works fine. Permissions for the file are 755. 


Any help given is much appreciated!

---

### Post by gmargo on 2011-08-21
You need a "[she-bang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29")" line, and you need a blank line after the content type.  Here's a minimal "test.py" that works for me (plus the script in your referred thread also worked for me):
```

#!/usr/bin/python

print "Content-Type: text/html"
print ""

print 'hi'

```You mentioned this error:
> 
Exec format error: exec of '/srv/www/mydomain.com/public_html/cgi-bin/test.py' failed
Premature end of script headers: test.py
which is exactly the error that will occur if you do not have the "she-bang" line.

---

### Post by ifben on 2011-08-21
It works! In my referred thread I didn't realize "#!/usr/bin/python" was actually part of the file.

Thank you very much to people like you who have the patience to deal with airhead mistakes!

---

