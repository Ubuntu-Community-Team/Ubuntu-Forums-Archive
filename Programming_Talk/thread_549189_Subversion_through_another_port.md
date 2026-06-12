---
title: "Subversion through another port"
date: 2007-09-12
forum: Programming Talk
---

### Post by Masterslave on 2007-09-12
Hello all,

Yesterday I've installed Subversion on Dapper.
My roommate also use subversion and he uses port 3690 for this (default Subversion port).
So I wanted to use port 3691. (because people have to connect to the repository at there home).
But when I start RapidSVN and want to switch the URL, I get the following error.

```

Execute: Switch URL
Error: Error while performing action: Can't connect to host 'wortel': Connection refused
Ready

```
URL I had:
svn://wortel/testrepo

URL I've enter and triggers the error above:
svn://wortel:3691/testrepo

My /etc/xinetd.d/svnserve looks like this:
```

service svn
{
       port = 3691
       socket_type = stream
       protocol = tcp
       wait = no
       user = svn
       server = /usr/bin/svnserve
       server_args = -i -r /var/svn
}

```
Anyone an idea to fix this?

Thanks in advance

---

### Post by ansi on 2007-09-12
> **Masterslave said:**
> 
But when I start RapidSVN and want to switch the URL, I get the following error.

Anyone an idea to fix this?


To find out what works not properly could you please test access to the repository via CLI, like: ``*svn ls svn://wortel:3691/testrepo*'' from your terminal? It might turn out that just RapidSVN works wrong (I wouldn't affirm this thesis because of I'm user of CLI, but everything is possible as well ;); this functionality hasn't been implemented yet, for example).

And some banal questions: Have you restarted your xinetd after changes in config? Will it be working if ``*svnserve*'' is started from CLI (``*/usr/bin/svnserve --listen-host=wortel -r /var/svn -d*'', for example)?


Regards,

---

### Post by Masterslave on 2007-09-13
It's working now, but it is running still on port 3690.
I've mounted my repos directory on the repos directory of my roommate, and it's working know.
I've set the premissions to 0777...

---

