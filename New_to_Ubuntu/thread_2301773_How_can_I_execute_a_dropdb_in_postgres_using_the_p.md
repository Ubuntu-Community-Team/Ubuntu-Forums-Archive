---
title: "How can I execute a dropdb in postgres using the postgres account without password?"
date: 2015-11-05
forum: New to Ubuntu
---

### Post by ScorpioTiger on 2015-11-05
I'm trying to drop a database in postgres using the postgres user which has no password. Every attempt has postgres prompting me for a password.

I've tried various combinations of the following;

sudo su postgres -c "/opt/alfresco-5.0.d/postgresql/bin/dropdb alfresco"
sudo su postgres -c "/opt/alfresco-5.0.d/postgresql/bin/dropdb -h localhost alfresco"
sudo -u postgres /opt/alfresco-5.0.d/postgresql/bin/dropdb -h localhost alfresco

Changing to the postgres user then;
/opt/alfresco-5.0.d/postgresql/bin/dropdb -h localhost -U postgres alfresco
/opt/alfresco-5.0.d/postgresql/bin/dropdb -U postgres alfresco

Nothing works. How on earth do I have postgres realise that this account has no password and that the user is logged in?

---

### Post by SeijiSensei on 2015-11-05
You must be talking about the password for the postgres user in Linux, right?

I only run CentOS on servers where there is also a postgres user with no password at the OS level.  From my experience there you should be able to run
```

$ sudo su
# su postgres
$ dropdb alfresco

```
Does that not work for you?

---

### Post by ScorpioTiger on 2015-11-05
No joy;

root@Alfresco-Test:/# sudo su
root@Alfresco-Test:/# su postgres
postgres@Alfresco-Test:/$ /opt/alfresco-5.0.d/postgresql/bin/dropdb alfresco
Password:
Password:
dropdb.bin: could not connect to database template1: fe_sendauth: no password supplied

I've tried absolutely everything I can think of.

---

### Post by SeijiSensei on 2015-11-05
Apparently the database itself has a password. Can you log in as user postgres with psql and issue the "DROP DATABASE alfresco" command that way?

Can you show us the contents of the pg_hba.conf file?  It's possible you are not able to connect because of restrictions in that.  Put its contents inside [noparse]```

```[/noparse] tags for legibility.  Since this is not a standard installation of PostgreSQL, I'm not sure exactly where that file might be located, but try /opt/alfresco-5.0.d/postgresql/data/ first if it exists.

---

### Post by ScorpioTiger on 2015-11-06
Thanks for the feedback.

Let me give you a better idea of what I'm trying to do;

I  have an Alfresco server. I have a cron job that calls a script that  stops the Alfresco service, TARs the Alfresco repository, indexes, etc  and does a pg_dump of the database. It all gets rsync'd to my home NAS  via SSH. This all works fine.

Where I'm running into trouble is  doing the restore. I have a fresh server that has been built using the  same process as the original in order to test the restore. I've got a  process drafted up whereby I move the backup to the new server, unzip  it; unzip the Alfresco files to the original location, then start the  postgres server, drop the Alfresco database, recreate it, then do a  restore of the backed up db.

This restore is just not working as  expected and I'm at a loss to explain why. I'm now thinking that I need  to run some kind of compare between the original server and my test  server. Any idea how I might do that?

---

### Post by SeijiSensei on 2015-11-06
I just restore by creating an empty database and running
```
psql newdb < pg_dump_file
```

Since the new database is created from the dump it is a clone of the original. I've never bothered to do any type of comparison after creating the clone. In 20 years of using PG this method has always worked reliably.

---

### Post by ScorpioTiger on 2015-11-06
Thanks for your help. Something seems to have gotten screwed up with Postgres and in the end it wouldn't even shutdown. I did a reboot of the server and now I'm able to log in to the Alfresco application and see everything restored as it should be. This has been a less than clean test of the restore and I'd prefer to have understood what was going on, but ultimately, the fact that I can see that the restore has worked correctly tells me that what I'm doing on the backup side is correct. Longer term, in the interests of scalability, I'm going to have to figure out a way to do incremental backups, but for now I have the peace of mind I was after.

Thanks again...

---

