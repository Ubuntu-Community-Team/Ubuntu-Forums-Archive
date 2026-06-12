---
title: "Help for a beginner trying to use cgi python and apache"
date: 2016-04-20
forum: Programming Talk
---

### Post by natibo on 2016-04-20
First of all, I have searched the forums and tried just about everything I have found.
Second:
my OS is ubuntu 15.10
I'm using python 3.4
Apache2 (which I admit I know nothing about but downloaded to try to get this to work)
I have tried all of the suggestions at this site [https://www.linux.com/blog/configuring-apache2-run-python-scripts]("https://www.linux.com/blog/configuring-apache2-run-python-scripts")

I have gone through Mark Lutz's book "Learning Python.
I am know going through his book "Python Programming". I know it is dated and I know his examples are more "Windows" centric, but oh well. I'm a 50 year old enginner who is home recovering from surgery and thought I would learn Python.

Program 1 executed from working directory and pulled up by firefox after double clicking:

```
<html>
<title>Interactive Page</title>
<body>
<form method=POST action="cgi-bin/cgi101.py">
    <P><B>Enter your name:</B>
    <P><input type=text name=user>
    <P><input type=submit>
</form>
</body></html>
```

here is the second program located in the cgi-bin sub-directory of the working directory:

```
    #!/usr/bin/env python3 (this file was made executable by chmod)

    # -*- coding: UTF-8 -*-# enable debugging

    import cgi, cgitb
    cgitb.enable()
    form = cgi.FieldStorage()                 # parse form data
    print('Content-type: text/html\n')        # hdr plus blank line
    print('<title>Reply Page</title>')        # html reply page
    if not 'user' in form:
        print('<h1>Who are you?</h1>')
    else:
        print('<h1>Hello <i>%s</i>!</h1>' % cgi.escape(form['user'].value))

```

This is what I get:

[IMG]https://goo.gl/photos/6Vw73Cu2k7LfJgkv6[/IMG]

If you can't see the picture firefox has a pop up window asking me what firefox should do with this file.
Here is my apache2.conf file
```
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
    #   /etc/apache2/
    #   |-- apache2.conf
    #   |   `--  ports.conf
    #   |-- mods-enabled
    #   |   |-- *.load
    #   |   `-- *.conf
    #   |-- conf-enabled
    #   |   `-- *.conf
    #    `-- sites-enabled
    #       `-- *.conf
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

    #Bo Edit

    ServerName localhost
    <Directory "/home/*/public_html">
        Options +ExecCGI
        AddHandler cgi-script .cgi
    </Directory>

    <Directory "/home/Dropbox/apache2">
        Options +ExecCGI
       SetHandler cgi-script
    </Directory>

    <Directory "/home/Dropbox/apache2">
       Options +ExecCGI
       AddHandler cgi-script .py
    </Directory>

    ScriptAlias "/cgi-bin/" "/var/www/html/cgi-bin"
    <Directory "/var/www/html/cgi-bin">
        AllowOverride None
        Options +ExecCGI +MultiViews +SymLinksIfOwnerMatch +Includes +Multiviews
        Order allow,deny
        Allow from all
        AddHandler cgi-script .py
        AddHandler cgi-script .cgi
        AddHandler wsgi-script .wsgi
    </Directory>

    AddHandler cgi-script .cgi

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

    <Directory /var/www/>
       Options Indexes FollowSymLinks
       AllowOverride None
       Require all granted
    </Directory>

    #<Directory /srv/>
    #   Options Indexes FollowSymLinks
    #   AllowOverride None
    #   Require all granted
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

I have spent about 2 days trying to get this to work. Any help would be appreciated.

---

### Post by frostschutz on 2016-04-21
If it offers you the script as download, it's not executing it... in the best case it's just an executable flag missing (chmod +x yourstuff.py), worst case something about your webserver config is off. Also try to run it in the terminal and see if it reports any syntax errors. The code you posted is indented in a way that would make the script not work (4 spaces before #!, perhaps just an issue with the way you copy&pasted it)

Python CGI (and CGI in general really) is unusual. If it must be Apache you could have a look at Python WSGI which is the successor of mod_python (which you should no longer use).

If it doesn't have to be Apache, you could have your Python script itself be the webserver. The advantage of that solution is that the whole thing is Python, the case where your code does not run but offered as download instead, does not exist ;) there are many libraries/packages/frameworks that work in this direction, for example Flask.

Python 2 and Python 3 have significant differences, if your book is dated you should use Python 2 instead, or get a book that actually covers Python 3 already. Otherwise (if you're just starting out, learning) you will be confused by the differences between the two.

---

