---
title: "LAMP and blank Pages"
date: 2008-03-21
forum: Programming Talk
---

### Post by RRosset on 2008-03-21
Hey mates! I searched the forum looking for an answer with no luck at all. My problem is that i installed apache + mysql with no problem. I'm able to run a PHP page and to access MySQL through MySQL Query Browser. But i'm not able to access MySQL through my PHP scripts. I only get a blank page. I read in CI (codeigniter.com) that in windows they install a few dll, my question is, should i install something else in my ubuntu in order to use both mysql and php5 without blank page? I'm a web developer and I really need this in order to develope locally and not in a remote server.

Thanks in advance mates!

Bob

---

### Post by LaRoza on 2008-03-21
How did you install?

If you installed the recommended way:

```

sudo tasksel

```

(Select "LAMP" do not unselect anything!)

It should work fine.

You can try installing:

```

sudo aptitude install php5-mysql

```

For the library. Not a DLL, as that is Windows specific, but similiar concept.

---

### Post by Can+~ on 2008-03-21
-Does it happen with any php file, even if it doesn't access a database, like a php with echo "Hello world"?
-Is the mysql-server running, and with anything in there? A database with a random table with content?
-Did you create a user with access to that database?
-Are you echoing the results after you do the query?
-*edited out LaRoza had an easier solution.*

It would be simpler if you post the php code.

---

### Post by RRosset on 2008-03-21
hueheuehu forget to install the client :P

My bad, thanks mates! you rock!

---

### Post by t3s7a on 2011-05-21
I also had my php files showing me a blank page, but the only thing that worked for my Ubunto 11.04 was:

```
sudo apt-get install php5 libapache2-mod-php5
```

---

