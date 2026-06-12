---
title: "ruby &amp; rails - even more broken!"
date: 2006-03-28
forum: Repositories &amp; Backports
---

### Post by pumuckel on 2006-03-28
hi there,

well... it's been a big mistake to start with a fresh and clean breezy installation on my notebook. the ruby version from official repositories seems not to support the rails web development framework.

yesterday everything worked fine on my up-to-date breezy! after a new installation today i added ruby through synaptic and gems by download and setup.

as recommended (because rails in repository seems to be broken too) i installed rails through gems. everything went fine (see additional informations below).

but now have a look at this:
```
axel@r2d2:~/Work$ rails test

    Rails does not work with Ruby version 1.8.3.
    Please upgrade to version 1.8.4 or downgrade to 1.8.2.

axel@r2d2:~/Work$
```

](*,) 

well... here few additional informations:
```
axel@r2d2:~/Work$ ruby -v
ruby 1.8.3 (2005-06-23) [i486-linux]
```

```
axel@r2d2:~/Work$ gem list

*** LOCAL GEMS ***

actionmailer (1.2.0)
    Service layer for easy email delivery and testing.

actionpack (1.12.0)
    Web-flow and rendering framework putting the VC in MVC.

actionwebservice (1.1.0)
    Web service support for Action Pack.

activerecord (1.14.0)
    Implements the ActiveRecord pattern for ORM.

activesupport (1.3.0)
    Support and utility classes used by the Rails framework.

postgres-pr (0.4.0)
    A pure Ruby interface to the PostgreSQL (>= 7.4) database

rails (1.1.0)
    Web-application framework with template engine, control-flow layer,
    and ORM.

rake (0.7.0)
    Ruby based make-like utility.

rubygems-update (0.8.11)
    RubyGems Update GEM

sources (0.0.1)
    This package provides download sources for remote gem installation
```

ruby (and rails) integration in ubuntu is as worse as wlan-wpa-encryption or ruby in apple-tiger....

---

### Post by beastie on 2006-03-29
> rails (1.1.0)
    Web-application framework with template engine, control-flow layer,
    and ORM.

There is a new version of Rails out there, 1.1. It's that version you have on your new box, because you installed in using gem, and gem gave you the latest stable release. Your old box is probably running 1.0. Rails 1.1 doesn't like Ruby 1.8.3, for whatever reason!

So, solutions ahead are either downgrading to 1.8.2, or installing 1.8.4. I chose to upgrade... but I haven't found a Ubuntu package, so I'm trying to build it from source right away, 'cause I want to run Rails 1.1...

*UPDATE*

Easy shot :) Follow the steps...

Get the .deb package for Ruby 1.8.4 and Libruby 1.8.4 from Dapper repository

[http://packages.ubuntu.com/dapper/libs/libruby1.8]("http://packages.ubuntu.com/dapper/libs/libruby1.8")
[http://packages.ubuntu.com/dapper/interpreters/ruby1.8]("http://packages.ubuntu.com/dapper/interpreters/ruby1.8")

Unpack 'em:
  dpkg -i packagename.deb

And enjoy using Rails 1.1.

---

### Post by pumuckel on 2006-03-29
[QUOTE=beastie]There is a new version of Rails out there, 1.1. It's that version you have on your new box, because you installed in using gem, and gem gave you the latest stable release. Your old box is probably running 1.0. Rails 1.1 doesn't like Ruby 1.8.3, for whatever reason!

So, solutions ahead are either downgrading to 1.8.2, or installing 1.8.4. I chose to upgrade... but I haven't found a Ubuntu package, so I'm trying to build it from source right away, 'cause I want to run Rails 1.1...

*UPDATE*

Easy shot :) Follow the steps...

Get the .deb package for Ruby 1.8.4 and Libruby 1.8.4 from Dapper repository

[http://packages.ubuntu.com/dapper/libs/libruby1.8]("http://packages.ubuntu.com/dapper/libs/libruby1.8")
[http://packages.ubuntu.com/dapper/interpreters/ruby1.8]("http://packages.ubuntu.com/dapper/interpreters/ruby1.8")

Unpack 'em:
  dpkg -i packagename.deb

And enjoy using Rails 1.1.[/QUOTE]
that's exactly what i did last night! :-)

dpkg -P --force-depends libruby1.8 (kick the breezy package without removing the dependencies)
dpkg -i libruby1.8_1.8.4-1ubuntu1_i386.deb (install the dapper package)

rails is broken for ruby 1.8.3 due to api-changes. *pitsch-patsch* to the rails people, minor version update with api changes... which hell did they escape...

anyway, i filed a bug in launchpad for the package manager.

---

### Post by reedlaw on 2006-03-29
I have upgraded to 1.1 and now I get this error when I try to open a controller view in a web browser:
```
 Permission denied - /var/www-rails/sias/public/../config/../tmp/sessions//ruby_sess.1e8ace5968fe815b
/usr/lib/ruby/1.8/pstore.rb:289:in `initialize'
/usr/lib/ruby/1.8/pstore.rb:289:in `transaction'
/usr/lib/ruby/1.8/cgi/session/pstore.rb:71:in `initialize'
/usr/lib/ruby/1.8/cgi/session.rb:273:in `initialize'
/usr/lib/ruby/gems/1.8/gems/actionpack-1.12.0/lib/action_controller/cgi_process.rb:111:in `session'
/usr/lib/ruby/gems/1.8/gems/actionpack-1.12.0/lib/action_controller/cgi_process.rb:141:in `stale_session_check!'
/usr/lib/ruby/gems/1.8/gems/actionpack-1.12.0/lib/action_controller/cgi_process.rb:107:in `session'
/usr/lib/ruby/gems/1.8/gems/actionpack-1.12.0/lib/action_controller/base.rb:885:in `assign_shortcuts_without_flash'
/usr/lib/ruby/gems/1.8/gems/actionpack-1.12.0/lib/action_controller/flash.rb:141:in `assign_shortcuts'
/usr/lib/ruby/gems/1.8/gems/actionpack-1.12.0/lib/action_controller/base.rb:373:in `process_without_filters'
/usr/lib/ruby/gems/1.8/gems/actionpack-1.12.0/lib/action_controller/filters.rb:364:in `process_without_session_management_support'
/usr/lib/ruby/gems/1.8/gems/actionpack-1.12.0/lib/action_controller/session_management.rb:117:in `process'
/usr/lib/ruby/gems/1.8/gems/rails-1.1.0/lib/dispatcher.rb:38:in `dispatch'
/usr/lib/ruby/gems/1.8/gems/rails-1.1.0/lib/fcgi_handler.rb:150:in `process_request'
/usr/lib/ruby/gems/1.8/gems/rails-1.1.0/lib/fcgi_handler.rb:54:in `process!'
/usr/lib/ruby/1.8/fcgi.rb:600:in `each_cgi'
/usr/lib/ruby/1.8/fcgi.rb:597:in `each_cgi'
/usr/lib/ruby/gems/1.8/gems/rails-1.1.0/lib/fcgi_handler.rb:53:in `process!'
/usr/lib/ruby/gems/1.8/gems/rails-1.1.0/lib/fcgi_handler.rb:23:in `process!'
/var/www-rails/sias/public/dispatch.fcgi:24
```

This is for a new rails project created with 1.1.  My old projects still work fine.  This is also only when I run the project through Apache2.  Using the WeBrick server I get no such error. Anyone else get this?

---

### Post by brixen on 2006-03-31
reedlaw, I got those errors under apache2 because of the permissions on the rails app directory and files. I did a 
[FONT="Courier New"]chgrp www-data -R /path/to/rails/app[/FONT]
and a 
[FONT="Courier New"]chmod g+w -R /path/to/rails/app[/FONT]
and that fixed it for me.

Usually, when you're using WEBrick, you run it as you, so the file permissions are probably fine if you created the rails app yourself. But apache2 runs as a different user.

---

### Post by reedlaw on 2006-04-05
I fixed it by switching to Litespeed web server.  Now I am having problems because I need to install ruby1.8-dev but it says it requires a different version of ruby (I am running 1.8.4).

---

### Post by krueger on 2006-04-10
Why are ruby packages labeled 1.8.2 something installing a ruby 1.8.3 version? I wish there was a quick solution of getting a 1.8.4 ruby, short of uninstalling all ruby-related packages and compiling all from scratch.

---

### Post by comforteagle on 2006-04-14
[QUOTE=brixen]reedlaw, I got those errors under apache2 because of the permissions on the rails app directory and files. I did a 
[FONT="Courier New"]chgrp www-data -R /path/to/rails/app[/FONT]
and a 
[FONT="Courier New"]chmod g+w -R /path/to/rails/app[/FONT]
and that fixed it for me.

Usually, when you're using WEBrick, you run it as you, so the file permissions are probably fine if you created the rails app yourself. But apache2 runs as a different user.[/QUOTE]

brixen, you rule!

---

### Post by paullovesjam on 2006-04-20
I followed Beastie's instructions and everything went smoothly working first time. 
My procedure if this helps anyone: 
Machine is Ubuntu Breezy, with ruby 1.8.3 installed. I then downloaded and installed (without removing the existing broken ruby) with the following command:

sudo dpkg -i libruby1.8_1.8.4-1ubuntu1_i386.deb ruby1.8-dev_1.8.4-1ubuntu1_i386.deb

After installation I confirmed the upgrade had been a success:
ruby --version => ruby 1.8.4 (2005-12-24) [i486-linux]

Downloads were take from [URL="http://archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/"]http://archive.ubuntu.com/ubuntu/pool/main/r/ruby1.8/
[/URL]

---

### Post by arghh on 2006-05-10
another way that works (i have no idea what else this breaks!)

is to go to the repositories /etc/apt/sources.list and replace every instance of hoary with dapper then go apt-get update
then go apt-get install ruby
then go apt-get -f install

ruby --version then shows 
ruby 1.8.4 (2005-12-24) [i486-linux]

and rails runs

so far so good!

---

