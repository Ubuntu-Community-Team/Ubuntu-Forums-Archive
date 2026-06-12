---
title: "Problem with MYSQL,PHP5 and Apache 2 in Ubuntu 8.04 Desktop"
date: 2008-07-26
forum: Programming Talk
---

### Post by ivikas on 2008-07-26
Hello all,

         Iam using ubuntu 8.04 desktop and i want a LAMP server over it for local web development.I have read forum post and installed all the above package using sudo apt-get but iam unable to run php program as the firefox browser is offering it for download instead of running it.I have also installed mod-php5 module but still problems:

Here's the php status on my terminal

root@-desktop:~# php
php       php5      php5-cgi  php-cgi   
root@-desktop:~# php

root@-desktop:~# php --version
PHP 5.2.4-2ubuntu5.3 with Suhosin-Patch 0.9.6.2 (cli) (built: Jul 23 2008 06:44:49) 
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies
root@-desktop:~# 

This is apache conf file

-------------------------------------------------------------------------

#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

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
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
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
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
--------------------------------------------------------------------------

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          apache2
# Required-Start:    $local_fs $remote_fs $network $syslog
# Required-Stop:     $local_fs $remote_fs $network $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start/stop apache2 web server
### END INIT INFO
#
# apache2		This init.d script is used to start apache2.
#			It basically just calls apache2ctl.

ENV="env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin"

#[ `ls -1 /etc/apache2/sites-enabled/ | wc -l | sed -e 's/ *//;'` -eq 0 ] && \
#echo "You haven't enabled any sites yet, so I'm not starting apache2." && \
#echo "To add and enable a host, use addhost and enhost." && exit 0

#edit /etc/default/apache2 to change this.
HTCACHECLEAN_RUN=auto
HTCACHECLEAN_MODE=daemon
HTCACHECLEAN_SIZE=300M
HTCACHECLEAN_DAEMON_INTERVAL=120
HTCACHECLEAN_PATH=/var/cache/apache2/mod_disk_cache
HTCACHECLEAN_OPTIONS=""

set -e
if [ -x /usr/sbin/apache2 ] ; then
	HAVE_APACHE2=1
else
	echo "No apache MPM package installed"
	exit 0
fi

. /lib/lsb/init-functions

test -f /etc/default/rcS && . /etc/default/rcS
test -f /etc/default/apache2 && . /etc/default/apache2

APACHE2CTL="$ENV /usr/sbin/apache2ctl"
HTCACHECLEAN="$ENV /usr/sbin/htcacheclean"

check_htcacheclean() {
	[ "$HTCACHECLEAN_MODE" = "daemon" ] || return 1

	[ "$HTCACHECLEAN_RUN"  = "yes"    ] && return 0

	[ "$HTCACHECLEAN_RUN"  = "auto" \
	  -a -e /etc/apache2/mods-enabled/disk_cache.load ] && return 0
	
	return 1
}

start_htcacheclean() {
	$HTCACHECLEAN $HTCACHECLEAN_OPTIONS -d$HTCACHECLEAN_DAEMON_INTERVAL \
			-i -p$HTCACHECLEAN_PATH -l$HTCACHECLEAN_SIZE
				
}

stop_htcacheclean() {
	killall htcacheclean 2> /dev/null || echo ...not running
}

pidof_apache() {
    # if pidof is null for some reasons the script exits automagically
    # classified as good/unknown feature
    PIDS=`pidof apache2` || true

    PFILE=`. /etc/apache2/envvars ; echo $APACHE_PID_FILE`
    if [ -z "$PFILE" ] ; then
    	echo ERROR: APACHE_PID_FILE needs to be defined in /etc/apache2/envvars >&2
	exit 2
    fi

    [ -e $PFILE ] && PIDS2=`cat $PFILE`
    
    # if there is a pid we need to verify that belongs to apache2
    # for real
    for i in $PIDS; do
    	if [ "$i" = "$PIDS2" ]; then
            # in this case the pid stored in the
            # pidfile matches one of the pidof apache
            # so a simple kill will make it
            echo $i
            return 0
        fi
    done
    return 1
}

apache_stop() {
	if `$APACHE2CTL configtest > /dev/null 2>&1`; then
		# if the config is ok than we just stop normaly
                $APACHE2CTL graceful-stop
	else
		# if we are here something is broken and we need to try
		# to exit as nice and clean as possible
		PID=$(pidof_apache)

		if [ "${PID}" ]; then
			# in this case it is everything nice and dandy
			# and we kill apache2
			log_warning_msg "We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!"
                        kill $PID
		elif [ "$(pidof apache2)" ]; then
			if [ "$VERBOSE" != no ]; then
                                echo " ... failed!"
			        echo "You may still have some apache2 processes running.  There are"
 			        echo "processes named 'apache2' which do not match your pid file,"
			        echo "and in the name of safety, we've left them alone.  Please review"
			        echo "the situation by hand."
                        fi
                        return 1
		fi
	fi
}

# Stupid hack to keep lintian happy. (Warrk! Stupidhack!).
case $1 in
	start)
		log_daemon_msg "Starting web server" "apache2"
		if $APACHE2CTL start; then
			if check_htcacheclean ; then
				log_progress_msg htcacheclean
				start_htcacheclean || log_end_msg 1
			fi
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
	;;
	stop)
		if check_htcacheclean ; then
			log_daemon_msg "Stopping web server" "htcacheclean"
			stop_htcacheclean
			log_progress_msg "apache2"
		else
			log_daemon_msg "Stopping web server" "apache2"
		fi
		if apache_stop; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
	;;
	reload | force-reload)
		if ! $APACHE2CTL configtest > /dev/null 2>&1; then
                    $APACHE2CTL configtest || true
                    log_end_msg 1
                    exit 1
                fi
                log_daemon_msg "Reloading web server config" "apache2"
		if pidof_apache > /dev/null ; then
                    if $APACHE2CTL graceful $2 ; then
                        log_end_msg 0
                    else
                        log_end_msg 1
                    fi
                fi
	;;
	restart)
		if check_htcacheclean ; then
			log_daemon_msg "Restarting web server" "htcacheclean"
			stop_htcacheclean
			log_progress_msg apache2
		else
			log_daemon_msg "Restarting web server" "apache2"
		fi
		if ! apache_stop; then
                        log_end_msg 1 || true
                fi
		sleep 10
		if $APACHE2CTL start; then
			if check_htcacheclean ; then
				start_htcacheclean || log_end_msg 1
			fi
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
	;;
	start-htcacheclean)
		log_daemon_msg "Starting htcacheclean"
		start_htcacheclean || log_end_msg 1
		log_end_msg 0
	;;
	stop-htcacheclean)
		log_daemon_msg "Stopping htcacheclean"
			stop_htcacheclean
			log_end_msg 0
	;;
	*)
		log_success_msg "Usage: /etc/init.d/apache2 {start|stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean}"
		exit 1
	;;
esac
------------------------------------------------------------------------
Mysql verion

root@-desktop:~# mysql --version
mysql  Ver 14.12 Distrib 5.0.51a, for debian-linux-gnu (i486) using readline 5.2
root@-desktop:~#


Please give a urgent fix for this 

Thanks in advance

---

### Post by rzrgenesys187 on 2008-07-26
If you have installed all of the packages correctly, namely these ones

```
php5 php5-mysql mysql-client-5.0 mysql-server-5.0 apache2 libapache2-mod-auth-mysql libapache2-mod-php5
```

It may simply be that your server needs restarted with this code

```
sudo /etc/init.d/apache2 restart
```

Also make sure your php script is in the default apache directory which is /var/www and when you go to the web page you type 127.0.0.1 (redirect IP address) into the location bar

---

### Post by ivikas on 2008-07-26
hi rzrgenesys187,

             I checked your list with synaptic package manager and founfd thet php5 not installed and i installed php5 and so all the list you gave me was completely installed.but still the php scripts is not runnig just firefox offers it for a download...

---

### Post by cdekter on 2008-07-26
> **ivikas said:**
> hi rzrgenesys187,

             I checked your list with synaptic package manager and founfd thet php5 not installed and i installed php5 and so all the list you gave me was completely installed.but still the php scripts is not runnig just firefox offers it for a download...

Have you restarted Apache since you made these changes? Adding modules/config etc doesn't take effect until Apache is restarted (or reloaded)

---

### Post by ivikas on 2008-07-26
hi rzrgenesys187,


Only problem is with apoache2

libapache2-mod-php5 is installed


This is what i have done 

root@-desktop:/var/www# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                                 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                                                                          [ OK ]
root@-desktop:/var/www# 

i have ran a sample php script "helloworld.php" frpm commandline and it's working
i have also checked database connection with php  from command line

The only problem is that apache2 is not executing php scripts--The Firefox offers it to download....

Please Help i am after this for a 3 days.Any link any reference??

---

### Post by kaivalagi on 2008-07-26
Have you enabled the php module in apache2?

If not follow these steps:

[LIST=1]
[*]run **e2enmod** to list available mods
[*]enter **php5** to enable it (it must have been listed already)
[*]to make sure all is good run **sudo /etc/init.d/apache2 force-reload** then **sudo /etc/init.d/apache2 restart**
[/LIST]

Hope that helps

Edit:
You should probably have a read of this doc section on ubuntu.com if you haven't already: [https://help.ubuntu.com/8.04/serverguide/C/web-servers.html](https://help.ubuntu.com/8.04/serverguide/C/web-servers.html)

Under the php5 section there is this which my suggestion would fix:
*"By default, the Apache 2 Web server is configured to run PHP5 scripts. In other words, the PHP5 module is enabled in Apache2 Web server automatically when you install the module. Please verify if the files /etc/apache2/mods-enabled/php5.conf and /etc/apache2/mods-enabled/php5.load  exist. If they do not exists, you can enable the module using a2enmod command."*

---

### Post by ivikas on 2008-07-29
Hello All,

           I done some updates and grub error 17 problem arised.I have a single hdd of 300 GB and i have been using one partition of it.I did not found a way out so reinstalled everything and it's working.But still fears of grub error 17.What exact it is?Can reinstall of grub recover from this error.

---

### Post by kaivalagi on 2008-07-29
> **ivikas said:**
> Hello All,

           I done some updates and grub error 17 problem arised.I have a single hdd of 300 GB and i have been using one partition of it.I did not found a way out so reinstalled everything and it's working.But still fears of grub error 17.What exact it is?Can reinstall of grub recover from this error.

[http://ubuntuforums.org/showthread.php?t=872006&highlight=grub+error+17](http://ubuntuforums.org/showthread.php?t=872006&highlight=grub+error+17)

---

