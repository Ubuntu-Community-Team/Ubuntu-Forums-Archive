---
title: "Perl: problem making program a daemon"
date: 2007-08-28
forum: Programming Talk
---

### Post by crazygerad on 2007-08-28
UPDATE August 28 2007: Sorry it was my fault I hardcoded the wrong value. Try not to set the outputs to devnulls until you check everything is ok.

I am developing an application to monitor an FTP folder, look for xml files, interpret them and send them on their way to a database. It is written in Perl and it works perfectly dies like it should with signals and transfers ok.

Problem is that I want to make it run as a daemon so as as soon as the computer starts it is continually checking this ftp folder. I have read many perl tutorials and the whole init.d rc.d topics but as soon as I start the script it forks and then dies. There is no process in ps ax and I cant kill what doesn't exist.

```

#!/usr/bin/perl
#prog.pl

use strict;
#Imports
use XML::Simple;
use Data::Dumper;
use DBD::Pg;
use Net::FTP;
use Getopt::Std;
use DBI;
#use Proc::Daemon;
use POSIX qw(setsid); #to use as a daemon

....code here to read the XML

procCMDFlags(); #depending on the flag -i messages are printed or not
if ($printMsg == 1)
{
   initialize ();
   main ();
}
else
{
   $printMsg = 1; #to force output of messages
   condPrint("Starting Service\n");   
   unless(my $pid = fork()) {
        condPrint("\$pid not defined cant fork") if (! defined $pid);
    	condPrint("\$pid recieved is".$pid."\n");
        exit if $pid;
        writePIDFile ($pid);
   	setsid;
        chdir("/");
   	umask 0;

        open (STDIN,  '/dev/null') or die "Can't read /dev/null: $!";
        open (STDOUT, '>$stdoutFile');
        open (STDERR, '>$errorFile');
        initialize ();
	main ();          #contains the infinitte loop while $var {}
   } # unless(my $pid = fork())
   condPrint("Ending Service\n");
} #else if ($printMsg == 1)

sub initialize {
   $SIG{INT} = \&catch_sig; #just sets the infinite variable to false
   $SIG{TERM} = \&catch_sig;
   $SIG{'HUP' } = \&catch_sig;
   $SIG{'ABRT'} = \&catch_sig;
   $SIG{'QUIT'} = \&catch_sig;
   $SIG{'TRAP'} = \&catch_sig;
   $SIG{'STOP'} = \&catch_sig;   
   
   readConfigFile();

   #initializing database
   $dbh = DBI->connect("dbi:Pg:dbname=$db_name",
                       "$db_user",
                       "$db_pass",
                       {
                         RaiseError => 1,
                         AutoCommit => 0
                       });
   if (!$dbh) {
      writeToLogFile("error", "Failed to start for not being able  to start the database connection");
      die "ERR: Couldn't open database connection: " . $DBI::errstr."\n";
   }
   
} # sub initialize

sub writePIDFile {
   my $recParamsSize = @_;
   if ($recParamsSize == 0)
   {
      die ("Wrong parameters qty writePIDFile\n");
   }
   open(PIDFILE, "> /var/run/prog.pid") || die ("Couldn't write to PID file\n");
   print(PIDFILE "$_[0]");
   close(PIDFILE);
} #END writePIDFile

 
```

I used the skeleton file in init to write the script
**prog.sh**
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:         
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: Example initscript
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
### END INIT INFO

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="XML monitor daemon"
NAME=prog
DAEMON=/usr/sbin/${NAME}.pl
DAEMON_ARGS=""
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/${NAME}.sh

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
		$DAEMON_ARGS \
		|| return 2
	# Add code here, if necessary, that waits for the process to be ready
	# to handle requests from services started subsequently which depend
	# on this one.  As a last resort, sleep for some time.
}

#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Wait for children to finish too if this is a daemon that forks
	# and if the daemon is only ever run from this initscript.
	# If the above conditions are not satisfied then add some other code
	# that waits for the process to drop all resources that could be
	# needed by services started subsequently.  A last resort is to
	# sleep for some time.
	start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
	[ "$?" = 2 ] && return 2
	# Many daemons don't delete their pidfiles when they exit.
	rm -f $PIDFILE
	return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
	#
	# If the daemon can reload its configuration without
	# restarting (for example, when it is sent a SIGHUP),
	# then implement that here.
	#
	start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
	return 0
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  #reload|force-reload)
	#
	# If do_reload() is not implemented then leave this commented out
	# and leave 'force-reload' as an alias for 'restart'.
	#
	#log_daemon_msg "Reloading $DESC" "$NAME"
	#do_reload
	#log_end_msg $?
	#;;
  restart|force-reload)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

:
```

Since I have been suffering with this for a while I made a makefile to install it and uninstall it.
**Makefile**

```
#Makefile

install:
	sudo cp /home/projects/xml/prog.pl /usr/sbin/prog.pl
	sudo cp /home/projects/xml/prog.conf /usr/share/prog/prog.conf
	sudo cp /home/projects/xml/prog.sh /etc/init.d/prog.sh
	sudo ln -s /etc/init.d/prog.sh /etc/rc2.d/S99prog
	sudo ln -s /etc/init.d/prog.sh /etc/rc2.d/K01prog

```

---

### Post by trwww on 2007-08-29
Hi,

I would just add a crontab entry that runs the program every 10 minutes.

Regards,

trwww

---

### Post by skeeterbug on 2007-08-29
> **trwww said:**
> Hi,

I would just add a crontab entry that runs the program every 10 minutes.

Regards,

trwww

I was going to suggest the same thing. I have a cron job set to run the 1st of every month at midnight. The crontab entry is very simple:

```

m  h  dom mon dow command
01 00 01 * * cd /home/skeeterbug/usage/ && perl usage.pl >> /home/skeeterbug/usage/usage.log

```

---

