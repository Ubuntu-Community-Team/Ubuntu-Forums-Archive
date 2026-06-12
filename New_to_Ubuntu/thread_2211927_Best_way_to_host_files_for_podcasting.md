---
title: "Best way to host files for podcasting"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by wlraider70 on 2014-03-18
I'm planning to setup a podcast with iTunes. As I understand it I need my media to have a URL so that I can assign it in the feed.
Whats the best way to use my server to do that. 

I'm not looking to create a website, and If possible I only want to add new files to the directory and thereby have a URL with their file-name at the end.

---

### Post by TheFu on 2014-03-18
Is this a trick question?
If you don't want a website, don't create one. Put a redirection URL in every directory as "index.html" - or at least make it blank, so that anyone asking for a file must know the exact name.

Just create a file directory with the podcast files - .ogg, I hope.

Then use whatever tool you want to create RSS or ATOM feeds for itunes.

---

### Post by wlraider70 on 2014-03-18
> **TheFu said:**
> Put a redirection URL in every directory as "index.html" - or at least make it blank, so that anyone asking for a file must know the exact name.

I don't know what this means or how it is accomplished, thus "Absolute Beginners Section". 

I'm asking how to make files in a directory accessible/downloadable from the internet.

---

### Post by tgalati4 on 2014-03-18
I think the message here is that you really do need a website. If you don't want to manage it, then your options are limited because after a while, you will have a lot of files to manage.  You can install a content management system such as [http://drupal.org](http://drupal.org) or you can rent some hosting space and use their basic page and just upload the files.  

I'm not sure if you can use Ubuntu One to serve the files, but you could research a way to do that.  You could then link a local directory on your podcast machine and syncronize it with Ubuntu One and use that URL to serve up the files.

---

