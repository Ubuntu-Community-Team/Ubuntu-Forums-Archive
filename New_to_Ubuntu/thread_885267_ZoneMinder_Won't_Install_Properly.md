---
title: "ZoneMinder Won't Install Properly"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by crjackson on 2008-08-09
Okay, so I'm trying to set up a home security system and the only software available seems to be ZoneMinder.  So I try to install from the repositories and I get the errors indicated in the screen shots listed below.

I have removed and purged everything associated with ZoneMinder and then tried to reinstall.  I still get the error.  I think it may have something to do with MySql because when I was installing the first time, I got in a hurry and clicked the next button instead of entering a password (i.e. I left it blank to configure later).  I'm not sure if that is the problem or not, but I'd like to solve this so that I can test and ultimately build a dedicated tower for monitoring surveillance cameras and playing back as needed.

Please assist in fixing this error so that I can test ZoneMider.  There are plenty of quality applications for doing this in windows xp, but since I'm committed to Ubuntu, I want to avoid MS if possible.

Thanks for your assistance...

---

### Post by crjackson on 2008-08-10
Okay, it seems that synaptic is broke.  I'm getitng the above errors on EVERYTHING I try to install.  Please help.

---

### Post by chrisod on 2008-08-10
Is there a forum or support group for Zoneminder somewhere? Absolute Beginner's might not be the best place to ask for help on a specialized, somewhat obscure application because odds are few if any of us use it.

---

### Post by sidrit on 2008-08-10
Strange. i had no problems setting it up.
hers's a mini-howto i wrote after:

[http://sidrit.wordpress.com/2008/08/04/video-surveillance-system-on-ubuntu-804-with-zoneminder/]("http://sidrit.wordpress.com/2008/08/04/video-surveillance-system-on-ubuntu-804-with-zoneminder/")

Hope it helps.

---

### Post by crjackson on 2008-08-12
> **sidrit said:**
> Strange. i had no problems setting it up.
hers's a mini-howto i wrote after:

[http://sidrit.wordpress.com/2008/08/04/video-surveillance-system-on-ubuntu-804-with-zoneminder/]("http://sidrit.wordpress.com/2008/08/04/video-surveillance-system-on-ubuntu-804-with-zoneminder/")

Hope it helps.

Thanks, I'll give this a shot.

---

### Post by TVTrukChik on 2008-10-19
There are support forums at [www.zoneminder.com]("http://www.zoneminder.com")

I had the same error you list above, and found the answer here by doing a search on the zoneminder forums:
[http://www.zoneminder.com/forums/viewtopic.php?t=10954&highlight=insecure]("http://www.zoneminder.com/forums/viewtopic.php?t=10954&highlight=insecure")

And look here (scroll down to "Installation from a .deb") for a tutorial:
[http://www.zoneminder.com/wiki/index.php/Documentation#Tutorial]("http://www.zoneminder.com/wiki/index.php/Documentation#Tutorial")

Haven't quite gotten it going yet, but I think I'm close.

---

### Post by crjackson on 2008-10-21
> **TVTrukChik said:**
> There are support forums at [www.zoneminder.com]("http://www.zoneminder.com")

I had the same error you list above, and found the answer here by doing a search on the zoneminder forums:
[http://www.zoneminder.com/forums/viewtopic.php?t=10954&highlight=insecure]("http://www.zoneminder.com/forums/viewtopic.php?t=10954&highlight=insecure")

And look here (scroll down to "Installation from a .deb") for a tutorial:
[http://www.zoneminder.com/wiki/index.php/Documentation#Tutorial]("http://www.zoneminder.com/wiki/index.php/Documentation#Tutorial")

Haven't quite gotten it going yet, but I think I'm close.

Okay, thanks. I'll give it another shot.

---

### Post by lapichiflati on 2008-10-21
I ran into this same problem, this is what I did to create the database that will work with package.

Assuming you have created a root user with a password for your mysql server
```

mysql -u root -p zm < /usr/share/zoneminder/zm_create.sql
mysql -u root -p zm
grant select,insert,update,delete on zm.* to 'zmuser'@localhost identified by 'zmpass';
quit
mysqladmin -u root -p reload

```

After this
```

sudo apt-get install zoneminder

```

And it should install correctly

---

