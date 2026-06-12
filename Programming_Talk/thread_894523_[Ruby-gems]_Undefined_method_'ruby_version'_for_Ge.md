---
title: "[Ruby-gems] Undefined method 'ruby_version' for Gem:Module"
date: 2008-08-19
forum: Programming Talk
---

### Post by cybertoast on 2008-08-19
*A solution that might be useful to others:*
Sometime in the last few weeks I started getting 
```

/usr/bin/gem:14: undefined method `ruby_version' for Gem:Module (NoMethodError)

```
any time I ran a *gem install anything*.

The solution was pretty straightforward:
```

sudo update_rubygems
sudo gem install rubygems_update

```

Things now work!

---

### Post by qnub on 2008-11-30
> sudo update_rubygems
on my system (Ubuntu server 8.10 amd64) say:
```
sudo: update_rubygems: command not found
```

---

### Post by hypertall on 2010-11-29
I had the same problem. update_rubygems (or update-rubygems) doesn't work. What I did was follow this: [http://stackoverflow.com/questions/1814301/updating-rubygems-on-ubuntu/1818903](http://stackoverflow.com/questions/1814301/updating-rubygems-on-ubuntu/1818903)
 
sudo apt-[COLOR=#00008b]get[/COLOR] remove rubygems 
wget [http:[COLOR=#808080]//rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz[/COLOR]]("http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz") 
tar xzvf rubygems-[COLOR=#800000]1.3[/COLOR].7[COLOR=#800000].tgz[/COLOR] 
cd rubygems-[COLOR=#800000]1.3[/COLOR].7 
sudo ruby setup.rb 
sudo ln -s /usr/bin/gem1.[COLOR=#800000]8[/COLOR] /usr/bin/gem 
sudo gem update --system 
 
It worked for most gems, but still didn't install mongrel and sqlite. I did 
 
sudo apt-get install libsqlite3-dev
 
and then
 
gem install mongrel 
 
and that solves it.

---

