---
title: "apache mysql php"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by lgastmans on 2008-05-06
Dear people,

Upgraded from Gutsy to Hardy Heron and having a hard time installing apache mysql and php in this new version. The following command used to work in Gutsy, but doesn't anymore:

apt-get install apache2 php5 libapache2-mod-php5 

The following message comes: E: Couldn't find package apache2

Can somebody help me out? And while you're at it, I need to install phpmyadmin, too ;-)

Thank you

---

### Post by ibutho on 2008-05-06
Apache 2 is available in Hardy. Check if you repositories are setup properly (and refreshed by running "apt-get update").

---

### Post by Joeb454 on 2008-05-06
I've just checked and I can have apache2 as a package also. Make sure you have all repositories enabled, that could be the problem :)

---

### Post by lgastmans on 2008-05-06
as always: thank you! 
apt-get update did the job

---

