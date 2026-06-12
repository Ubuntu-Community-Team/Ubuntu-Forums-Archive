---
title: "Cross-Subdomain Sessions [PHP]"
date: 2007-12-16
forum: Programming Talk
---

### Post by 71fnRVVm on 2007-12-16
Anyone know how to successfully create cross-subdomain sessions?

I've tried setting the parameters as stated in the PHP.net docs,but have had no success.

For example, a user logins through "sub1.domain.com" but may click over to "domain.com" for certain things, and I want to be able to see these sessions across subdomains.

Further, I have a dev area setup that looks like "dev.domain.com/sub1" and I don't want to have to play with session creation depending on whether or not it's the dev env.

Thanks in advance!

--Kyle

---

### Post by pmasiar on 2007-12-16
I am not sure what you want to accomplish, maybe you need to rethink why you need it?

By definition, session is stored on the server, so other server does not have info about it, and would need to query first server for session-related info (from client provided session ID).

Maybe by URL rewriting you can consolidate all relevant domains into common URLs, and process them on same server?

Edit: I missed it is cross **subdomain**. duh!

---

### Post by 71fnRVVm on 2007-12-16
Well the point is very simple.  If someone's logged in, I don't want a "login" button to appear on the top-level domain.  That's pretty stupid, I would think.

From what I've read, you can set session parameters using sessions_set_cookie_params();... but I've had no luck with it.

URL rewriting is not really something I want to delve into, especially since I've created a whole system on this subdomain structure.

Thanks

--Kyle

---

### Post by tomchuk on 2007-12-17
```

ini_set('session.cookie_domain', '.example.com')

```
Note the '.' before the domain - that will set the cookie for example.com and all its subdomains.

You can set session.cookie_domain in your app using the above or set it in your php.ini.

---

### Post by aks44 on 2007-12-17
In addition to tomchuk's post, you have to know whether your subdomains are running on the same host or on different hosts.

PHP's default session management is based on files, which makes your sessions data local to a specific host. If your various subdomains run on different hosts you'll have to use a database-based session manager so that your session data is stored centrally.

Beware: DB-based sessions are tricky to implement. See [this article]("http://www.mysqlperformanceblog.com/2007/03/27/php-sessions-files-vs-database-based/") which explains the main issue (in the CGIs I'm working on I chose to implement it using InnoDB / FOR UPDATE, for various practical reasons but YMMV).

---

