---
title: "Php local execution only"
date: 2009-02-20
forum: Programming Talk
---

### Post by Dr Small on 2009-02-20
I am trying to think of a way to only allow local execution of a php file and disallow any remote execution. Like, I can setup a cron on the server to execute /usr/bin/php /path/to/file.php, and if anyone tries to access the file on the server from the web, it will not execute.

Perhaps I need to just use something like this?
[php]if($_SERVER[HTTP_USER_AGENT]){ die(); }[/php]

There has got to be a more fool proof way to do this. Any ideas?

---

### Post by hastur on 2009-02-20
hi,

two simple ideas :
- put it in a protected directory (e.g. with a "deny all" .htaccess file on an apache server). this should only disable http access to your script, not CLI access.
- name it script.txt - this should not stop CLI invocation and the server won't feed it to the php parser when accessed from the web. but anybody would be able to read the content of the script. that's exactly what hackers do with their f*ck#ng "r51.txt hack".

sorry if this doesn't help ;)

---

### Post by Dr Small on 2009-02-20
Both are pretty good ideas, but then I just thought of this idea before I just read your reply.
[php]if($_SERVER[REMOTE_ADDR] != "127.0.0.1"){ die(); }[/php]

And I am going to preform some tests to see if that will work as expected.

---

### Post by hastur on 2009-02-20
I'm not to sure globals variable like $_SERVER['REMOTE_ADDR'] are secure/stable (I mean, couldn't they be forged to any value by a remote attacker ? can their value be universally depended upon on any server configuration ?) - that's only a problem if security and portability are a matter for you...

---

### Post by Dr Small on 2009-02-20
I'm not sure if it can be forged or not, I have never tried, but I have found out from my testing results that local execution has no REMOTE_ADDR.

---

### Post by Dr Small on 2009-02-20
> **hastur said:**
> hi,

two simple ideas :
- put it in a protected directory (e.g. with a "deny all" .htaccess file on an apache server). this should only disable http access to your script, not CLI access.
- name it script.txt - this should not stop CLI invocation and the server won't feed it to the php parser when accessed from the web. but anybody would be able to read the content of the script. that's exactly what hackers do with their f*ck#ng "r51.txt hack".

sorry if this doesn't help ;)
Your .htaccess file is the best solution. Here's what I put in it:
```
<Files updatefeeds.php>
        deny from all
</Files>
```

The server disallows users from accessing the file, yet the php binary can execute it without a hitch. Problem solved. Thanks for your help :D

---

