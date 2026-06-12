---
title: "Sqiud is blocking access to Webmin"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Jarr0d on 2008-09-08
Hey guys,

I have set up a proxy server with a content filter. I am using Squid as the proxy, Dansguardian as the content filter. 

I have also set up Webmin so I can manage everything through my IE browser. When I have the proxy enabled I cannot get to webmin. I get the following error.

```

ERROR
The requested URL could not be retrieved

--------------------------------------------------------------------------------

While trying to retrieve the URL: 10.10.10.248:10000 

The following error was encountered: 

Access Denied. 
Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect. 
```


My problem is very similar to this post [http://ubuntuforums.org/showthread.php?t=548768](http://ubuntuforums.org/showthread.php?t=548768) but the guy never said how he solved it.

My squid.conf looks like this.

```
acl our_networks src 10.10.10.0/24
acl webmin url_regex "/etc/squid/webmin.acl"
acl webmin_port port 10000
http_access allow our_networks
http_access allow localhost
http_access allow webmin
http_access allow CONNECT webmin_port our_networks
```

This might look a bit all over the place as I have been doing some googling on it.

I know that it isn't DansGuardian blocking it but it isn't even getting to that stage.

Can someone point out where I have gorn wrong?

---

### Post by Dr Small on 2008-09-08
Yes, I have the same problem with Squid and DansGuardian. If you find a fix, I'll be using it too :)

---

### Post by Jarr0d on 2008-09-11
Anyone?

---

### Post by Jarr0d on 2008-09-12
Right I have found a fix.

In my sarg.conf I have the following rules (As stated in my first post)

```
acl our_networks src 10.10.10.0/24
acl webmin url_regex "/etc/squid/webmin.acl"
acl webmin_port port 10000
http_access allow our_networks
http_access allow localhost
http_access allow webmin
http_access allow CONNECT webmin_port our_networks
```

I than added the following line

```
http_access allow CONNECT webmin_port localhost
```

So I copied and modified the last rule so it also allowed localhost through.

restart the squid service and you should be sweet.
Worked for me :)

---

### Post by Dr Small on 2008-09-12
What am I supposed to put in /etc/squid/webmin.acl ? Because it doesn't exist, and I don't know what to put in it. (I'm no Squid expert, let alone understand the Access Control Lists! :D)

Here is what I have:
```
acl my_network src 192.168.0.0/24
http_access allow my_network
http_access allow localhost

# ALLOW WEBMIN
acl webmin url_regex "/etc/squid/webmin.acl"
acl webmin_port port 10000
http_access allow CONNECT webmin_port my_network
http_access allow CONNECT webmin_port localhost

```

And then Squid is complaining when I restart it:
```
 * Restarting Squid HTTP proxy squid                                            2008/09/12 11:21:03| strtokFile: /etc/squid/webmin.acl not found
2008/09/12 11:21:03| aclParseAclLine: WARNING: empty ACL: acl webmin url_regex "/etc/squid/webmin.acl"
                          
```

Dr Small

---

### Post by Jarr0d on 2008-09-13
Sorry mate, I forgot to add that in.
The contents of "/etc/squid/webmin.acl" should be the URL of your webmin server.

So in my "/etc/squid/webmin.acl" file I have [https://192.168.1.3:10000](https://192.168.1.3:10000)

Cheers

---

### Post by KegRaider on 2012-09-22
I know this is an OLD topic, but it is still relevant.
I used this thread to help me when I setup early in the piece, and now that I have 'upgraded' to 12.04, I needed this again, but I have a few changes ;)

Since the new version uses SQUID3, you need to adjust the configs accordingly....

The file "/etc/squid3/webmin.acl" will need to contain: 
```

[https://192.168.1.6:10000]("https://192.168.1.3:10000")  

```(*or whatever your squidserver's IP address is.)

In the "/etc/squid3/squid.conf" file you need to have:
```

acl my_network src 192.168.1.0/24 
http_access allow my_network 
http_access allow localhost 
acl webmin url_regex "/etc/squid/webmin.acl" 
acl webmin_port port 10000 
http_access allow CONNECT webmin_port my_network 
http_access allow CONNECT webmin_port localhost

```

So, once again, thanks Jarr0d this works a treat.

-KegRaider

---

