---
title: "max file descriptors (ulimit parameter)"
date: 2017-10-17
forum: Programming Talk
---

### Post by eyasso on 2017-10-17
Hi all,

I am trying to run elasticsearch in Ubuntu in production mode. For that to happen, file descriptors should be set to 65536.
I am trying to set max file descriptors to 65536. Setting it from command line works. However, the problem is that it is not persistent.
The way to make it persistent is to add following line: "<user>  -  nofile  65536" to /etc/security/limits.conf and "session    required   pam_limits.so" to /etc/pam.d/su.
The problem is that it doesn't work.
I also found this post [HTML]http://posidev.com/blog/2009/06/04/set-ulimit-parameters-on-ubuntu/[/HTML] but it doesn't work also.
I am using Ubuntu version 17.04.

It's appreciate any help.
Thanks,

---

