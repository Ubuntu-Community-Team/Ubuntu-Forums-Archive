---
title: "Setting up postgis for postgresql"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by mlemily on 2008-07-30
Hi all,

Maybe beginner talk is not the best place for this, but as a gui girl, I feel like a beginner at the command line -

I'm trying to setup postgresql on my machine, enabled with postgis

Following the directions on this page:
[http://ubuntuforums.org/showthread.php?t=529238&highlight=postgis](http://ubuntuforums.org/showthread.php?t=529238&highlight=postgis)

Specifically:

"Step Three: More Configuration

There are a few things you'll have to do to get POSTGIS to "spatially enable" your database.

First, you set up the postgis libs:

createlang plpgsql mydb"


I find that

sudo su postgres createlang plpgsql template_postgis

returns the following:

/usr/bin/createlang: line 8: use: command not found
/usr/bin/createlang: line 10: use: command not found
/usr/bin/createlang: line 11: use: command not found
/usr/bin/createlang: createlang: line 13: syntax error near unexpected token `$version,'
/usr/bin/createlang: createlang: line 13: `my ($version, $cluster, $db, $port, $host);'

My question is, am I missing stuff I need from my install of createlang?

Thanks for all your help!
Emily

---

### Post by caljohnsmith on 2008-07-30
I looked at those directions, and they refer to the packages "postgresql-8.1-postgis" and "postgresql-8.1" which appear to be out-of-date; there are two newer packages in the repositories:
```
postgresql-8.3
postgresql-8.3-postgis
```
Did you install either of those instead by chance?
> **mlemily said:**
> 
sudo su postgres createlang plpgsql template_postgis

I'm not clear where you got the above command, because if I'm understanding the directions correctly, they say:
```
createlang plpgsql mydb
```
Which may need to be run as root with sudo, I don't know, as I'm not familiar with the program you're trying to install. And for the next commands it gives:
```
sudo -u postgres psql -d mydb -f usr/share/postgresql-8.1-postgis/lwpostgis.sql
sudo -u postgres psql -d mydb -f usr/share/postgresql-8.1-postgis/spatial_ref_sys.sql
```
Probably all you have to do for those commands to work is replace the 8.1 with 8.3 if you successfully installed the packages above.

Anyway, I hope that helps to get you started, but post back if you need more help. :)

---

### Post by mlemily on 2008-08-05
Thanks for your reply!

I'm back to this task after a long weekend.

I did indeed install both:

postgresql-8.3
postgresql-8.3-postgis

In terms of

createlang plpgsql mydb

I've simply chosen to name my db "template_postgis"

and I found that running just

createlang plpgsql template_postgis

returns:

createlang: could not connect to database template_postgis: FATAL:  Ident authentication failed for user "emily"

while 

sudo su postgres createlang plpgsql template_postgis

returns the messages in my original post

Does that help one bit?

Emily

---

### Post by mlemily on 2008-08-29
Hi folks,

I found a linux user here in my hometown to help me with my issue in person and I'm all set up now.

I can't tell you what the solution was, 'cause I'm not sure what they did that made things work.

Thanks for all your help!
Emily

---

