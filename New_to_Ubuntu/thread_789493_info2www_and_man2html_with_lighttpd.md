---
title: "info2www and man2html with lighttpd"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by bilodeau on 2008-05-10
Howdy,

I've been using ubuntu for a couple of years now, and am really impressed with the consistent improvements.  Unfortunately, things for me hit a snag when I did a fresh install of 8.04 a few days ago.

I like to use man2html and info2www to look at man and info pages with firefox via the lighttpd program.  This worked without a hitch in 7.10.  I upgraded to 8.04, installed the relevant progams, and now I get a "404 - Not Found" error whenever I try to look at either the man2html link: [http://localhost/cgi-bin/man/man2html](http://localhost/cgi-bin/man/man2html)
, or at the info2www link:
[http://localhost/cgi-bin/info2www](http://localhost/cgi-bin/info2www)
.

I've done some basic checks - yes, lighttpd is running via checking with ps, yes cgi-bin is enabled in the /etc/lighttpd/conf-enabled directory.  If I just point firefox at [http://localhost/](http://localhost/), I get the default welcome/placeholder page.  I have set the localhost option in the config file at /etc/lighttpd/lighttpd.conf.

What else can I do to track down this strange error?  With the same configuration, under 7.10, I could look at man and info pages via my web browser to my heart's content.

Aarrgghh!

Thank you for any help,
Paul

---

### Post by Monicker on 2008-05-10
I've never used lighttpd myself, but does it write to any log files in /var/log?  Perhaps a more descriptive error message might be listed there.

---

### Post by bilodeau on 2008-05-10
Howdy Again,
Here is a brief snippet from /var/log/lighttpd/access.log:

127.0.0.1 localhost - [10/May/2008:13:39:36 -0600] "GET /cgi-bin/info2www HTTP/1.1" 404 345 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.14) Gecko/20080404 Firefox/2.0.0.14"
127.0.0.1 localhost - [10/May/2008:13:39:45 -0600] "GET /cgi-bin/man/man2html HTTP/1.1" 404 345 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.14) Gecko/20080404 Firefox/2.0.0.14"

In /var/log/lighttpd/error.log I get:
2008-05-10 13:59:27: (log.c.75) server started 
2008-05-10 13:59:27: (server.c.931) WARNING: unknown config-key: debug.dump-unknown-headers (ignored)

From what I see, nothing is reported as an error, and the entries in the access.log are saying that lighttpd didn't find the 

The entries for info2www and man2html are in the directory /usr/lib/cgi-bin, per the placeholder page:

[paul@paul-desktop log]$ ls -l /usr/lib/cgi-bin/
total 40
-rwxr-xr-x 1 root root 35318 2005-04-14 12:15 info2www
drwxr-xr-x 2 root root  4096 2008-05-09 15:22 man
[paul@paul-desktop log]$ ls -l /usr/lib/cgi-bin/man/
total 76
-rwxr-xr-x 1 root root 20848 2007-10-28 13:20 man2html
-rwxr-xr-x 1 root root  8250 2007-10-28 13:20 mansearch
-rwxr-xr-x 2 root root 18096 2007-10-28 13:20 mansec
-rwxr-xr-x 2 root root 18096 2007-10-28 13:20 manwhatis

Any other suggestions?

---

### Post by agharbeia on 2008-09-17
I'm having the same problem with a Perl CGI.

---

### Post by azulmarino on 2008-11-10
I've found in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/lighttpd/+bug/292347") that the trick to make cgi work is to comment out the second line from:

/etc/lighttpd/conf-available/10-cgi.conf

That's the line starting with "alias.url".

Then restart the server and now the script should work.

---

