---
title: "What's GetDeb???"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by iscariotes on 2013-04-15
My sources.list has these lines:

# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) quantal-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) quantal-getdeb games

What's getdeb repository? What is in it? Should I enable it?

---

### Post by raja.genupula on 2013-04-15
you can find about them here 

[http://www.ubuntuupdates.org/ppa/getdeb_apps](http://www.ubuntuupdates.org/ppa/getdeb_apps)
[http://www.ubuntuupdates.org/ppa/getdeb_games](http://www.ubuntuupdates.org/ppa/getdeb_games)

---

### Post by iscariotes on 2013-04-16
Sorry, I didn't understand well... what's the difference between Getdeb and PPA?

---

### Post by pqwoerituytrueiwoq on 2013-04-16
[getdeb](http://www.getdeb.net/updates/ubuntu/12.10/)/[playdeb](http://www.playdeb.net/updates/Ubuntu/12.04) are repos, a ppa is on lauchpad (not much difference at the end of the day, both are software sources)

you could combine those lines like this:
[FONT=courier new]# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) quantal-getdeb apps games[/FONT]

you probally disabled them cause the site was dead for 2-3 months, that is a source i recommend and setup for anyone i install linux for

---

