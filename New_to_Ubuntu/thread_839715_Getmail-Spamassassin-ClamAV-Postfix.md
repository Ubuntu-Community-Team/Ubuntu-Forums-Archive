---
title: "Getmail-Spamassassin-ClamAV-Postfix"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by agent-orange on 2008-06-24
I am still quite new to Linux and I am stuck and need some help.
I have installed getmail which seems to be working.  I want to incorporate Spamassassin and ClamAV but this is where I am getting my problems.  Below is my Filters from getmailrc.

Let me know if you need to see anything else.

[filter-1]
type = Filter_external
path = /usr/bin/spamc
#I have also tried
path = /usr/bin/spamassassin
arguments = ("-s 250000", )

# Drop infected messages
[filter-2]
type = filter_classifier
path = /usr/bin/clamdscan
arguments = ("--stdout", "--no-summary", "-")
exitcodes_drop = (1, )


Thanks in advance
D

---

### Post by schwascore on 2008-07-18
I don't know enough to comment specifically on your issue, but this might be of use:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

