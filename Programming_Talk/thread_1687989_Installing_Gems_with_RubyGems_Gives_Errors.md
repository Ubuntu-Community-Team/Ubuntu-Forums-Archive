---
title: "Installing Gems with RubyGems Gives Errors"
date: 2011-02-14
forum: Programming Talk
---

### Post by ryuurei on 2011-02-14
Hello there.
I have recently been learning the Ruby language as another skill to add to my toolbox. I have been trying to get gems to work for a while now but have been presented with the following:
```
$ sudo gem install rails
ERROR:  Loading command: install (LoadError)
    no such file to load -- zlib
ERROR:  While executing gem ... (NameError)
    uninitialized constant Gem::Commands::InstallCommand

```
for instance.

I have tried several things.
First, I tried to download the zlib-ruby project file but the site was down. See [http://www.blue.sky.or.jp/atelier/ruby/ruby-zlib-0.6.0.tar.gz.]("http://www.blue.sky.or.jp/atelier/ruby/ruby-zlib-0.6.0.tar.gz")
Second, I tried going to [ruby_dir]/ext/zlib and running
```

ruby extconf.rb
checking for deflateReset() in -lz... no
checking for deflateReset() in -llibz... no
checking for deflateReset() in -lzlib1... no
checking for deflateReset() in -lzlib... no
checking for deflateReset() in -lzdll... no

```
Finally, I was going to try
```

rvm package install zlib
rvm remove 1.9.2
rvm install 1.9.2 -C --with-zlib-dir=$rvm_path/usr

```
but I got
```

rvm package install zlib
No command 'rvm' found, but there are 20 similar ones
rvm: command not found

```
I did try installing rvm with the command
```

bash < <( curl http://rvm.beginrescueend.com/releases/rvm-install-head )

```
found on [http://rvm.beginrescueend.com/](http://rvm.beginrescueend.com/)
but I still get the exact same error as mentioned above.

I am working with Ruby 1.9.2. I compiled it from the source I downloaded from the official Ruby website. I am running Maverick. I did install Ruby before rvm and such. When I run gem I get:
```

gem
RubyGems is a sophisticated package manager for Ruby.  This is a
basic help message containing pointers to more information.

  Usage:
    gem -h/--help
    gem -v/--version
    gem command [arguments...] [options...]

  Examples:
    gem install rake
    gem list --local
    gem build package.gemspec
    gem help install

  Further help:
    gem help commands            list all 'gem' commands
    gem help examples            show some examples of usage
    gem help platforms           show information about platforms
    gem help <COMMAND>           show help on COMMAND
                                   (e.g. 'gem help install')
    gem server                   present a web page at
                                 http://localhost:8808/
                                 with info about installed gems
  Further information:
    http://rubygems.rubyforge.org

```

Any help is greatly appreciated.
[]("http://www.blue.sky.or.jp/atelier/ruby/ruby-zlib-0.6.0.tar.gz")

---

### Post by ryuurei on 2011-02-15
This problem is now solved.
After searching around using
```

apt-cache search zlib

```
I found a package upon installing of which removed my problem with zlib at last.
I had to do the following:
```

$ sudo apt-get install libghc6-zlib-dev

```

Hope this helps somebody.

---

### Post by josiasds on 2012-06-05
Actually, it helps a lot.

---

