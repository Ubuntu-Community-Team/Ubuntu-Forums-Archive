---
title: "repositories- when will open office 3 be included?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by ginestre on 2008-11-03
The new OO 3 reads and writes the new microsoft 'open' format docx etc, which many of our correspondents unwittingly use, so I need to update. And since the repo route to installation is so much simpler than anything else, I wondered if OO 3 is likely to be included soon? I'd rather wait a few days than manually install on the 6 machines I have in my care... Does anyone know'

---

### Post by ronocdh on 2008-11-03
> **ginestre said:**
> The new OO 3 reads and writes the new microsoft 'open' format docx etc, which many of our correspondents unwittingly use, so I need to update. And since the repo route to installation is so much simpler than anything else, I wondered if OO 3 is likely to be included soon? I'd rather wait a few days than manually install on the 6 machines I have in my care... Does anyone know'
I would expect 3 to make it into the repos by year's end, January at the latest. RC4 came very late to the table, and the lads at Canonical didn't want Intrepid to ship with anything that they weren't sure was stable (and kudos to them for it!).

If that's too long of a wait for you--and please keep in mind it's total speculation--then I'd recommend [installing it yourself]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml"). Good luck!

---

### Post by Paqman on 2008-11-03
Bear in mind it'll probably go into the backports repo, not the main ones. So you'll need that enabled.

---

### Post by Fass on 2008-11-03
You can also, if you want to and are runing Ibex, us Calc's OpenOffice ppa by adding to your /etc/apt/sources.list file:

```
#Calc's_open_office_ppa
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

Then just run sudo aptitude update && sudo aptitude upgrade and it will update to OpenOffice 3.0.

---

