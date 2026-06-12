---
title: "500 internal error with mod rewrite"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by duceduc on 2011-10-25
I am having issue with one of my mod rewrite url. I keep getting an internal error message when I click on the link.

The link is setup for visitors to confirm their email address. Once they click on it, their email address is added to the database. Everything seems fine running internally, except for the proper page that suppose to load up when the link is clicked. My other mod rewrite rules works fine, only this one.

If the mod rewrite is turned off, the link goes to the home page and not the page that tells the visitors their email address has been added.

My htaccess files looks like this.
> # Follow symbolic links in this directory
Options +FollowSymLinks
RewriteEngine on
RewriteRule ^(profile|news-all|contact|all-archive|rss-feed).html$ index.php?cmd=$1
RewriteRule ^index.html$ index.php
RewriteRule ^print_(.*)\.html$ index.php?cmd=print&blog=$1
RewriteRule ^friend_(.*)\.html$ index.php?cmd=tell-a-friend&blog=$1
RewriteRule ^blog/(.*)/(.*)/archive.html$ index.php?cmd=archive&month=$1&year=$2
RewriteRule ^news/(.*)/(.*).html$ index.php?cmd=news&post=$1
RewriteRule ^blog/(.*)/(.*).html$ index.php?cmd=blog&post=$1
RewriteRule ^verify-email/(.*)/index.html index.php?cmd=verify_email&code=$1 [nc]
RewriteRule ^unsubscribe-notification/(.*)/index.html index.php?cmd=unsubscribe_notification&code=$1 [nc]

The one in question is the line that includes 'verify-email...'

---

### Post by jnorthr on 2011-10-25
are your using apache2 or cherokee ?

---

### Post by duceduc on 2011-10-25
apache2.

---

### Post by duceduc on 2011-10-27
I still can't get this resolve. Anyone have an idea. I can supply link to site if needed. Thanks.

---

### Post by rg4w on 2011-10-27
Does your error log contain any details?

---

### Post by duceduc on 2011-10-27
No, I don't any errors related to this issue. I've looked in the apache2 error log and syslog. All shows nothing.

---

### Post by ashwinrao on 2011-10-27
It is obvious that the error message is due to the .htaccess codes. I would suggest that you to comment the .htaccess codes one by one to debug the exact line of .htaccess code which is causing the issue.

---

### Post by duceduc on 2011-10-28
Ok. I have enabled error log in my script and I do see an error now.

> Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.,

---

### Post by decoherence on 2011-10-28
Perhaps your mod_rewrite rule and your DirectoryIndex directive in your apache config are clashing? For some reason your redirection is being redirected (probably back to the first redirection, which in turn goes on to the next one and back again, etc) ... basically you might be going from index.html to index.php back to index.html and so on.

Just a guess. It's been a while since I touched apache.

---

### Post by duceduc on 2011-10-28
Here is more message with loglevel set to 'debug'
> [Fri Oct 28 16:09:52 2011] [debug] core.c(3069): [client 192.168.1.1] redirected from r->uri = /index.php=index.php=index.php=index.php=index.php=index.php=index.php=index.php=index.php=verify-email/2-1e5b7cfd03b2d46da75ab916ae16b/index.php,

---

