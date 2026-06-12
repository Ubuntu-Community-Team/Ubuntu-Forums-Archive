---
title: "access.log logging differently"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by Rob-Zilla on 2014-02-22
Hello Ubuntu Community,

I have a minor problem, my access.log file located in /var/log/apache2 used to log ip addresses like so: 

Where 'X' represents any number to make an IP address:

XX.XXX.XX.XX - GET...TIME.... /path/to/mywebsite 200 etc etc

but recently it has been logging information like so:

c-comcast-XX-XXX-XXX-XX-.com - GET...TIME.... /path/to/mywebsite 200 etc etc

I haven't changed anything and my apache config file has not been tampered with nor have I adjusted the way it logs.

Any insight would be greatly appreciated, its not a big deal but its a bit annoying.

Thanks a bunch for any help!

---

### Post by Lars Noodén on 2014-02-22
What is the current value of [HostnameLookups](http://httpd.apache.org/docs/2.4/mod/core.html#hostnamelookups) in your virtual host's configuration file?

---

### Post by Rob-Zilla on 2014-02-22
Hello Lars,

this is what my /etc/apache2/sites-available/default file looks like (I hope I grabbed I'm providing you with the info you mentioned)


<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
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


Thanks for the help :)

:EDIT: 

#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

---

### Post by Lars Noodén on 2014-02-22
> **Rob-Zilla said:**
> 
HostnameLookups Off

That's how it should be.  Perhaps there is another location?

```

grep -ir HostnameLookups /etc/apache2/*

```

---

### Post by Rob-Zilla on 2014-02-22
After running the suggested command I got the following

> /etc/apache2/apache2.conf:# HostnameLookups: Log the names of clients or just their IP addresses
/etc/apache2/apache2.conf:HostnameLookups Off


Could there be something else causing this?

---

