---
title: "Feisty Rails Sandbox with Lighttpd?"
date: 2007-04-20
forum: Programming Talk
---

### Post by moon2js on 2007-04-20
Anyone else setting up Ruby on Rails on a Feisty box? I'm looking to set up rails with lighttpd this weekend, and I'm wondering if anyone else's in the same boat and wants to share notes.

I've tried in the past on Edgy with [this howto ("Install Ruby Rails on Ubuntu Edgy Eft")]("http://www.urbanpuddle.com/articles/2006/12/07/install-ruby-rails-on-ubuntu-edgy-eft"), but never really got the lighttpd.conf file quite right. There's also [stuff on the wiki]("https://help.ubuntu.com/community/RubyOnRails").

Anything I should know that is different from Edgy? Any tips?

---

### Post by wastedtime on 2007-04-22
I am also looking for a howto for ruby on rails on feisty. I tried using the tutorial at 
[http://ariejan.net/2006/12/03/installing-rails-on-ubuntu-dapper-edgy/](http://ariejan.net/2006/12/03/installing-rails-on-ubuntu-dapper-edgy/)

that only lead to a host of errors i describe here .

[http://ubuntuforums.org/showthread.php?t=417757](http://ubuntuforums.org/showthread.php?t=417757)

The same application used to work perfectly fine before the upgrade to feisty. I am thinking of going back to edgy in case this problem is not resolved :(.

When i used the tutorial . Fiesty could not find the following packages.

libmysqlclient14 
libmysqlclient14-dev

---

### Post by TheR on 2007-04-24
I got rails running on Festy x86-64 with Postgres 

gem seems to be broken (at least for me) and I install everything using synaptic.


by 

TheR

---

### Post by darrenm on 2007-04-24
I've had RoR working fine with Feisty but not with lighttpd.

I always do ```
sudo apt-get install rubygems rails
``` then ```
sudo gem update
``` and it works fine. MySQL client gets installed when you install MySQL.

---

### Post by ceeg on 2007-04-25
```

sudo apt-get install ruby ri rdoc rubygems 

```
```

sudo apt-get install lighttpd mysql-server

```
```

sudo gem install rails --include-dependencies

```
```

sudo apt-get install libmysql-ruby

```

Then enable a few lighttpd modules, like mod_proxy, mod_rewrite, mod_fasgcgi, etc. There is a command-line utility to do so. Then edit your /etc/lighttpd/lighttpd.conf file to setup a proxy for your web app. Easy.

---

