---
title: "newbie with questions..."
date: 2012-03-16
forum: New to Ubuntu
---

### Post by Red Maple Leaf eh on 2012-03-16
Hello All: I am apparently our company's IT person (that should be lower case i and lower case t....) and am well enough versed in XP/W7 and MacOS, but know nothing about Linux and the various strains. The techie that we had on staff previously had put together our Webserver, which we use for a Web2Print storefront. It has run smoothly for a couple of years, without issues, but the system badly need updating. We are running Ubuntu 9.1 (Karmic) with GNOME 2.28.1 on the server and its 2 backups. It is running with Dual Core Athlon 4450e's and 2GB ram. It keeps telling me it is now unsupported and needs to update. We are running a LAMP stack website that ties to a fairly in-depth database. I know that the Apache needs to be updated as well, but what order should it be done in.... do Apache first and then Ubuntu.. or the other way around.... I don't want to screw it up, because I know I won't be able to fix it!
Does it break the code of conduct on this forum to post available freelance opportunities?
Thanks

---

### Post by dolphin194 on 2012-03-16
When you update Ubuntu, the Apache server will automatically be updated to a later version. I recommend updating Ubuntu first, since it will update Apache automatically. Then you can manually update Apache to the latest version once Ubuntu has been updated.

In addition to that, I recommend that you update to **10.04**, *not 11.10* until its end of life date. This is because 10.04 is a *Long-Term Support* release, and is much more stable than 11.10, and the end of support date for 10.04 is the same as 11.10. When you reach that End of Life date, update to 12.04. Stick to the LTS releases from then on to reduce the frequency you have to update. (Karmic is not a LTS release)

I am running Ubuntu 10.04 right now on this computer and it has worked amazingly well. I also have this ye-olde PowerEdge 2650 that *was* running 10.04 (running 11.10), and it has run amazingly well too (10.04 ran better than 11.10). I would downgrade it to 10.04 if I wasn't so lazy.
I believe it is against the code of conduct to post about freelance jobs, since it would technically be advertising.

---

### Post by Holdolin on 2012-03-16
I would definately go with 10.04.  Yep, it's a bit older, but in my server-minded thinking older=more mature/stable.  I've used it in some of my production servers with no stablity problems whatsoever.

I would reccomend though, that instead of simply upgrading, backing up your data and doing a clean install.  Unless, of course you don't yet have the knowledge of how to do backups in Ubuntu (which i highly recomend learning.)  Weather you upgrade or do a clean install, I'm confident you'll be in good shape with 10.04.  She's stable and mature, and has a lot of life left in her.

Welcome to the forums, and to the goodness that is Ubuntu :)

---

### Post by Diametric on 2012-03-16
Also check out this site as it directly relates to your question.

Good luck!

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by Bucky Ball on 2012-03-16
10.04 LTS. Supported for five years (April 2015). LTS = servers and production machines ... ;)

---

### Post by d4m1r on 2012-03-16
This is more a of sever related question, but I would stay away from updating such an old version of Apache to the latest, too many things have changed.

FYI, 12.04 (which is the next LTS version) will be released in just over a month, so I'd recommend waiting for it, do a fresh install, and install the latest Apache from scratch then (looking at your old config files).

---

### Post by dolphin194 on 2012-03-18
> **d4m1r said:**
> This is more a of sever related question, but I would stay away from updating such an old version of Apache to the latest, too many things have changed.

FYI, 12.04 (which is the next LTS version) will be released in just over a month, so I'd recommend waiting for it, do a fresh install, and install the latest Apache from scratch then (looking at your old config files).

Actually, I wouldn't do that since 12.04 will probably not be that stable, since it will be fresh.

---

### Post by anewguy on 2012-03-19
If you're relatively new to Linux and the server, take the path of least resistance.  10.04 LTS is proven in the field.  12.04 will be new, and as much as anyone might hate to admit it, will have problems that will need to be patched.  I suspect that would continue for a month or two during a "shakedown" of the new OS. 

I don't know about changes to Apache, etc., may be.  Nor do I know if there have been changes to the database software you use that may also require some adjustment.  I would be prepared for a full export, recreation of tables, full import, recreation of indexes, etc..  Has anything changes in PHP, etc., that may have an affect on your transition?  It may not need to be done, but the biggest thing you can do is have yourself prepared to cover all your bases, particularly on something as mission critical as your server.  Convince your managers you need some sort of box to test the conversion process on before you try it on the fly.  They shouldn't be adverse to this when they understand how critical their system is and that there are some unknowns.

I hope others with the detailed knowledge will address potential PHP, database, etc., changes from 9.x to 10.x or 12.04.  If there are none (read none, not just "none of critical importance" - they come back to bite you), more power to you.  I would just hope everyone here will do their best to be sure you are fully prepared.

Dave ;)

---

