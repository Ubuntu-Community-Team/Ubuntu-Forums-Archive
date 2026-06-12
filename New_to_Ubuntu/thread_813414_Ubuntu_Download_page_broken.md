---
title: "Ubuntu Download page broken?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by mohnkern on 2008-05-30
Has anyone else tried to go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and gotten an error and can't download?

The error I'm seeing is:

user warning: Table 'drupal_ubuntu2.mirror_list' doesn't exist query: select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 1 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'EU' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 2 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'NA' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 3 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'AS' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 4 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'SA' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 5 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'OC' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 6 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'AF' order by o, countryname in /srv/drupal-farm/www/includes/database.mysql.inc on line 172.

so I can't select a download location.  I've tried Firefox 2.0.5 and IE 7

---

### Post by Vicfred on 2008-05-30
im gettin that message too >_<, im on ubuntu 8.04 with firefox 3 RC1.

You can still download ubuntu through the torrent, that way you help to dont overload the server, and it is faster =D, download it here.

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

---

### Post by drs305 on 2008-05-30
I get the same thing. It's the beginning of the weekend not too long after a major release. The server is probably just overloaded.

Added: or somebody just forgot a . in a line of code ;-)

---

### Post by mohnkern on 2008-05-30
At least it isn't me then.

> **Vicfred said:**
> im gettin that message too >_<

---

### Post by Mark_in_Hollywood on 2008-05-30
I had used that site (URL) about 30 days ago to d/l a copy of Hardy Heron. when I looked at it only a moment ago at 5:15 pacific daylight time (around 1 am UCT), it had the same error message you posted.

I would give it a day or maybe two days and give the programmers some time to fix that.

Nothing's much wrong, maybe some wires got crossed. You could try a mirror, if you are in a big hurry.

---

### Post by sports fan Matt on 2008-05-30
Confirmed and I also think too much traffic but I wonder why now since HH has been out a few weeks?

---

### Post by jbspear on 2008-05-30
I'm also looking at the Ubuntu download page and it doesn't seem operational.  For example, the "choose a location near you" drop down list is empty and offers no choices.  

I looked into getting a free installation DVD shipped but apparently they take 10 weeks.  An alternative might be that there are some private sellers on Amazon who are offering the installation DVDs for under $6 + shipping.  I have no relationship to them but the link is at [http://www.amazon.com/gp/offer-listing/B0019KKM4O/ref=dp_olp_2?ie=UTF8&qid=1212197800&sr=8-1](http://www.amazon.com/gp/offer-listing/B0019KKM4O/ref=dp_olp_2?ie=UTF8&qid=1212197800&sr=8-1)

I have a new laptop that came equipped with Vista + Windows Mail and I really really don't care for either, plus I'm getting a lot of hangups and crashes.  The latest version of WORD has been complexified beyond reason.  So, I'm looking forward to trying Ubuntu which is reported to be much cleaner and simpler for routine uses.  Just need the download site to come back to life, or perhaps I'll try the Amazon sellers.

---

