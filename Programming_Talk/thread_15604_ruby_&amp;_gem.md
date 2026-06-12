---
title: "ruby &amp; gem"
date: 2005-02-15
forum: Programming Talk
---

### Post by iant on 2005-02-15
Hello,

a couple of (newbie) ruby related questions that i hope someone here might be able to help with.

1. I was just wondering, has anybody managed to get gem for ruby installed under ubuntu yet?  
if so, would you be able to tell me how you got it to work - i've been sitting here for a good couple of hours trying an install it (such is life) and no luck. 

the error i get is:
  
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:26:in `require': No such file to load -- rubygems/builder (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:58:in `manage_gems'
        from /tmp/rubygems-0.8.4/./post-install.rb:63:in `install_sources'
        from /tmp/rubygems-0.8.4/./post-install.rb:74:in `instance_eval'
        from setup.rb:583:in `instance_eval'
        from setup.rb:583:in `try_run_hook'
        from setup.rb:577:in `run_hook'
        from setup.rb:1315:in `exec_task_traverse'
        from setup.rb:1168:in `exec_install'
        from setup.rb:887:in `exec_install'
        from setup.rb:705:in `invoke'
        from setup.rb:674:in `invoke'
        from setup.rb:1352

(the default 'ruby' seems to be at /usr/local/bin/ruby )

however, if try an install using:
root@ubuntu:/tmp/rubygems-0.8.4 # /usr/bin/ruby setup.rb 

which brings me to my next, hopefully related, question...

2. i seem to 2 versions of ruby installed for some reason:

ian@ubuntu:~ $ whereis ruby
ruby: /usr/bin/ruby /usr/lib/ruby /usr/local/bin/ruby /usr/local/lib/ruby /usr/man/man1/ruby.1
ian@ubuntu:~ $

is this correct? i suspect not.
if not, is there any way i can completely uninstall all ruby packages so i may build ruby from the source?

thanks for the help!

---

### Post by wtd on 2005-02-15
I strongly recommend downloading the latest stable Ruby from [http://www.ruby-lang.org](http://www.ruby-lang.org) and compiling it yourself.  There are some minor oddities in the Ubuntu version that can complicate things.

Also be sure you're running the gem setup.rb with sudo.

---

### Post by iant on 2005-02-17
thanks for the help.  
i've just downloaded and compiled the latest stable as suggested, first removing the old ruby directories and it's working great.  i've got rails up an working too.

cheers!

---

### Post by killercat on 2006-10-16
you must use sudo before your commands.

---

### Post by Woei on 2006-10-16
> **iant said:**
> the error i get is:
  
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:26:in `require': No such file to load -- rubygems/builder (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:58:in `manage_gems'
        from /tmp/rubygems-0.8.4/./post-install.rb:63:in `install_sources'
        from /tmp/rubygems-0.8.4/./post-install.rb:74:in `instance_eval'
        from setup.rb:583:in `instance_eval'
        from setup.rb:583:in `try_run_hook'
        from setup.rb:577:in `run_hook'
        from setup.rb:1315:in `exec_task_traverse'
        from setup.rb:1168:in `exec_install'
        from setup.rb:887:in `exec_install'
        from setup.rb:705:in `invoke'
        from setup.rb:674:in `invoke'
        from setup.rb:1352

(the default 'ruby' seems to be at /usr/local/bin/ruby )

however, if try an install using:
root@ubuntu:/tmp/rubygems-0.8.4 # /usr/bin/ruby setup.rb 

which brings me to my next, hopefully related, question...

2. i seem to 2 versions of ruby installed for some reason:

ian@ubuntu:~ $ whereis ruby
ruby: /usr/bin/ruby /usr/lib/ruby /usr/local/bin/ruby /usr/local/lib/ruby /usr/man/man1/ruby.1
ian@ubuntu:~ $

is this correct? i suspect not.
if not, is there any way i can completely uninstall all ruby packages so i may build ruby from the source?

thanks for the help!

Please read Debian's (and by extension, Ubuntu's) position on using 'gems': [http://pkg-ruby-extras.alioth.debian.org/rubygems.html](http://pkg-ruby-extras.alioth.debian.org/rubygems.html) . It's basically the same as with Perl's CPAN modules: either you go wholesale for Debian's prepackaged (and possibly outdated versions) as managed with dpkg, or you don't use Debian's packages, and install everything yourself. Mixing the two will only get you into problems like you've experienced yourself.

---

### Post by asimon on 2006-10-17
I installed the following ruby packages from Ubuntu's repositories (this is on Edgy, the versions on Dapper are different):
```

$ dpkg -l |grep ruby
ii  libatk1-ruby                               0.15.0-1.1                           ATK bindings for the Ruby language
ii  libcairo-ruby                              1.2.0-1                              Cairo bindings for the Ruby language
ii  libcairo-ruby1.8                           1.2.0-1                              Cairo bindings for the Ruby language
ii  libdbm-ruby                                1.8.2-1                              DBM interface for Ruby
ii  libdbm-ruby1.8                             1.8.4-5ubuntu1                       DBM interface for Ruby 1.8
ii  libgdbm-ruby                               1.8.2-1                              GDBM interface for Ruby
ii  libgdbm-ruby1.8                            1.8.4-5ubuntu1                       GDBM interface for Ruby 1.8
ii  libgdk-pixbuf2-ruby                        0.15.0-1.1                           Gdk-Pixbuf 2 bindings for the Ruby language
ii  libglib2-ruby                              0.15.0-1.1                           Glib 2 bindings for the Ruby language
ii  libgtk2-ruby                               0.15.0-1.1                           GTK+ bindings for the Ruby language
ii  libmysql-ruby                              2.7.1-1                              MySQL module for Ruby
ii  libmysql-ruby1.8                           2.7.1-1                              MySQL module for Ruby 1.8
ii  libopengl-ruby                             0.32f-2ubuntu1                       OpenGL binding for Ruby
ii  libopenssl-ruby                            1.0.0+ruby1.8.2-1                    OpenSSL interface for Ruby
ii  libopenssl-ruby1.8                         1.8.4-5ubuntu1                       OpenSSL interface for Ruby 1.8
ii  libpango1-ruby                             0.15.0-1.1                           Pango bindings for the Ruby language
ii  libqt0-ruby1.8-qt4                         1.4.6-0ubuntu1                       Qt4 bindings for Ruby
ii  libreadline-ruby                           1.8.2-1                              Readline interface for Ruby
ii  libreadline-ruby1.8                        1.8.4-5ubuntu1                       Readline interface for Ruby 1.8
ii  libruby1.8                                 1.8.4-5ubuntu1                       Libraries necessary to run Ruby 1.8
ii  libsqlite3-ruby                            1.1.0-2                              SQLite3 interface for Ruby
ii  libsqlite3-ruby1.8                         1.1.0-2                              SQLite3 interface for Ruby 1.8
ii  libtcltk-ruby                              1.8.2-1                              Tcl/Tk interface for Ruby
ii  libtcltk-ruby1.8                           1.8.4-5ubuntu1                       Tcl/Tk interface for Ruby 1.8
ii  rdoc                                       1.8.2-1                              Generate documentation from ruby source file
ii  ruby                                       1.8.2-1                              An interpreter of object-oriented scripting
ii  ruby1.8                                    1.8.4-5ubuntu1                       Interpreter of object-oriented scripting lan
ii  ruby1.8-dev                                1.8.4-5ubuntu1                       Header files for compiling extension modules
ii  ruby1.8-examples                           1.8.4-5ubuntu1                       Examples for Ruby 1.8

```
Of course you may not want all of those. The most important ones are ruby1.8-dev, rdoc, libreadline-ruby, libopenssl-ruby, libgdbm-ruby, libdbm-ruby.

Then I downloaded rubygems 0.8.11 and installed it via 'sudo ruby setup.rb'. Afterwards I had no problems installing stuff via gem, like for example 'sudo gem install ZenTest'.

Of course if you want to install some gem which builds a native extensions like for example rmagick you'll need the respective header files installed, in the example of rmagick you need libmagick9-dev.

As Woei sayed, installing everything ruby related your own without debian packages may look like a more clean solution. But then you end up playing with equivs to prevend packages like amarok bring with them Ubuntu's ruby and you need to set paths, etc. So far I am happy with having ruby core (and some more) come from Ubuntu and the rest via gem.

---

