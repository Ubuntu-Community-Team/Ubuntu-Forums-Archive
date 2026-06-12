---
title: "How to password-protect server-status output in my browser?"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by Ulf_Dunkel on 2014-06-06
I run a Ubuntu 14.04 VM with Apache 2.4 on a server farm and would like to use the well-known [http://my.domain/server-status](http://my.domain/server-status) page, but without others being able to see this page, too.

In my /etc/apache2/mods-available/status.conf, I have set this section:
```
<IfModule mod_status.c>
        <Location /someRandomCrapCharacters/server-status>
                SetHandler server-status
        </Location>

        # Keep track of extended status information for each request
        ExtendedStatus On

        # Determine if mod_status displays the first 63 characters of a request or
        # the last 63, assuming the request itself is greater than 63 chars.
        # Default: Off
        #SeeRequestTail On

        <IfModule mod_proxy.c>
                # Show Proxy LoadBalancer status in mod_status
                ProxyStatus On
        </IfModule>
</IfModule>
```

The module is enabled in Apache2.4.

So when I call the URL [http://my.domain/someRandomCrapCharacters/server-status](http://my.domain/someRandomCrapCharacters/server-status), I see the Server Status page. But others could, too, if they'd know or find the URL. This is what I would like to avoid.

What should I do best to get rid of the silly workaround with the /someRandomCrapCharacters/ folder name, but instead have to enter a password at least once to qualify for being allowed to see the Server Status page?

---

