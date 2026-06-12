---
title: "Installing Ruby on Rails on Ubuntu 7.10 Gutsy Gibbon"
date: 2007-10-26
forum: Programming Talk
---

### Post by Railsbuntu on 2007-10-26
Hi guys,

For my first post on the board, I am coming with a problem. I have not been able to install Rails cleanly on a fresh new install of Ubuntu.

Here are the steps I took:

```
sudo apt-get install ruby irb rdoc libyaml-ruby libzlib-ruby ri
wget http://rubyforge.org/frs/download.php/20989/rubygems-0.9.4.tgz
tar xvzf rubygems-0.9.4.tgz
cd rubygems-0.9.4
sudo ruby setup.rb
sudo gem update --system
sudo gem install rails -y
```

Then I wanted to install Retrospectiva, an issue tracking tool created under Rails:
```
sudo apt-get install libruby
sudo gem install mysql
```
The last command issues the following error:
```
Select which gem to install for your platform (i486-linux)
 1. mysql 2.7.3 (mswin32)
 2. mysql 2.7.1 (mswin32)
 3. mysql 2.7 (ruby)
 4. mysql 2.6 (ruby)
 5. Skip this gem
 6. Cancel installation
> 3
Building native extensions.  This could take a while...
ERROR:  While executing gem ... (Gem::Installer::ExtensionBuildError)
    ERROR: Failed to build gem native extension.

ruby extconf.rb install mysql
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:1


Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/mysql-2.7 for inspection.
Results logged to /usr/lib/ruby/gems/1.8/gems/mysql-2.7/gem_make.out
```

Can someone tell me what is going wrong with the Rubygems? :confused:

What would be the correct steps to follow to install a clean Rails environment?

---

### Post by jimmybondo on 2007-10-26
try installing build-essential:

```
sudo apt-get install build-essential
```

That should install make, which is probably what it is looking for.
Jim

---

### Post by jimmybondo on 2007-10-26
Actually ran into the same problem about 10 seconds after I posted. Make sure to run this command:
```
sudo apt-get install ruby1.8-dev
```
I still recommend the build package for future uses...
Jim

---

### Post by Railsbuntu on 2007-10-27
Hi jimmybondo,

Thanks for your help. I installed the missing software you pointed out, and now here is the new error message:

```
 sudo gem install mysql
Need to update 15 gems from http://gems.rubyforge.org
...............
complete
Select which gem to install for your platform (i486-linux)
 1. mysql 2.7.3 (mswin32)
 2. mysql 2.7.1 (mswin32)
 3. mysql 2.7 (ruby)
 4. mysql 2.6 (ruby)
 5. Skip this gem
 6. Cancel installation
> 3
Building native extensions.  This could take a while...
ERROR:  While executing gem ... (Gem::Installer::ExtensionBuildError)
    ERROR: Failed to build gem native extension.

ruby extconf.rb install mysql
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lm... yes
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lz... no
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lsocket... no
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lnsl... yes
checking for mysql_query() in -lmysqlclient... no
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
        --with-opt-dir
        --without-opt-dir
        --with-opt-include
        --without-opt-include=${opt-dir}/include
        --with-opt-lib
        --without-opt-lib=${opt-dir}/lib
        --with-make-prog
        --without-make-prog
        --srcdir=.
        --curdir
        --ruby=/usr/bin/ruby1.8
        --with-mysql-config
        --without-mysql-config
        --with-mysql-dir
        --without-mysql-dir
        --with-mysql-include
        --without-mysql-include=${mysql-dir}/include
        --with-mysql-lib
        --without-mysql-lib=${mysql-dir}/lib
        --with-mysqlclientlib
        --without-mysqlclientlib
        --with-mlib
        --without-mlib
        --with-mysqlclientlib
        --without-mysqlclientlib
        --with-zlib
        --without-zlib
        --with-mysqlclientlib
        --without-mysqlclientlib
        --with-socketlib
        --without-socketlib
        --with-mysqlclientlib
        --without-mysqlclientlib
        --with-nsllib
        --without-nsllib
        --with-mysqlclientlib
        --without-mysqlclientlib


Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/mysql-2.7 for inspection.
Results logged to /usr/lib/ruby/gems/1.8/gems/mysql-2.7/gem_make.out
```

I am getting mixed up with what I installed and uninstalled then reinstalled. I guess I'd rather reinstall everything from scratch?:confused:

---

### Post by longstockings on 2007-10-27
I've been setting up ruby, rails and mysql by following along with my book and had the same problem trying to install the mysql gem.

The solution is to run this
```
sudo gem install mysql -- --with-mysql-config=/usr/bin/mysql_config
```

---

### Post by Railsbuntu on 2007-10-27
Hi longstocking,

It still doesn't work.

However, I decided to postpone this issue, and to carry on and install Retrospectiva. And well, everything worked fine although this mysql gem still gives trouble.

So I am going to consider for now that the Rails installation is complete and works perfectly :D I will still work on that gem and keep you updated.

---

### Post by dm1024 on 2007-10-28
sudo apt-get install  libmysqlclient-dev

---

### Post by Railsbuntu on 2007-10-29
Hi,

I have also installed RedMine and it worked perfectly. I don't exactly know what this mysql ruby gem is about. But for now I will just drop it, and avoid breaking my now working Railsbuntu box.

Actually the RedMine installation documentation doesn't even talk about the mysql gem.

See you soon :guitar:

---

### Post by kjirstenkoka on 2008-02-12
Alternatively,

sudo apt-get install libmysqlclient15-dev


> **dm1024 said:**
> sudo apt-get install  libmysqlclient-dev

---

