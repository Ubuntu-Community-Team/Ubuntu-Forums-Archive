---
title: "If you can handle xml with python read please"
date: 2008-07-03
forum: Programming Talk
---

### Post by gsiliceo on 2008-07-03
Hi, i want to export my rhythmbox ratings to itunes, i know is possible to do it with a python script because [there is already one]("http://code.google.com/p/itunes-to-rhythmbox-ratings/") that goes the other way (importing itunes ratings in rhythmbox).


We'll if anybody can help me with this, i've attached what i've got done so far, its a modification of the original script mentioned above, but is not working.

I attack two small samples of both xmls files.

I post here because im frustrated after 4 days of tinkering with this thing, i've tried several tools to manage xml.

And i don't really want to lose 2 years of ratings just because rhythmbox can't write them to an ipod.

---

### Post by pmasiar on 2008-07-03
did you tried ElementTree to parse XML? Since 2.5 is in core modules, if not- easy to install.

FOr generating XML, I learned kid templating a while ago and am 100% happy.

---

### Post by gsiliceo on 2008-07-03
Oh thanks for the advice, i needed to know what should i learn since im a python noob.

---

### Post by pmasiar on 2008-07-03
depends what you already know.... see wiki in my sig - links for Python learners

---

### Post by days_of_ruin on 2008-07-03
[http://ubuntuforums.org/showthread.php?t=594676&highlight=parsing+xml+python]("http://ubuntuforums.org/showthread.php?t=594676&highlight=parsing+xml+python")

---

### Post by gsiliceo on 2008-07-03
THank you that regex command works wonders and since this is a one time thing i don't need to learn complicated libraries to correctly parse my xml.

---

### Post by gsiliceo on 2008-07-04
I feel stupid i didnt needed to learn all this to export my ratings to itunes i fact i discovered a programming-less metod to export ratings from any media player to any media player.
Simply create m3u playlists with itumes with 5 stars then one with 4 stars and so on.
Then import and click the raiting on them ha!
Thanks anyway

---

