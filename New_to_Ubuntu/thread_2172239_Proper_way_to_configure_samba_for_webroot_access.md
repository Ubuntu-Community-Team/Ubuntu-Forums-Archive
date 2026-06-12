---
title: "Proper way to configure samba for webroot access"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by David_Goodnature on 2013-09-03
I'm running two virtual servers on ubuntu 12.10 server.  mysite and mysite_test.  No problems.

Want to configure samba to allow access to /var/www/mysite_test with appropriate permissions so I don't have to jump through extra hoops whenever I want to work on files.
I'm very unfamiliar to samba.

What is the easiest way to do this?

Samba is installed and appears to be working.

Added this to smb.conf, the best I could determine from other forums.

[COLOR=#ff2600][mysite_test][/COLOR]
[COLOR=#ff2600]    comment = [/COLOR][COLOR=#ff2600]mysite[/COLOR][COLOR=#ff2600] development share[/COLOR]
[COLOR=#ff2600]    path = /var/www/[/COLOR][COLOR=#ff2600]mysite_test[/COLOR]
[COLOR=#ff2600]    browsable = yes[/COLOR]
[COLOR=#ff2600]    guest ok = yes[/COLOR]
[COLOR=#ff2600]    read only = no[/COLOR]
[COLOR=#ff2600]    create mask = 0755[/COLOR]
[COLOR=#ff2600]    force group = www-data[/COLOR]
[COLOR=#ff2600]    force user = www-data[/COLOR]


added a user with a password

restarted samba

logging in asks for credentials, but fails every time.

Does my user need to be a member of a particular group???

Any input, where should I look, etc would be appreciated.

PS - I would like to know how to do this properly so that I can use this technique on a production website in the future.


Thank you in advance!!!

---

### Post by David_Goodnature on 2013-09-04
Update -

I have now achieved the ability to connect to the share.

I can read the files in the share, but cannot write anything.

When I try to add a file to the share from my mac, I get "Finder wants to make changes.  Type your password to allow this."

I type the username and password for the share, the box shakes, but nothing happens.

Thoughts??

---

