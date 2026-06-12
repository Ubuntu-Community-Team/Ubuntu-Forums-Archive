---
title: "WSGI / python module import quesion"
date: 2010-05-19
forum: Programming Talk
---

### Post by blake82 on 2010-05-19
Hi All,

I've been playing around with wsgi on 10.04, and I'm having trouble importing modules I've written in the project directory when running in daemon mode with apache.

I've tried setting an additional python path like this in both apache.conf and wsgi.conf (but not simultaneously):

```
WSGIPythonPath directory|/home/blake/workspace/testWebApp001/src
```

...and am getting no love. I always get an internal server error and a message in the log saying that that the module I'm trying to import doesn't exist. However, the standard library modules import with no problem.

Also, sys.argv[0] is mod_wsgi instead of /home/blake/workspace/testWebApp001/src/testApp001.py

Finally, when I test the program with wsgiref.simple_server, everything works fine.

Any ideas?

Thanks,

Blake

PS: Here's my virtual host file for the test site:

```
<VirtualHost *:80>

	ServerName www.testsite.com
	ServerAlias testsite.com
	ServerAdmin blake@testsite.com

	DocumentRoot /var/www/testSite001
	Alias /robots.txt /var/www/testSite001/robots.txt
	Alias /favicon.ico /var/www/testSite001/favicon.ico
	Alias /media/ /var/www/testSite001/media/

	<Directory /var/www/testSite001>
	Order allow,deny
	Allow from all
	</Directory>

	WSGIDaemonProcess testsite.com processes=1 threads=15 display-name=%{GROUP}
	WSGIProcessGroup testsite.com
	
	WSGIScriptAlias / /home/blake/workspace/testWebApp001/src/testApp001.py

	<Directory /home/blake/workspace/testWebApp001/src>
	Order allow,deny
	Allow from all
	</Directory>

	LogLevel info

</VirtualHost>
```

---

### Post by DaithiF on 2010-05-21
Hi,
I tend to make whatever additions I need to the python path within my wsgi script itself, so for example if your wsgi script is within the directory you want to add, then this code:

```
import os, sys
sys.append(os.path.dirname(__file__))
```
at the top of your wsgi script will do the trick.

---

