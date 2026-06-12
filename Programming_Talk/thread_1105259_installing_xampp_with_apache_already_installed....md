---
title: "installing xampp with apache already installed..."
date: 2009-03-24
forum: Programming Talk
---

### Post by qmqmqm on 2009-03-24
I already have Apache on a remote Solaris box before installing xampp. After installing xampp, when I type in the ip address in the web browser address bar again I get the same page as before, and I do not seem to get the default yellow-themed xampp homepage.

So I attempted to stop the existing Apache:

doing "apachectl stop" did not work.

And I tried to kill -9 the processes, it says "not owner":
#ps -ef | grep pache
webservd 8346 1 0 17:38:09 ? 0:00 /usr/apache2/bin/httpd -k start
webservd 8349 1 0 17:38:09 ? 0:00 /usr/apache2/bin/httpd -k start
webservd 8348 1 0 17:38:09 ? 0:00 /usr/apache2/bin/httpd -k start
root 8548 28940 0 17:42:02 pts/1 0:00 grep pache
webservd 8351 1 0 17:38:16 ? 0:00 /usr/apache2/bin/httpd -k start
webservd 8350 1 0 17:38:09 ? 0:00 /usr/apache2/bin/httpd -k start
webservd 8347 1 0 17:38:09 ? 0:00 /usr/apache2/bin/httpd -k start

Any ideas how I can get rid of the running apaches? Or is xampp albe to use the existing apache?

Ultimately my goal is to put a web application inside of xampp and being able to navigate to the web application using a web browser.

Any advise is greatly appreciated!

Tom

---

### Post by Anthon on 2009-03-24
I replied to something similar on a different thread not 10 minutes ago:

sudo /etc/init.d/apache2 stop

should do the trick

---

### Post by qmqmqm on 2009-03-24
Hi Anthon

Unfortunately that did not work:

#./etc/init.d/apache stop

Tha did not stop the apache...

Any ideas?

---

### Post by cabalas on 2009-03-24
> **qmqmqm said:**
> #./etc/init.d/apache stop

Hey, 

Just checking but did you try the command without the '.' at the start of the path. You don't need the dot like you have above because it is an absolute path.

---

### Post by qmqmqm on 2009-03-24
It did not work either...

Looks like the apache would restart itself as soon as I stopped it...

---

### Post by qmqmqm on 2009-03-24
I was able to use pkgrm to remove some of the apache-related packages and bring the web server down.

However when I tried to remove the last apache-related package, I get the following error:

svc:/network/http:apache2 remains enabled; aborting
pkgrm: ERROR: class action script did not complete successfully

Removal of <SUNWapch2r> failed.

I did kill all the processes related to apache using "kill -9 ...".
Does anyone know how to remove this package?

---

### Post by slavik on 2009-03-25
pkgrm? Removal of <SUNWapch2r> failed.?

Are you running Solaris per chance?

It would be best to find how apache is setup under Solaris, since there could be some other script that is starting it and such.

---

