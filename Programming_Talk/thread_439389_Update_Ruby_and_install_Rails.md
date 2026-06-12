---
title: "Update Ruby and install Rails"
date: 2007-05-10
forum: Programming Talk
---

### Post by tc101 on 2007-05-10
Where are the best instructions for updating Ruby and installing Rails on ubuntu?

---

### Post by tc101 on 2007-05-10
Also, how can I tell if mySQL is installed, and if it is not, how do I install it?

---

### Post by cknoblock on 2007-05-10
This worked for me.

[http://rails.aizatto.com/2007/05/02/installing-ruby-on-rails-on-ubuntu-feisty-fawn-via-rubygems/](http://rails.aizatto.com/2007/05/02/installing-ruby-on-rails-on-ubuntu-feisty-fawn-via-rubygems/)
or
[http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu) (includes mysql install)

To see if you have mysql installed you can either open Synaptec and search form mysql and see if any of the mysql-server-x.x is installed, or you can check for the init script under /etc/init.d/mysql. If it exists, you got it.

-chris

---

### Post by metnik on 2007-05-10
[http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu)

mysql is mysql-server on Synaptic

---

### Post by tc101 on 2007-05-11
Thanks for the link to 
[http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu)

Did you just use "The quickest way" method at the begining?

---

