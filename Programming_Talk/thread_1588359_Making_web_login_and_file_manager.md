---
title: "Making web login and file manager"
date: 2010-10-04
forum: Programming Talk
---

### Post by jakupl on 2010-10-04
Hello peops. I play in a fairly well known string quartet, and as our reputation grows and workload increases we need better ways to be organized.
We have been using the living heck out of dropbox, but beeing a string quartet, we need a huge lot of space for video and audio recording of ourselves.

I feel like geeking out, so I have obtained a static ip address, a domain name and I will get myself a server running ubuntu server edition. My plan is to slap on a webpage for the quartet.. It might be overkill, but I have always wanted a server like this for a bunch of other handy stuff anyways.

So my problem is:

I want a portion of the webpage to be password protected. I won't need usernames and different passwords. We are only 4 people, so one universal password will probably be sufficient (am I wrong here?)

We will need a file manager on site, and the ability to easily upload large files. 
And I have NO IDEA how to do any of this.

I am a little bit experienced in basic HTML, Python and Bash. But I have never touched PHP, CSS, MySQL or all the other stuff. So this is going to be interesting.

I would be very grateful if I could be pointed in the right direction.
Thanks for you help.

---

### Post by juancarlospaco on 2010-10-04
Install[** AjaXplorer**]("http://www.ajaxplorer.info/"), is all you want already working and tested...

:)

---

### Post by jakupl on 2010-10-04
> **juancarlospaco said:**
> Install[** AjaXplorer**]("http://www.ajaxplorer.info/"), is all you want already working and tested...

:)

Thanks.

Would it be possible to use AjaXplorer in </iframe> tag
That would be nice, because the webpage will contain loads of other stuff as well.

EDIT: AjaXplorer sure is looking D*** nice. Thanks a bunch.

---

### Post by jakupl on 2010-10-04
Nevermind. I can make it open up in a new window. Thankyou for your help.

however, AjaXplorer isn't the only thing I would like to password protect. So I still need a way to hide webpages behind a password.

---

### Post by spjackson on 2010-10-05
> **jakupl said:**
> Nevermind. I can make it open up in a new window. Thankyou for your help.

however, AjaXplorer isn't the only thing I would like to password protect. So I still need a way to hide webpages behind a password.

It sounds like you should look at htaccess and htpasswd.
[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)
[http://httpd.apache.org/docs/2.0/programs/htpasswd.html](http://httpd.apache.org/docs/2.0/programs/htpasswd.html)

Alternatively, there are full-featured content management systems (Drupal, Mambo, Joomla! etc.)

---

