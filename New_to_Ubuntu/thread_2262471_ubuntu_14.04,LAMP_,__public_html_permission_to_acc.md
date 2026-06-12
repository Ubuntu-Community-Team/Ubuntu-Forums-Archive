---
title: "ubuntu 14.04,LAMP ,  public_html permission to access"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by unreal2 on 2015-01-25
Hi,

I'm looking for answers in the network but don't find help.
I used such methods as


```
**Forbidden**

 You don't have permission to access /~ad on this server.

 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at localhost Port 80

```

chmod 700 or 755 not working.
```
ad@pc:~$ chmod 700 public_html/ -R
ad@pc:~$ ls -l public_html/
razem 12
-rwx------ 1 ad ad 20 sty 24 17:16 info.php

```

```
/home/ad/public_html/
```

a2enmod userdir , 
/etc/apache2/mods-enabled/userdir.conf 
```
UserDir public_html
     UserDir disabled root
     UserDir enabled ad
    <Directory /home/*/public_html>
```
/etc/apache2/apache2.conf 
```
<Directory /home/*/public_html>

```

and probably some I forgot to write.

Pls help me and sorry for my english.

---

### Post by Doug S on 2015-01-25
The recommendation is to get your public_html access working in two steps: First so that regular html works (i.e. index.html); And second so that PHP works.> **unreal2 said:**
> chmod 700 or 755 not working.
```
ad@pc:~$ chmod 700 public_html/ -R
ad@pc:~$ ls -l public_html/
razem 12
-rwx------ 1 ad ad 20 sty 24 17:16 info.php

```That will not work, use 755 and check parent directory access permissions also. Put and index.html file there and try that first.> **unreal2 said:**
> a2enmod userdir , 
/etc/apache2/mods-enabled/userdir.conf 
```
UserDir public_html
     UserDir disabled root
     UserDir enabled ad
    <Directory /home/*/public_html>
```O.K. good. I assume you have just listed part of the userdir.conf here. If not just restore the original file.> **unreal2 said:**
> /etc/apache2/apache2.conf 
```
<Directory /home/*/public_html>

```I don't know what you are showing here. Just restore the original file, which doesn't have any such line.

O.K. now once you have it working for index.html, you have to enable php in the user directory, as it does not work by default. Edit /etc/apache2/mods-available/php5.conf, the file itself tells you what to do, but here is mine:```
doug@s15:/etc/libvirt/qemu$ [COLOR=#ff0000]cat /etc/apache2/mods-available/php5.conf[/COLOR]
<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
        SetHandler application/x-httpd-php-source
    </FilesMatch>
[COLOR=#ff0000]    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.)[/COLOR] Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
#   <IfModule mod_userdir.c>
#       <Directory /home/*/public_html>
#           php_admin_value engine Off
#       </Directory>
#   </IfModule>
</IfModule>
doug@s15:/etc/libvirt/qemu$
```and, of course, for changes to take effect:```
sudo service apache2 restart
```

---

### Post by unreal2 on 2015-01-26
Still not working any ideas?
I have an encrypted LVM all disk. And Ubuntu encrypted home catalog.

 What else can I show you?

ls -l home
```
ad@pc:/$ ls -l home
razem 16
-rw-r--r--  1 root root   177 gru  1 09:52 a
drwx------ 49 ad   ad   12288 sty 26 10:32 ad

```

ls -l ad
```
ad@pc:/home$ ls -l ad
razem 3124304
-rw-rw-r--  1 ad   ad        38259 sty  5 17:42 1000s&#322;ów.odt
drwxr-xr-x  7 root root       4096 sty  7 09:10 ChomikBox
drwxr-xr-x  6 ad   ad         4096 sty 25 09:07 Dokumenty
drwx------  7 ad   ad         4096 sty 26 10:33 Dropbox
drwxr-xr-x  2 ad   ad         4096 gru  2 18:17 dwhelper
-rw-r--r--  1 ad   ad         8980 lis 29 15:02 examples.desktop
drwxr-xr-x  2 ad   ad         4096 gru  2 18:17 Muzyka
drwxr-xr-x  5 ad   ad         4096 sty 22 17:20 Obrazy
drwxrwxr-x  5 ad   ad         4096 gru 23 11:47 perl5
-rw-r--r--  1 ad   ad   3199123456 gru  1 18:24 pl_a.iso
drwxr-xr-x 16 ad   ad        16384 sty 20 17:04 Pobrane
drwxrwxr-x  3 ad   ad         4096 sty 12 14:24 d
drwxr-xr-x  2 ad   ad         4096 sty 26 12:09 public_html
drwxr-xr-x  2 ad   ad         4096 lis 29 15:15 Publiczny
drwxr-xr-x  2 ad   ad         4096 gru 26 14:51 Pulpit
drwxr-xr-x  2 ad   ad         4096 lis 29 15:15 Szablony
drwxrwxr-x 11 ad   ad         4096 sty 23 12:26 VirtualBox VMs
drwxr-xr-x  2 ad   ad         4096 sty 22 20:24 Wideo
drwxrwxr-x  3 ad   ad         4096 gru 22 14:50 dzielony
drwxrwxr-x  3 ad   ad         4096 gru 22 15:13 work
ad@pc:/home$ 


```

chmod  755 public_html -R
```
ad@pc:~$ ls -l public_html/
razem 32
-rwxr-xr-x 1 ad ad 32 sty 26 12:09 a.html
-rwxr-xr-x 1 ad ad  0 sty 26 12:09 a.html~
-rwxr-xr-x 1 ad ad 20 sty 24 17:16 info.php

```
cat /etc/apache2/mods-available/php5.conf
```
ad@pc:~$ cat /etc/apache2/mods-available/php5.conf
<FilesMatch ".+\.ph(p[345]?|t|tml)$">
    SetHandler application/x-httpd-php
</FilesMatch>
<FilesMatch ".+\.phps$">
    SetHandler application/x-httpd-php-source
    # Deny access to raw php sources by default
    # To re-enable it's recommended to enable access to the files
    # only in specific virtual host or directory
    Order Deny,Allow
    Deny from all
</FilesMatch>
# Deny access to files without filename (e.g. '.php')
<FilesMatch "^\.ph(p[345]?|t|tml|ps)$">
    Order Deny,Allow
    Deny from all
</FilesMatch>

# Running PHP scripts in user directories is disabled by default
# 
# To re-enable PHP in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.
#<IfModule mod_userdir.c>
 #   <Directory /home/*/public_html/>
       # php_admin_flag engine Off
  #  </Directory>
#</IfModule>


```
cat /etc/apache2/apache2.conf
```
ad@pc:~$ cat /etc/apache2/apache2.conf 
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.4/ for detailed information about
# the directives and /usr/share/doc/apache2/README.Debian about Debian specific
# hints.
#
#
# Summary of how the Apache 2 configuration works in Debian:
# The Apache 2 web server configuration in Debian is quite different to
# upstream's suggested way to configure the web server. This is because Debian's
# default Apache2 installation attempts to make adding and removing modules,
# virtual hosts, and extra configuration directives as flexible as possible, in
# order to make automating the changes and administering the server as easy as
# possible.

# It is split into several files forming the configuration hierarchy outlined
# below, all located in the /etc/apache2/ directory:
#
#       /etc/apache2/
#       |-- apache2.conf
#       |       `--  ports.conf
#       |-- mods-enabled
#       |       |-- *.load
#       |       `-- *.conf
#       |-- conf-enabled
#       |       `-- *.conf
#       `-- sites-enabled
#               `-- *.conf
#
#
# * apache2.conf is the main configuration file (this file). It puts the pieces
#   together by including all remaining configuration files when starting up the
#   web server.
#
# * ports.conf is always included from the main configuration file. It is
#   supposed to determine listening ports for incoming connections which can be
#   customized anytime.
#
# * Configuration files in the mods-enabled/, conf-enabled/ and sites-enabled/
#   directories contain particular configuration snippets which manage modules,
#   global configuration fragments, or virtual host configurations,
#   respectively.
#
#   They are activated by symlinking available configuration files from their
#   respective *-available/ counterparts. These should be managed by using our
#   helpers a2enmod/a2dismod, a2ensite/a2dissite and a2enconf/a2disconf. See
#   their respective man pages for detailed information.
#
# * The binary is called apache2. Due to the use of environment variables, in
#   the default configuration, apache2 needs to be started/stopped with
#   /etc/init.d/apache2 or apache2ctl. Calling /usr/bin/apache2 directly will not
#   work with the default configuration.


# Global configuration
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the Mutex documentation (available
# at <URL:http://httpd.apache.org/docs/2.4/mod/core.html#mutex>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
Mutex file:${APACHE_LOCK_DIR} default

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 5


# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog ${APACHE_LOG_DIR}/error.log

#
# LogLevel: Control the severity of messages logged to the error_log.
# Available values: trace8, ..., trace1, debug, info, notice, warn,
# error, crit, alert, emerg.
# It is also possible to configure the log level for particular modules, e.g.
# "LogLevel info ssl:warn"
#
LogLevel warn

# Include module configuration:
IncludeOptional mods-enabled/*.load
IncludeOptional mods-enabled/*.conf

# Include list of ports to listen on
Include ports.conf


# Sets the default security model of the Apache2 HTTPD server. It does
# not allow access to the root filesystem outside of /usr/share and /var/www.
# The former is used by web applications packaged in Debian,
# the latter may be used for local directories served by the web server. If
# your system is serving content from a sub-directory in /srv you must allow
# access here, or in any related virtual host.
<Directory />
        Options FollowSymLinks
        AllowOverride None
        Require all denied
</Directory>

<Directory /usr/share>
        AllowOverride None
        Require all granted
</Directory>

<Directory /var/www/html>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

#<Directory /srv/>
#       Options Indexes FollowSymLinks
#       AllowOverride None
#       Require all granted
#</Directory>




# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#
AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<FilesMatch "^\.ht">
        Require all denied
</FilesMatch>


#
# The following directives define some format nicknames for use with
# a CustomLog directive.
#
# These deviate from the Common Log Format definitions in that they use %O
# (the actual bytes sent including headers) instead of %b (the size of the
# requested file), because the latter makes it impossible to detect partial
# requests.
#
# Note that the use of %{X-Forwarded-For}i instead of %h is not recommended.
# Use mod_remoteip instead.
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
IncludeOptional conf-enabled/*.conf

# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet


```
cat /etc/apache2/mods-enabled/userdir.conf
```
ad@pc:~$ cat /etc/apache2/mods-enabled/userdir.conf 
<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html/>
                AllowOverride ALL 
                 #FileInfo AuthConfig Limit Indexes
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Require all granted
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Require all denied
                </LimitExcept>
        </Directory>
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet


```

```
ad@pc:~$ ls /etc/apache2/mods-enabled/
access_compat.load  authz_user.load  filter.load       php5.load
alias.conf          autoindex.conf   mime.conf         setenvif.conf
alias.load          autoindex.load   mime.load         setenvif.load
auth_basic.load     deflate.conf     mpm_prefork.conf  status.conf
authn_core.load     deflate.load     mpm_prefork.load  status.load
authn_file.load     dir.conf         negotiation.conf  userdir.conf
authz_core.load     dir.load         negotiation.load  userdir.load
authz_host.load     env.load         php5.conf
ad@pc:~$ 


```

---

### Post by yancek on 2015-01-26
Have you verified that your user is part of the Apache group?  In Ubuntu, that should be the group:  www-data.  Might try changing the group for public_html to www-data.

---

### Post by Doug S on 2015-01-26
This:
> **unreal2 said:**
> ```
ad@pc:/$ ls -l home
razem 16
-rw-r--r--  1 root root   177 gru  1 09:52 a
drwx------ 49 ad   ad   12288 sty 26 10:32 ad

```Needs to be at least this:```
ad@pc:/$ ls -l home
razem 16
-rw-r--r--  1 root root   177 gru  1 09:52 a
drwx[COLOR=#ff0000]r[/COLOR]-[COLOR=#ff0000]xr[/COLOR]-[COLOR=#ff0000]x[/COLOR] 49 ad   ad   12288 sty 26 10:32 ad
```

Edit: > **unreal2 said:**
> I have an encrypted LVM all disk. And Ubuntu encrypted home catalog.I have no experience with encrypted directories, but it makes sense that it might be a problem. I don't know.

---

### Post by unreal2 on 2015-01-26
```
sudo chown -R www-data:www-data /home/ad/public_html
sudo adduser ad www-data 
sudo chmod -R 775 /home/ad/public_html 
```

and I had to change
```
cd /home
chmod 755 ad
```

 
 
 Now works great thank you very much.

---

