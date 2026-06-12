---
title: "Best Way For PostgreSQL Linkage?"
date: 2007-01-06
forum: Programming Talk
---

### Post by SuperMike on 2007-01-06
I'm building a GPL PHP web app that has PostgreSQL linkage. I'm trying to decide how the installer process would work best with it. Perhaps you can share some advice on that?

I was going to make the installation process simple, smooth, and yet not annoyingly assuming of the underlying Linux distro. I was thinking of making it so that the sysop drops the web app in an Apache directory and just connect to it. Then, it detects that it was never installed and starts to show a "wizard-like" interface in the browser that describes the process of installing the database to the sysop, tweaking any other *.conf file settings, and then logging in to start administering the application with users, groups, and other parts of the application. Seems fairly straight-forward except for the best practice of the PostgreSQL linkage.

In particular in PostgreSQL, there is the '/var/lib/postgresql/*/main/pg_hba.conf' file for setting the security for the database connection as well as the way one builds the database connection. I was going to call the application 'x' and then make the username used for the db connection to be 'x' as well. I would prefer to use a tough password and go with something fairly specific rather than being wide open with:

```
host  all  all  127.0.0.1  255.255.255.255  trust
```

What would you recommend? I want the experienced sysops to appreciate that I've made the best choices and like the installer a great deal.

---

