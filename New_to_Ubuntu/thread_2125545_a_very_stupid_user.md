---
title: "a very stupid user"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by thepigeonking on 2013-03-14
hi guys, im very new. I setup Ubuntu server and stupidly deleted the www directory. Is there a way to get this back? Thanks

---

### Post by dargaud on 2013-03-14
You mean /var/www ? I guess you can simply do "sudo mkdir /var/www", but it will still be empty...

---

### Post by thepigeonking on 2013-03-14
yeah I did that but its empty :(

---

### Post by prodigy_ on 2013-03-14
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by varunendra on 2013-03-14
I haven't used server, but in my desktop version, the folder contains a single html file "index.html", which contains just a test message code -
[html]<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>[/html]

So I assume it is just a place for static html pages that are to be served.

---

### Post by woxuxow on 2013-03-14
> **varunendra said:**
> I haven't used server, but in my desktop version, the folder contains a single html file "index.html", which contains just a test message code -
[html]<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>[/html]

So I assume it is just a place for static html pages that are to be served.

putting a html file is to not showing the directory`s content by browsers

---

### Post by philinux on 2013-03-14
> **thepigeonking said:**
> hi guys, im very new. I setup Ubuntu server and stupidly deleted the www directory. Is there a way to get this back? Thanks

Won't it be in the trash folder?
Depends on how you deleted it I'm guessing. I never used a server set up before.

---

