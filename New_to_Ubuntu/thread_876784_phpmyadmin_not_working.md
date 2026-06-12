---
title: "phpmyadmin not working"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by amai on 2008-08-01
Followed this thread still phpmyadmin not working.

[http://ubuntuforums.org/showthread.php?t=841173](http://ubuntuforums.org/showthread.php?t=841173)

I am getting the following errors

[http://172.16.1.2/myphpadmin](http://172.16.1.2/myphpadmin)

Firefox can't find the server at avg.urlseek.vmn.net.


[http://172.16.1.2/myphpadmin](http://172.16.1.2/myphpadmin)

Firefox can't establish a connection to the server at 172.16.1.2.

everything else is working but phpmyadmin





Here is the output of


# less /etc/apache2/conf.d/phpmyadmin.conf
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
        Options Indexes FollowSymLinks
        DirectoryIndex index.php

        # Authorize for setup
        <Files setup.php>
            # For Apache 1.3 and 2.0
            <IfModule mod_auth.c>
                AuthType Basic
                AuthName "phpMyAdmin Setup"
                AuthUserFile /etc/phpmyadmin/htpasswd.setup
            </IfModule>
            # For Apache 2.2
            <IfModule mod_authn_file.c>
                AuthType Basic
                AuthName "phpMyAdmin Setup"
                AuthUserFile /etc/phpmyadmin/htpasswd.setup
            </IfModule>
            Require valid-user
        </Files>
        <IfModule mod_php4.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_value include_path .
        </IfModule>
        <IfModule mod_php5.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_value include_path .
        </IfModule>
</Directory>

(END)

---

### Post by indytim on 2008-08-01
I recommend using the file browser of choice, find the exact location of the index.php for the local install of phpMyAdmin.  In your browser do the 
http://localhost/<phpmyadmin folder>/index.php

IndyTim

---

### Post by ByteJuggler on 2008-08-01
The URL for phpmyadmin is usually 

```
http://localhost/**phpmyadmin**
```

and not (as you put)

```
http://localhost/[COLOR="Red"]**myphpadmin**[/COLOR]
```

---

