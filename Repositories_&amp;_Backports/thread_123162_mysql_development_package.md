---
title: "mysql development package?"
date: 2006-01-29
forum: Repositories &amp; Backports
---

### Post by benk on 2006-01-29
Is there a mysql development package for Ubuntu? I see a mysql-client, mysql-server, mysql-common but nothing that specifically says development.

The reason why I'm asking is that I'm trying to install a perl module (DBD::mSQL) via CPAN and it's asking for the mysql includes directory. I can't find it with the regular mysql packages but when I download the mysql binary there is definitely an includes package in there.

These are the repositories that I have in /etc/apt/sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse

---

### Post by moephan on 2006-01-29
I think you might need libmysqlclient. That should install the includes, etc... HTH

Cheers, Rick

---

### Post by longst on 2011-05-06
> **benk said:**
> Is there a mysql development package for Ubuntu? I see a mysql-client, mysql-server, mysql-common but nothing that specifically says development.

The reason why I'm asking is that I'm trying to install a perl module (DBD::mSQL) via CPAN and it's asking for the mysql includes directory. I can't find it with the regular mysql packages but when I download the mysql binary there is definitely an includes package in there.

These are the repositories that I have in /etc/apt/sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse

If you solve this problem regarding mysql development package ? Thanks

---

### Post by longst on 2011-05-06
I think I found the place to solve this question

[http://www.wolfe.id.au/2010/12/06/installing-ruby-with-rvm-on-ubuntu-10-10/](http://www.wolfe.id.au/2010/12/06/installing-ruby-with-rvm-on-ubuntu-10-10/)

"Install Mysql client and development package.
sudo apt-get install mysql-client libmysqlclient-dev"

so probably the "libmysqlclient-dev" has to be installed

---

### Post by longst on 2011-05-06
I think I found the place to solve this question

[http://www.wolfe.id.au/2010/12/06/installing-ruby-with-rvm-on-ubuntu-10-10/](http://www.wolfe.id.au/2010/12/06/installing-ruby-with-rvm-on-ubuntu-10-10/)

"Install Mysql client and development package.
sudo apt-get install mysql-client libmysqlclient-dev"

so probably the "libmysqlclient-dev" has to be installed

---

