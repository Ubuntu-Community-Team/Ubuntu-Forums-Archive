---
title: "apt-get notifications"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by know-it-some on 2008-08-21
I want to be able to be alerted each week to new packages that have updates available on the server.  I am thinking about writing a shell script that does pseudo-this:

checks for updates available via apt-get
writes that info to a log file
emails me the contents of the log files IF the file is greater than 145 bytes

The questions is how to code it.  What do people here recommend, something like:

apt-get -s dist-upgrade > /root/scripts/apt-check.log
if [I need help with this part...]
then
  mail [email]admin@domain.tld[/email] -s 'hadoop package updates' < /root/scripts/apt-check.log
fi

Thanks for any suggestions.

---

### Post by know-it-some on 2008-08-21
Actually, I went the perl route:

#!/usr/bin/perl

`apt-get -s dist-upgrade > /root/scripts/apt-check.log`;
if (-s '/root/scripts/apt-check.log' > 145) {
  `mail admin\@domain.tld -s 'hadoop package updates' < /root/scripts/apt-c
heck.log`;
}

---

### Post by know-it-some on 2008-08-21
And in case you are curious.  145 bytes is how big that file is if there are zero available updates.

---

