---
title: "postfix main.cf problem"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by little ron on 2011-11-17
Hi,
I am learning to program by writing an application that in one of it's functions needs to send emails to people at certain times.

I'm a beginner on a stand alone machine running ubuntu 11.10 with an email account at yahoo.com.

Developing the application first in bash then perl and then in c++, for the command line and then hopefully as a gui application - everything is going ok until I tried to program the email feature.

As the first program is in bash I need to have an email client that can run from the command line so I installed "mutt" and then found out that you need an email server as ubunto does not have one so I installed postfix - now when ever I try to do anything with mutt I get the following fatal error :-

sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

I have checked the /etc/postfix directory and it contains the master.cf file but not the main.cf

I did a search and found main.cf in 
./usr/lib/postfix/main.cf

I have removed and installed postfix a number of times and it always seems to install main.cf in the wrong place.

All the tutorials and help guides seem to assume main.cf is in /etc/postfix before they start to offer assistance.

Also I use Evolution for my day to day stuff, will doing the above cause any problems with Evolution.

Loving all this Unix/programming under the hood stuff.

Anyone help please

Thanks 
little ron

---

