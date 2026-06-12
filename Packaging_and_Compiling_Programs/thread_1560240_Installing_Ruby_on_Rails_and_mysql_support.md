---
title: "Installing Ruby on Rails and mysql support"
date: 2010-08-24
forum: Packaging and Compiling Programs
---

### Post by templewulf on 2010-08-24
Hi all,

I'm a long-time programmer, but I'm new to Ubuntu. I wanted to try a Ruby on Rails site with my new Linux box, but I'm having trouble with some setup.

I got the RoR site to the point where Apache displays the default Welcome page. At this point, the tutorial I'm following suggests I do "rake db:create". Rake tells me that mysql support is no longer bundled, so I try to install the mysql gem (i.e. sudo gem install mysql).

The problem is that when I try to gem install mysql, I get this output:
```
Building native extensions.  This could take a while...
ERROR:  Error installing mysql:
        ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb
extconf.rb:10:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:10
```Obviously I'm missing the extconf.rb script, but I don't know what that means for my installation process or how to go about fixing it. Any tips?

PS: I'm also pretty new to the forums, so any tips on moving the thread or forum conventions are also appreciated.

---

### Post by SevenMachines on 2010-08-25
i'm guessing you're actually missing mkmf.rb. check you have the ruby dev package installed
$ sudo apt-get install ruby1.8-dev

---

