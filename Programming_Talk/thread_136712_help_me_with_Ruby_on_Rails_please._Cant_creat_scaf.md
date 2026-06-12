---
title: "help me with Ruby on Rails please. Cant creat scaffold."
date: 2006-02-26
forum: Programming Talk
---

### Post by bbqbaker on 2006-02-26
I have been sitting here for hrs trying to create the scaffold according to the RoR book i recently purchase. i getting just a little frustrated now. lol

anyways i am at the part of the book that is creating the scaffold for my DB. now when i type

ruby script/generate scaffold Products Admin, I get following

exist app/controllers/
...
Access denied for user: 'root@localhost' (using password:no)

//////////////////////

now i assumed that i should put root and my root password everywhere in the database.yml. i also check to see if i can access mysql logging in with root + root password. that all is ok.

what should I do? i know its something really simple....

---

### Post by stoffe on 2006-02-26
I *think* that it's an issue with the built-in Mysql driver in rails - it has problems on Debian and Ubuntu. Something about accessing the socket that isn't working because it's in the wrong place, but I don't remember details.

Installing the C++ binding version instead fixes it. I suppose it is in the repos, but I usually install Rails with gem so I don't know. If you use gems, just grab appropriate mysql and ruby headers from repos and "sudo gem install mysql". There's instructions for all of this somewhere on the Rails wiki, including the problems with the socket.

---

### Post by bbqbaker on 2006-02-26
hi thanks for the reply. actually after MUCH frustration, i was able to reset my PW to root. now the error message is gone but now i have this..

koloa@ubuntu:/var/www/depot$ ruby script/generate scaffold Product Admin
      exists  app/controllers/
      exists  app/helpers/
      exists  app/views/admin
      exists  test/functional/
  dependency  model
      exists    app/models/
      exists    test/unit/
      exists    test/fixtures/
   identical    app/models/product.rb
   identical    test/unit/product_test.rb
   identical    test/fixtures/products.yml
       error  Before updating scaffolding from new DB schema, try creating a tab le for your model (Product)
///////////////////////

products is a table i created for my depot_development database. its already in there, but not sure why its not seeing it.

---

### Post by bbqbaker on 2006-02-26
i also noticed in the fine print that i may need to reinstall mysql/ruby drivers? is this so? is there an apt-get for this?

---

### Post by bbqbaker on 2006-02-26
in my synaptic package manager i have the following checked:

libdbd-mysql-ruby,
libdbd-mysql-ruby1.8, 
libdbd-mysql, and 
libdbd-mysql

and this is what my site has:
Ruby version	1.8.3 (i486-linux)
RubyGems version	0.8.11
Rails version	1.0.0
Active Record version	1.13.2
Action Pack version	1.11.2
Action Web Service version	1.0.0
Action Mailer version	1.1.5
Active Support version	1.2.5
Application root	/var/www/depot
Environment	development
Database adapter	mysql

---

### Post by bbqbaker on 2006-02-27
ok, so i thought there was something corrupt since i cant install gem install mysql. well i got that fixed, but still encountering this

error  Before updating scaffolding from new DB schema, try creating a table for your model (Product)


the product table is created and located in depot_development DB. since it is still not working, i created a database called product. still no avail...


any ideas?

---

### Post by beastie on 2006-03-03
A good article helped me get 'gem install mysql' working :

[http://paulgoscicki.com/archives/2005/09/ruby-on-rails-on-ubuntu/]("http://paulgoscicki.com/archives/2005/09/ruby-on-rails-on-ubuntu/")

... then all my Database Connection problems were solved! Long live Rails, long live Ubuntu Linux! (under Ubuntu 5.10)

---

### Post by bbqbaker on 2006-03-03
hey thanks for the reply. what fixed my problem was a fresh install AND my mysql table was lower case!

---

