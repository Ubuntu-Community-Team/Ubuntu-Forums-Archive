---
title: "Heckuva time with start-stop-daemon"
date: 2010-03-30
forum: Programming Talk
---

### Post by Bean Street on 2010-03-30
We run a parallel processing farm with Matlab appservers, formerly on CentOS we are now moving all to Jaunty 9.04.  That's the good news.  The bad news is that our processing daemon (written on the old daemon interface, ie. /etc/init.d/functions) isn't working out on Ubuntu.  I do not want to throw in the towel!!!  So thanks for any wisdom you can share.

The particulars:

ISSUE: matlab runs flexlm, and we must execute under the installed user account.

So my thought (start-stop-daemon newbie) was to --chuid to that account (also named matlab):

start-stop-daemon --start --oknodo --background --chuid matlab:matlab --name "pq_daemon.pl -q $name" --startas $DAEMON -- -q $name -p $PIDFILE

I can see in the ps -ef listing that I have succeeded in switching the $DAEMON from running as root to running as matlab, eg:

matlab   27828     1  0 09:30 ?        00:00:00 /usr/bin/perl -w /home/matlab/QFDC/tools/pq/pq_daemon.pl -q daily -p /var/log/qfdc/pq/pqd.daily.pid

but the environment is root's, not matlab's!  (Don't let me confuse you, the account name is matlab as is the application!) Further, this line in the $DAEMON:

Log( $ENV{USER} );

gives:

root

What gives?  I obviously am out of my league or something.  What did I miss?  Any ideas for what to do?

THANKS A LOT!!!

---

### Post by Bean Street on 2010-03-30
Switching this:  sudo /etc/init.d/pqd restart

to this (duh):

/etc/init.d/pqd

works!! 
Now the daemon gives $USER = matlab.

---

