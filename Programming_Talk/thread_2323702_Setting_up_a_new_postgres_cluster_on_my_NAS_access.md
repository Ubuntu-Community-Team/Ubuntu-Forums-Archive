---
title: "Setting up a new postgres cluster on my NAS accessed soft link to laptop"
date: 2016-05-07
forum: Programming Talk
---

### Post by simonwatsonsjw on 2016-05-07
Hi All,

I have a ThinkPad T530 with Ubuntu 16.04. I also have a QNAP TS469L NAS.

I have connected to the NAS using ISCSI where I have an ext 4 partition. There are other files on that partition but I am trying to set up a new postgres 9.5 database cluster on there to store a large amount of data. However, I suspect this issue relates to the use of soft links and issues with file ownership rather than issues relating to the NAS and ISCSI connection.

Using the below code results in a cluster I can log into if I carry it out where all the files are on my laptop. 
```

sudo pg_createcluster 9.5 dbReddit --user=postgres --datadir=/dbNAS/dbPstgres/data
sudo systemctl daemon-reload
systemctl start postgresql@9.5-dbReddit.service

```

However, If I substitute the file dbPostgres for a soft link (ln -s) pointing to a file dbPostgres on my NAS, I get the following error:

```

Creating new cluster 9.5/dbReddit ...
  config /etc/postgresql/9.5/dbReddit
  data   /dbNAS/dbPostgres/data
  locale en_AU.UTF-8
initdb: could not access directory "/dbNAS/dbPostgres/data": Permission denied
Error: initdb failed

```

I have ensured that all files are owned by postgres and belong to the postgres group. 

Could you advise how I get the cluster set up on my nas? The purpose for this is to allow me to use the information storage on my NAS but still use my local processor to run the queries. If I set up a postgres database server on my nas, the version supplied by QNAP is older and I would have to rely on quite low CPU specifications.

Thanks and regards,

Simon

---

### Post by simonwatsonsjw on 2016-05-07
Hi All,
Figured this out - postgres can tell the mount is over a soft link and doesn't like it. My solution was to create a mount --bind to the nas instead:
```

sudo mount --bind /media/simon/b434sb43234bb3432/dbPostgres/ /dbNAS

```

After this

```
sudo pg_createcluster 9.5 dbReddit --user=postgres --datadir=/dbNAS/postgres/9.5/data
```

worked fine. Now setting up as usual.

Simon

---

