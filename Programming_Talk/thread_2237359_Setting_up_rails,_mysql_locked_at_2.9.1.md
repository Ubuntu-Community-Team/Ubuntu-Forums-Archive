---
title: "Setting up rails, mysql locked at 2.9.1"
date: 2014-08-01
forum: Programming Talk
---

### Post by Ed J on 2014-08-01
I trying to get a rails development environment setup on my freshly install ubuntu 14.04.
I've installed ruby, rvm, rails, LAMP.
I know ruby is working, I can get to the irb
I know mysql is working since I can access it using phpmyadmin, and the command line.
After I installed rails I created a test project that appeared to indicate rails was functioning, but didn't check the db.
I cloned my repo from github and tried to run the bundler and it failed the mysql portion.
Other gems had no problem.

When running 
```
 bundle install 
```
I get the following...
Which is similar to the errors I get when I run gem install mysql -v '2.9.1'

```

Gem::Installer::ExtensionBuildError: ERROR: Failed to build gem native extension.

        /usr/bin/ruby1.9.1 extconf.rb 
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lm... yes
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lz... yes
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lsocket... no
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lnsl... yes
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lmygcc... no
checking for mysql_query() in -lmysqlclient... no
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
	--with-opt-dir
	--without-opt-dir
	--with-opt-include

...some omiited for brevity

	--with-mygcclib
	--without-mygcclib
	--with-mysqlclientlib
	--without-mysqlclientlib


Gem files will remain installed in /home/ed/.bundler/tmp/3543/gems/mysql-2.9.1 for inspection.
Results logged to /home/ed/.bundler/tmp/3543/gems/mysql-2.9.1/ext/mysql_api/gem_make.out
An error occurred while installing mysql (2.9.1), and Bundler cannot continue.
Make sure that `gem install mysql -v '2.9.1'` succeeds before bundling.


```

I did try to install mysql using apt-get at first that didn't work so I installed LAMP later. 
Not sure how to fix this mess.

---

