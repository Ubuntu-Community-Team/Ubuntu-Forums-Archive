---
title: "Who to Running lightTPD and php on Ubuntu edy ?"
date: 2007-01-31
forum: Programming Talk
---

### Post by thijs on 2007-01-31
I need a good conf file of lighttpd!.:KS

---

### Post by Mirrorball on 2007-01-31
You would get more answers if you had posted this in the Servers and Security forum. ;)

---

### Post by erikringmar on 2007-02-02
Please let me know if you're getting a reply to this elsewhere.  I'm struggling with the lighttpd.conf as well.

Erik

---

### Post by po0f on 2007-02-03
/etc/lighttpd/conf-available/10-fastcgi.conf
```
[FONT="Courier New"]
## FastCGI programs have the same functionality as CGI programs,
## but are considerably faster through lower interpreter startup
## time and socketed communication
##
## Documentation: /usr/share/doc/lighttpd-doc/fastcgi.txt.gz
##                [http://www.lighttpd.net/documentation/fastcgi.html](http://www.lighttpd.net/documentation/fastcgi.html)

server.modules   += ( "mod_fastcgi" )

## Start an FastCGI server for php4 (needs the php4-cgi package)
**## ADDED: changed all instances of php4 with php5**
fastcgi.server    = ( ".php" => 
    ((
        "bin-path" => "/usr/bin/php**5**-cgi",
        "socket" => "/tmp/php.socket",
        "max-procs" => 2,
        "idle-timeout" => 20,
        "bin-environment" => ( 
            "PHP_FCGI_CHILDREN" => "4",
            "PHP_FCGI_MAX_REQUESTS" => "10000"
        ),
        "bin-copy-environment" => (
            "PATH", "SHELL", "USER"
        ),
        "broken-scriptfilename" => "enable"
    ))
)
[/FONT]
```

Requires that [php5-cgi](http://packages.ubuntu.com/edgy/web/php5-cgi) be installed.  (What I added is in bold.)

---

