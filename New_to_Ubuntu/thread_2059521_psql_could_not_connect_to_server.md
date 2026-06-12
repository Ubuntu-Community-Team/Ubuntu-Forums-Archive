---
title: "psql: could not connect to server"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by eli1028 on 2012-09-18
Under the postgres user, I tried **psql** command and I'm getting this error

**psql: could not connect to server: No such file or directory Is the server running locally and accepting connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?**

But when I'm trying this command **/usr/local/pgsql/bin/psql** , it is working.

Anything wrong with my configuration?
Btw, I'm using postgresql-9.2

---

### Post by spjackson on 2012-09-18
It sounds like you have two Postgresql installations, probably one from the Ubuntu repository /usr/bin/psql, which is not running, and the other in /usr/local/pgsql/bin/psql installed via some other means, which is running.

There are a number of options, but what I'd probably do is
```

PATH=/usr/local/pgsql/bin:$PATH

```And to make it permanent, add it to ~/.bashrc

---

### Post by eli1028 on 2012-09-20
> **spjackson said:**
> It sounds like you have two Postgresql installations, probably one from the Ubuntu repository /usr/bin/psql, which is not running, and the other in /usr/local/pgsql/bin/psql installed via some other means, which is running.

There are a number of options, but what I'd probably do is
```

PATH=/usr/local/pgsql/bin:$PATH

```And to make it permanent, add it to ~/.bashrc
I checked /usr/bin/psql, it exists. Is there any way I can remove this? I installed postgresql version 8 before. I guess, I missed some cleaning there.

---

### Post by spjackson on 2012-09-20
> **eli1028 said:**
> I checked /usr/bin/psql, it exists. Is there any way I can remove this? I installed postgresql version 8 before. I guess, I missed some cleaning there.
If you set the PATH as I indicated previously, it should work. Does it?

If, in addition, you want to clean up /usr/bin/psql then
```
/usr/bin/psql --version
```should tell you what version it is. synaptic should be able to remove that version. I'd advise you to be sure that you have a secure backup of your databases before attempting to remove the old version.

---

