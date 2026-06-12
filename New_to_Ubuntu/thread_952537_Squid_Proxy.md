---
title: "Squid Proxy"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by bazz on 2008-10-19
I have been looking and can not find anything to set squid up as a public proxy with user authentication. I find lots of local proxy info, but nothing I can use.

I'd like to set squid so a remote user can go to the url (where the squid server is) and he/she can enter his/her user name and password and use the proxy through https.
Is this possible? Can anyone give me a little direction on this....squid is all new to me.
Thanks!

---

### Post by Dr Small on 2008-10-19
Greetings,
Have you taken a look at this page?
[http://wiki.squid-cache.org/SquidFaq/ProxyAuthentication](http://wiki.squid-cache.org/SquidFaq/ProxyAuthentication)

I have never set it up, but now you have interested me too, so I will be attempting with you ;)

---

### Post by Gone fishing on 2008-10-19
Certainly is possible - I use webmin to configure squid and various other things on our school server. I notice that you can create an ACL (External Auth ACL) in which you can specify users. 

Obviously you can add this ACL to the squid.conf but Webmin makes things easier.

Here's a link showing how to use Webmin to configure Squid [http://swelltech.com/support/webminguide/ch12.html#sqauth](http://swelltech.com/support/webminguide/ch12.html#sqauth)

---

### Post by bazz on 2008-10-19
I know I can do all this with ssh...but I think it be cool to do a real proxy. SSH is easy...its just a matter of 
ssh -D 8080 -p 22 username@url/or IP
and configure your web browser to use localhost on 8080

However I find squid interesting....

I have read a lot of what was posted, but to be honest because its so new to me I do not understand a lot of it. I do want to learn, but really dont have the time to bang away at it hours at a time. I was kinda hoping for a "oh yeah....I'v done that". Who knows that still may happen.

So does webadmin have the ability to set something up like that?
As for the ACL (External Auth ACL) is that IP/domain/, or user based. We are obviously shooting for user here.

Thanks....hope this takes off!!

---

### Post by bazz on 2008-10-19
> **Gone fishing said:**
> Certainly is possible - I use webmin to configure squid and various other things on our school server. I notice that you can create an ACL (External Auth ACL) in which you can specify users. 

Obviously you can add this ACL to the squid.conf but Webmin makes things easier.

Here's a link showing how to use Webmin to configure Squid [http://swelltech.com/support/webminguide/ch12.html#sqauth](http://swelltech.com/support/webminguide/ch12.html#sqauth)

Thanks for the link....I noticed the wiki on the webmin page is dead, at least this give me a little idea. I just dont comprehend any of it yet...

---

### Post by Dr Small on 2008-10-19
Well, off hand, why do you need authentication with Squid? Are you connecting outside of your network or is the Squid server somewhere on your LAN?

---

### Post by bazz on 2008-10-19
> **Dr Small said:**
> Well, off hand, why do you need authentication with Squid? Are you connecting outside of your network or is the Squid server somewhere on your LAN?

The squid server would be on my network at home (possibly portfoward, or DMZ), so for example....If I'm at my office and something is blocked I could log into a web interface to access the proxy. Enter the URL and off I go.

So squid server would be on my home LAN
User would connect outside of LAN/home network.

As for the authentication...I dont want just anybody to be able to access the proxy. Only individual I give permission to.

---

### Post by Gone fishing on 2008-10-19
You can set up an ACL to allow access from certain IP addresses / ranges, would this work?

---

### Post by bazz on 2008-10-19
no unfortunately not....I have no idea where the IP would be comming from.

---

