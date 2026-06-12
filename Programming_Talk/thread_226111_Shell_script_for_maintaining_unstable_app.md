---
title: "Shell script for maintaining unstable app"
date: 2006-07-30
forum: Programming Talk
---

### Post by RasutoIbuki on 2006-07-30
Hi,

I have an application that is pretty unstable. It communicates with MySQL server and for some reason it keep losing it's connection with it. The MySQL server is fine no other apps have this problem. Is there anyway I could write a shell script so when the application issues the following error "DB Error - SQL Server Has Gone Away" it will automatically close and reopen the program?

Thanks for any help

---

### Post by adamkane on 2006-07-30
I don't have the specifics, but yes. You can right a bash script and enable it as a cron job or as a daemon.

See:
[http://72.14.203.104/search?q=cache:xMgthrXC-5wJ:wiki.theory.org/BASH%2520script%2520to%2520run%2520bittorrent%2520as%2520a%2520daemon+bash+daemon](http://72.14.203.104/search?q=cache:xMgthrXC-5wJ:wiki.theory.org/BASH%2520script%2520to%2520run%2520bittorrent%2520as%2520a%2520daemon+bash+daemon)

---

