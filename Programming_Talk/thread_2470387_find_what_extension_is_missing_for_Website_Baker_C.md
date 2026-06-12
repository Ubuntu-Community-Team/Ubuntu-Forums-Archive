---
title: "find what extension is missing for Website Baker CMS"
date: 2021-12-28
forum: Programming Talk
---

### Post by cazz on 2021-12-28
Hi
I have upload a CMS system to my Ubuntu server that run Apache2 (I also have another server that run Nginx)
I wonder if that is possible to find in a log or somewhere what kind of extension the CMS need.

---

### Post by spjackson on 2021-12-29
The starting point would be the pre-requisite list from the documentation for the CMS.

For Apache, try /var/log/apache2/error.log first. For nginx, maybe /var/log/nginx/error.log.

---

### Post by TheFu on 2021-12-29
Why not check the CMS documentation?  There isn't 1 all-used file format for every CMS.  Each will work with different files. They are unique.  If the actual CMS were put into the thread title, then perhaps someone familiar with that CMS would respond?

Or is this software a secret-squirrel operation? When secrecy is important, I can understand not posting any details.

---

### Post by cazz on 2021-12-30
Hi and thanks for the replay
I have ask in the forum and only info that can give me is very basic, version of PHP and MySQL and space, not so much more.
I have look and I have not find any more info.
I also look into other CMS system but I do like this one alot.

Is not so big CMS system, Website Baker.

But I going to try a little more :)

---

### Post by schragge on 2021-12-30
> **cazz said:**
> Is not so big CMS system, Website Baker
Older versions (<2.10.0) seem to be pretty well documented. See e.g. [Before installation]("https://help.websitebaker.org/en/userguide/installation/prior-to-installation.php").

For newer versions they suggest using wiki, but the English part is half-empty. The German part is OK though. See e.g. [Systemvoraussetzungen]("http://wiki.websitebaker.org/doku.php/install/start#systemvoraussetzungen").

---

### Post by mIk3_08 on 2021-12-30
> **cazz said:**
> Hi and thanks for the replay
I have ask in the forum and only info that can give me is very basic, version of PHP and MySQL and space, not so much more.
I have look and I have not find any more info.
I also look into other CMS system but I do like this one alot.
Is not so big CMS system, Website Baker.
But I going to try a little more :)
I am very confused.
> **cazz said:**
> 
I also look into other CMS system but I do like this one alot.

What cms you talking about? can you specify the cms you used. Thanks and Advanced Happy New Year.

---

### Post by CharlesA on 2021-12-30
> **mIk3_08 said:**
> What cms you talking about? can you specify the cms you used. Thanks and Advanced Happy New Year.

They mentioned it further up in the thread: Website Baker.

@OP: I have edited the title of the thread to mention the CMS you are trying to get working. You didn't mention which specific errors you were getting, so it is nothing but guess work.

The links that  schragge provided may help, however.

---

### Post by cazz on 2021-12-30
wow thanks
that wiki did tell me what to install and now it works :)

---

### Post by cazz on 2021-12-30
One more question :)
I have got it to work in my lab server.
I trying now at a friends server and he have same settings that I have (Ubuntu server with latest version of PHP 7.4 and MySQL 8.0.27)
I have also check both "php -m" and "apachectl -M" and it is same.

Is that some more settings I can look at,  right permission is ok in both lab and his server also config file for virtual host

---

