---
title: "Javascript security question"
date: 2009-11-12
forum: Programming Talk
---

### Post by tc101 on 2009-11-12
I am working on a company website.  An employee has to enter a login and password to get into the site.  We want to write code in javascript that would upload a file to an FTP server.  In order to do this, we have to enter the password to the FTP sever in javascript.  An angry employee could do a "view source", see the password, get on the FTP server and do serious damage.

The employees using the site are data entry type people, not serious hackers.  I need some way to hide the password that will be in the javascript code so an employee doing a casual "view source" can't see.  How would you do this?

---

### Post by korvirlol on 2009-11-12
you could "md5" the password that the user enters and compare it to an MD5's correct password. 

That way they cant see what the actual password is, and md5 is computationally unfeasible(is that a word?) to decrypt....

seems like you should rethink your framework though, using javascript to do this will never be the best way.

---

### Post by tc101 on 2009-11-12
> seems like you should rethink your framework though, using javascript to do this will never be the best way. 

We have some third party software that is all done in javascript.  It uses a third party activeX control.  It would be a big job to do this in anything other than javascript.

---

### Post by Reiger on 2009-11-12
This is not going to work that easily, or at least from what I see it is a chicken and egg problem: an MD5 (which is not deemed secure anymore) of a password does not map to the password, and certainly not in the FTP world where passwords are taken &#8216;as is&#8217; i.e. plain text. (Which is why FTP is disallowed in many &#8216;secure&#8217; environments, along with other such plain text protocols as Telnet). 

Of course it is possible to use a HTTP server as intermediary: establish a session with the website, upload a file anonymously to the site and have the site take on the responsibility of forwarding the upload to the correct FTP address. On the downside that pretty much cuts out your neat 3rd party software you were using...

EDIT: Of course if you think nobody with skills is going to use that site anyway you can still go the obfuscation route. Mostly for the fuzzy feeling, not for the actual benefits.

---

### Post by myrtle1908 on 2009-11-12
Any reason why you can't make your web users also ftp users?  This way you can re-use their credentials when uploading to the ftp server.  Security-table synchronization can be a pain however.

If not, Reiger's suggestion of uploading to the web server and having it take care of the FTP is the way to go.  What web server are you dealing with, languages etc?  Uploading a file to FTP is trivial in perl, php, java etc.

---

