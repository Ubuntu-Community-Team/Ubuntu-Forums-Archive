---
title: "Need Help on knowledgeroot"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-14
Hi guys,

i just installed knowledgeroot and i don't know where it install it. I am trying to make a Knowledge Base that why i wanna try knowledgeroot but after install i don't know where to start the program

can anyone help me please? sorry for a dumb question. still getting use to ubuntu

---

### Post by Cypher on 2008-05-14
Did you install it with "apt", if so..you can list the contents of the package with
```

dpkg -L knowledgeroot

```

---

### Post by Mikel12 on 2008-08-21
Kind of old thread but i'll answer anyway.

You configure knowledgeroot through your browser, point it at
[http://localhost/knowledgeroot/install.php]("http://localhost/knowledgeroot/install.php")

And follow the instructions.

---

### Post by LostAndFound on 2009-06-15
Hi 

I just installed Knowledgeroot on Jaunty, and I'm also trying to figure out how to get it going.

I found out where it was installed

$locate knowledgeroot | grep install.php
shows:
/usr/share/knowledgeroot/install.php

So I guess I have to copy this folder to /var/www/ 
--or is there a good reason why it's in /usr/share?

There is no readme.

---

### Post by Celauran on 2009-06-15
> **LostAndFound said:**
> 
I found out where it was installed

$locate knowledgeroot | grep install.php
shows:
/usr/share/knowledgeroot/install.php

So I guess I have to copy this folder to /var/www/ 
--or is there a good reason why it's in /usr/share?

There is no readme.

Have you tried [http://localhost/knowledgeroot/install.php](http://localhost/knowledgeroot/install.php) as suggested above? /knowledgeroot/ is likely aliased in Apache.

---

### Post by iansane on 2009-07-12
I'm playing with knowlegeroot because my company has no documentation on how to do anything so I'm looking for ways to get things organized. Apparently even though the knowlegebase install installs Apache2 it doesn't set up the alias because [http://localhost/knowlegeroot/install.php](http://localhost/knowlegeroot/install.php) gives a page not found error. The files do exist in /usr/share/knowlegebase though.

I'm going to install webmin because I still haven't learned to manually edit the conf files

---

### Post by iansane on 2009-07-12
OK Webmin was no good so I learned how to add the line

```

Alias /knowledgeroot/ /usr/share/knowledgeroot/

```

to the /etc/apache2/apache2.conf file
by

```

sudo gedit /etc/apache2/apache2.conf

```

and then restart the server.

```

sudo /etc/init.d/apache2 restart

```

Got that from another post on ubuntu forums. Don't remember which one.
It was much easier than figuring out webmin with no howto or good documentation to be found.

Now the install.php is giving error  "Fatal error: Class 'db' not found in /usr/share/knowledgeroot/include/init.php on line 101"

Here's lines 100 and 101 from the init.php file if anyone can tell me how to fix this.
```

100 // init databaseclass
101 $CLASS['db'] = new db();

```

Thanks

---

