---
title: "How do i find files from terminal?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by daimaru on 2008-04-27
hi i noticed that in 8.04 the locate command does not work anymore for me.

to find files i used to update the locate database and then search for the file i wanted:
```
sudo locate -u
locate hdparm.conf

```locate -u does not exist anymore, so I'm looking for a way to find stuff from terminal.

the find command never seems to return what i want PLUS it takes ages ...
```
find / -name 'hdparam.conf' 
```any help appreciated thx

---

### Post by elpichi on 2008-04-27
I use this to look in a specific directory
```
ls *hdparm.conf*
```
this looks for all file with those words in its name

but locate still works for me, using hardy..
according to locate entries
to update the database 
```

-d, --database DBPATH  use DBPATH instead of default database (which is
                         /var/lib/mlocate/mlocate.db)
```
shouldn't that do the job?

---

### Post by FakeOutdoorsman on 2008-04-27
I usually:
```
sudo updatedb
locate -i hdparm
```

---

### Post by daimaru on 2008-04-27
thank you,
must have totally overlooked the updatedb thing. That solved it for me thanks again guys.

ps: been some time since i visited the forum, so I noticed the change in design. Where do I [COLOR=Red]mark my thread as "Solved"[/COLOR] ? it used to be under "tread tools" but its not there anymore.

---

### Post by FakeOutdoorsman on 2008-04-27
Good question.  Looks like it hasn't been [re-enabled yet]("http://ubuntuforums.org/showpost.php?p=4788174&postcount=2").  In my uneducated opinion, I believe they released the redesign way to early.  As of a few days ago, all links looked just like normal text.

---

### Post by daimaru on 2008-04-27
> **FakeOutdoorsman said:**
> Good question.  Looks like it hasn't been [re-enabled yet]("http://ubuntuforums.org/showpost.php?p=4788174&postcount=2").  In my uneducated opinion, I believe they released the redesign way to early.  As of a few days ago, all links looked just like normal text.

yeah and could it be that the forum has slowed down to a crawl? or is it just my connection. "Search took 25 seconds" lol omg!

---

### Post by FakeOutdoorsman on 2008-04-27
It does sometimes seem slower.  I assumed it was due to traffic from Hardy Heron.  I seem to get better results (at least faster results) using google site search:
```
site:ubuntuforums.org openbox
```

---

### Post by daimaru on 2008-04-27
> **FakeOutdoorsman said:**
> It does sometimes seem slower.  I assumed it was due to traffic from Hardy Heron.  I seem to get better results (at least faster results) using google site search:
```
site:ubuntuforums.org openbox
```
guess it was a network glitch on my side. Now everything runs ok. but still I guess to close the thread I'll have to do it the old fashioned way by editing my post and chaning the title to [Solved]...

---

