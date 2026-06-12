---
title: "Apache2 domain name redirect"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by pslStu on 2008-11-25
Greetings

Apologies if this is repeated elsewhere, I couldn't seem to find exactly what I was after.

What I would like to do is redirect a specific incoming domain name on to another domain name, while keeping the original in the address bar.
So, a user types in [www.domain1.com](www.domain1.com), which points to my server, and I want it to automatically redirect to [www.domain2.com](www.domain2.com), but still show [www.domain1.com](www.domain1.com) in the address bar.
(it seems most domain name providers have this feature in a nice little package waiting to be used, but not the one I'm with, and changing it isn't an option)

I'm using individual Virtual Host files in /etc/apache2/sites-available as it's a multi-domain server, indentifying by name.

I found ```
Redirect / http://www.domaintobeforwardedto.com/
``` on a website, which does redirect if I place it within the <VirtualHost> tag of the virtual host file, but it changes the URL in the address bar.

I should also add that this is a temporary measure, as it doesn't seem best practice, but unfortunately it's required.

Can anyone help me out?

---

### Post by saru411 on 2008-11-25
You might get faster/better help from the Server or Networking subforums.

---

### Post by Titan8990 on 2008-11-25
The easiest way to do this is just to setup a CNAME record for the domain that needs to get redirected and point it to the A record of the domain you are redirecting to.


[http://en.wikipedia.org/wiki/List_of_DNS_record_types](http://en.wikipedia.org/wiki/List_of_DNS_record_types)


With a web server the only types of records you will need to deal with are CNAME, A, and possibly NS.

---

