---
title: "I hope the &quot;community&quot; could help"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by noriel on 2014-03-31
I want to set up a cache server in my ubuntu..

have you tried it?

can you give some updated links and updated tutorial that really works? 

please.. thank you

---

### Post by Lars Noodén on 2014-03-31
What do you want to cache?  If you're looking to cache HTTP, then Squid is what you are looking for.  

[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

About the only things you really need to configure for basic use are the cache size/location and the access control lists.

---

### Post by sandyd on 2014-03-31
Moved to Absolute Beginners Section

---

### Post by noriel on 2014-03-31
> **Lars Noodén said:**
> What do you want to cache?  If you're looking to cache HTTP, then Squid is what you are looking for.  

[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

About the only things you really need to configure for basic use are the cache size/location and the access control lists.

how about HTTP and HTTPS? 

Thank you.

any TIPS and TWEAKS ? to make caching better?

---

### Post by noriel on 2014-04-01
Im trying to build a cache server...

Im following this guide [http://ubuntuserverguide.com/2012/12/how-to-install-and-configure-lusca-as-proxy-server-in-ubuntu-server-12-04.html](http://ubuntuserverguide.com/2012/12/how-to-install-and-configure-lusca-as-proxy-server-in-ubuntu-server-12-04.html)  (lusca in ubuntu server 12.04)

my question is

is there any other way to do this? 
[B]
[COLOR=#ff0000]sudo nano /etc/lusca/squid.conf
[/COLOR][/B][COLOR=#111111][FONT=Droid Sans][B]
Use the following Lusca File Configuration:
[/B][/FONT][/COLOR]
#=============================================
# Port and Transparent
#=============================================
http_port 3128 transparent
server_http11 on
icp_port 0
#=============================================
# Lusca Cache Directory
  #=============================================
cache_dir aufs /cache-1/ 25000 15 256
[COLOR=#111111][FONT=Droid Sans]
I have to configure the [B]squid.conf ..

[/B]
can I edit it via "copy-paste" the code in the guide ? 


I have to edit it manually if Ill use nano right? but it has hundreds of lines..It will be too difficult for me... [/FONT][/COLOR]

---

### Post by lisati on 2014-04-01
Threads merged

---

### Post by TheFu on 2014-04-01
Welcome to the forums.   This is a "how to edit" question?

Copy/paste, scp, sftp, use a real editor that can load a file, run a comparison tool, use a config management tool like ansible, puppet, chef, rexify, salt ... there are hundreds of ways to do this.  Heck, use sed, awk, perl, python, ruby .... there are hundreds of ways.

Or is this a squid question? I'd never heard of lusca before your post.
Or is this a webcaching server question where memcache, nginx, something like that is needed?

"cache server" is extremely generic.

---

### Post by Lars Noodén on 2014-04-01
HTTPS and HTTP can be done by Squid. I would recommend looking at the basic documentation in the link above and at the Squid web site:
[http://www.squid-cache.org/Doc/config/](http://www.squid-cache.org/Doc/config/)

The directives that you need to look at first are http_port, http_access, and cache_dir.  The default configuration file has lots of options and annotations but find and focus on those first.  Make sure your cache diectories are big enough 

Then as you start to use squid, follow the access logs for a week or so and make sure it is caching and not running out of room.

I would not mess with trying to set up an intercepting proxy (formerly called transparent proxy) but instead set up a normal proxy cache and change the settings in your desktop environment or browser(s).

---

