---
title: "CGI Question"
date: 2007-04-24
forum: Programming Talk
---

### Post by jert on 2007-04-24
Greetings all.

I'm looking for assistance with a small CGI problem I'm working with ...

I've got a new install of Ubuntu Server 7.04, with CGI installed and ... sort of ... working.

I'm trying to install a script which uses an /img and /css subdirectory to format the output.  I've got the script executing in /usr/lib/cgi-bin, but it's giving me a text-only output.

All subdirectories and files belong to the www-data user/group.  The /img and /css directories have 755 permissions, and the images themselves have 644 permissions.

The appropriate section from my apache2 conf files are:

apache2.conf:

         AddHandler cgi-script .cgi

sites-available/default

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory /usr/lib/cgi-bin/>
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

Any ideas?

Thanks in advance,

- Jert


Update:  

From /var/www/apache2/error.log:

[Tue Apr 24 21:09:44 2007] [error] [client 192.168.1.12] (8)Exec format error: exec of '/usr/lib/cgi-bin/sim/css/base.css' failed, referer: [http://mystic/cgi-bin/sim/index.cgi](http://mystic/cgi-bin/sim/index.cgi)
[Tue Apr 24 21:09:44 2007] [error] [client 192.168.1.12] Premature end of script headers: base.css, referer: [http://mystic/cgi-bin/sim/index.cgi](http://mystic/cgi-bin/sim/index.cgi)

---

### Post by phossal on 2007-04-25
What is the question?

---

