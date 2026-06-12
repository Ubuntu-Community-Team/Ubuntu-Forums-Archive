---
title: "How to install Ruby on Rails on Ubuntu 8.10"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Zeck on 2008-10-31
I all,
I have a question. How to install Ruby and Rails on Ubuntu 8.10. /easy way/ Any idea ?

---

### Post by talsemgeest on 2008-10-31
[http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu)

---

### Post by karatedog on 2009-04-16
> **talsemgeest said:**
> [http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu)
The link is dead, and the question remains. 
- should I use apt-get with dependencies or Synaptics?
- should I install Rails through Synaptics or gem? If I install it via Synaptics, it is not listed as installed gem.
Ruby on Rails Ubuntu documentation (for Ubuntu 8.04) strongly advise to forget Synaptics when installing Ruby or Rails

---

### Post by qrwe on 2009-04-16
Found this one:
[http://ruphus.com/code/rails/railsonubuntu-howto.html](http://ruphus.com/code/rails/railsonubuntu-howto.html)

---

### Post by Tibuda on 2009-04-16
I had problems installing Rails from the RubyGems version in both Intrepid (8.10) and Jaunty (9.04), so I suggest you install it from the source. It is not really that hard.
This is what I run in terminal to install it. I'll comment everything:
```
# Install Ruby and other dependencies
sudo aptitude install ruby rdoc irb ri libopenssl-ruby1.8 ruby1.8-dev build-essential

# Download RubyGems source code to /tmp and install it
cd /tmp
wget http://rubyforge.org/frs/download.php/45905/rubygems-1.3.1.tgz
tar xvzf rubygems-1.3.1.tgz
cd rubygems-1.3.1/
sudo ruby setup.rb
sudo ln -s /usr/bin/gem1.8 /usr/bin/gem

# Install Rails and Mongrel server (mongrel is optional)
sudo gem install rails mongrel

# Install support for Sqlite3 (optional)
sudo aptitude install libsqlite3-0 libsqlite3-dev
sudo gem install sqlite3-ruby

# Install support for MySQL (optional)
sudo aptitude install libmysql-ruby mysql-server mysql-client mysql-client-dev mysql-query-browser
sudo gem install mysql
```

Rails is already installed. You can see the Rails version in the terminal with
```
rails -v
```

You can update all yours gems later with:
```
sudo gem update
```

---

### Post by sudipta_cht on 2009-04-18
[http://wiki.rubyonrails.org/getting-started/installation/linux](http://wiki.rubyonrails.org/getting-started/installation/linux)

This one works perfectly

---

### Post by me.translucent on 2009-04-19
click system->administration->synaptic package manager.Search for rails there,click on it and click apply it will download the rails and you are done .

---

### Post by umuro on 2009-06-09
Using a package manager to install rails is not advisable. Then you cannot follow the latest upgrades.

You could  check if the current Jaunty tested installation applying to 8.10 also : [http://conceptspace.wikidot.com/rails101:basic-ruby-on-rails-installation](http://conceptspace.wikidot.com/rails101:basic-ruby-on-rails-installation)

It's just a few lines.

---

### Post by Noobuntu5 on 2009-06-13
> **sudipta_cht said:**
> [http://wiki.rubyonrails.org/getting-started/installation/linux](http://wiki.rubyonrails.org/getting-started/installation/linux)

This one works perfectly


+1 This was the best way to do it. !!!! :D

---

### Post by securians on 2010-01-30
Ruby on Rails or RoR, is an open source web application framework for the Ruby programming language.

We build quality Ruby On Rails web applications for start-ups and established businesses since early 2006. We focus on the core idea, perfect the interface, suggest innovative features and deliver; we help your company succeed faster by using the best technologies available.

Secure Next is a software technology corporation that develops, manufactures, and supports a wide range of software and web development projects. Headquartered in Fresno, California, USA, and its offshore in Chennai, India, we rock on every single projects we develop and venture into upcoming technology with a vision of agile web development & customer satisfaction. Thus, we want to make people feel informed and involved, committing quality and timeliness and ready to flourish using latest technology.

ref: [www.rordevelopers.com]("http://www.rordevelopers.com"), [offshore programmers, software programmers]("http://www.securenext.com") , [indian programmers]("http://www.securenext.com") & [URL="http://www.securenext.com/hire-dedicated-programmers.php"]hire developers
[/URL]

---

### Post by VinceMD on 2010-07-04
Hi,
The message above looks like spam to me ... Anyway, I hope my contribution will be helpful (and not spamful :D).
I wrote myself a short tutorial to install Ruby On Rails. I use it each time I need to setup a new development machine under Ubuntu. It covers the install of mysql and rmagick. Could be useful..
[http://www.vbrouillet.fr/news/2010/07/04/ubuntu-rails/](http://www.vbrouillet.fr/news/2010/07/04/ubuntu-rails/)
I didn't know you can use Synaptic for that..

---

