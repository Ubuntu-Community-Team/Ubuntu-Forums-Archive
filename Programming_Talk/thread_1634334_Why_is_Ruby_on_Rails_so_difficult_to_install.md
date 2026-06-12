---
title: "Why is Ruby on Rails so difficult to install?"
date: 2010-11-30
forum: Programming Talk
---

### Post by cancer10 on 2010-11-30
HI

I mean installing the whole LAMP package can be done with just 1 line

```
sudo tasksel install lamp-server
```


But taking a look into [this]("http://ubuntuforums.org/showthread.php?t=169891") tutorial, its like a monster process. 

Why is it a lengthy process? No simple alternative?



Any inputs will be appreciated.


Thanks

---

### Post by CptPicard on 2010-11-30
If you're going to be developing, it really is not all that hard.

First of all, that's a very old thread; but anyway: You need to get the rubygems package management system because it's just nicer to have in the long run than to rely on the distribution package manager (although there is a rails package here on Debian though).

After that it's just a matter of installing the rails gem and off you go, there is no need to mess with an Apache configuration unless you specifically plan to deploy on it -- rails comes with its own development server.

---

### Post by cancer10 on 2010-11-30
So the question now is, how do I install ruby on rails in a simple way?


Thanks for your reply

---

### Post by trivialpackets on 2010-11-30
> **cancer10 said:**
> So the question now is, how do I install ruby on rails in a simple way?


Thanks for your reply


Simple Way.

```
sudo apt-get install ruby irb ri rdoc ruby1.8-dev libzlib-ruby libyaml-ruby libreadline-ruby libncurses-ruby libcurses-ruby libruby libruby-extras libfcgi-ruby1.8 build-essential libopenssl-ruby libdbm-ruby libdbi-ruby libdbd-sqlite3-ruby sqlite3 libsqlite3-dev libsqlite3-ruby libxml-ruby libxml2-dev libssl-dev libpcre3-dev zlib1g-dev

wget [http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz](http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz)

tar -zxvf rubygems-1.3.7.tgz

cd rubygems-1.3.7

sudo ruby setup.rb

sudo gem install rails
```


HOWEVER...It's been a long time since I've done it this way before.  I personally use rvm which is a bit less simple, but it gets the job done for me.

---

### Post by tgalati4 on 2010-11-30
I installed RoR using guidance found on these forums.  I have Tracks running on both Dapper and Hardy servers. It's involved, but doable.  Depending on what application you are installing, you may use a binary blob instead via bitnami stacks.

Tracks forums on Linux: [http://www.getontracks.org/forums/viewforum/8/](http://www.getontracks.org/forums/viewforum/8/)

Bitnami:  [http://bitnami.org/](http://bitnami.org/)

---

### Post by Simian Man on 2010-11-30
On Fedora:
```

yum install rubygem-rails

```
They also have several other rubygem packages.  I find that Fedora has the best, most up-to-date development packages.

---

### Post by trivialpackets on 2010-11-30
If you want to set up the box for deployment, you'll need something a bit more than my setup.  I documented it [here]("http://rubyplusplus.wordpress.com/2010/08/24/quick-rails-box-ubuntu-10-04/") for 10.04 (and this is only one of many options), but haven't even thought about it lately.  While developing, what I had on the first post should be enough, and if you need more than that while in development, I recommend getting to know a bit of git and heroku.  Great tools.

---

### Post by cancer10 on 2010-11-30
I wish debian could make a much simpler package for installing ruby :(

---

### Post by cancer10 on 2010-11-30
> **eric.proctor said:**
> Simple Way.

```
sudo apt-get install ruby irb ri rdoc ruby1.8-dev libzlib-ruby libyaml-ruby libreadline-ruby libncurses-ruby libcurses-ruby libruby libruby-extras libfcgi-ruby1.8 build-essential libopenssl-ruby libdbm-ruby libdbi-ruby libdbd-sqlite3-ruby sqlite3 libsqlite3-dev libsqlite3-ruby libxml-ruby libxml2-dev libssl-dev libpcre3-dev zlib1g-dev

wget [http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz](http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz)

tar -zxvf rubygems-1.3.7.tgz

cd rubygems-1.3.7

sudo ruby setup.rb

sudo gem install rails
```


HOWEVER...It's been a long time since I've done it this way before.  I personally use rvm which is a bit less simple, but it gets the job done for me.



Will this process be automatically mapped with apache, so when I run [http://localhost/myrubyapp](http://localhost/myrubyapp), my ruby application would be running?

---

### Post by Søren on 2010-12-01
i havent installed it for six months or so but i always thought it was easy in synaptic? if you just check the rails install it installs all the other 2763589 dependencies for you. It even set up the environmental variables.

her is an a guide for installing on 10.04
[http://ubuntuforums.org/showthread.php?t=1459056](http://ubuntuforums.org/showthread.php?t=1459056)
How to install Ruby on Rails on Ubuntu 10.04 Lucid Lynx

---

### Post by excetara2 on 2010-12-01
I'd install with rvm. This guide is fairly simple if your familiar with using command line:

[http://www.web2linux.com/05/installing-rails-3-on-ubuntu-10-04-lucid-lynx/](http://www.web2linux.com/05/installing-rails-3-on-ubuntu-10-04-lucid-lynx/)


Gives a little more details on the rvm part (if not sure how to properly edit .bashrc or where to go to do so):

[http://www.christopherirish.com/2010/08/25/how-to-install-rvm-on-ubuntu-10-04/](http://www.christopherirish.com/2010/08/25/how-to-install-rvm-on-ubuntu-10-04/)

I wouldn't say it's much easier to install rails 3 on windows.

Cheers

---

