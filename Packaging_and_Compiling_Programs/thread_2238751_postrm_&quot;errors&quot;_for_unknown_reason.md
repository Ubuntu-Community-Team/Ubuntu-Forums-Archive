---
title: "postrm &quot;errors&quot; for unknown reason"
date: 2014-08-09
forum: Packaging and Compiling Programs
---

### Post by wolfgentleman on 2014-08-09
Here is my postrm script:
```
#!/bin/bashif [ "$1" = "purge" ]
then
        echo "Unaccepting License Agreement..."
        if [ -e /usr/share/debconf/confmodule ]
        then
                . /usr/share/debconf/confmodule
                db_purge
        fi
        echo "Removing Server Databases..."
        rm -r /opt/ts3/server-db
        exit 0
else
        echo "Removing Logs..."
        rm -r /var/log/ts3/server*
        echo "Removing Service..."
        rm /etc/init.d/ts3-server
        update-rc.d -f ts3-server remove &> /dev/null
        echo " Note: The server database, whitelist/blacklist, and files were not removed."
        echo "       They may be found in '/opt/ts3/server-db'"
        echo "       If you are purging ts3-server, it will be removed in the next step."
        exit 0
fi
```
And here is the output of 'apt-get purge ts3-server':
```
Removing ts3-server ...
Delinking...
Removing Logs...
Removing Service...
 Note: The server database, whitelist/blacklist, and files were not removed.
       They may be found in '/opt/ts3/server-db'
       If you are purging ts3-server, it will be removed in the next step.
Purging configuration files for ts3-server ...
Unaccepting License Agreement...
Removing Server Databases...
dpkg: error processing ts3-server (--purge):
 subprocess installed post-removal script returned error exit status 128
Errors were encountered while processing:
 ts3-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
What am I doing wrong? I can't seem to figure it out. I've tried '&>/dev/null' ing 'rm -r /opt/ts3/server-db' in hopes it was the rm command and that would nullify the error code... but it didn't work :-(

---

