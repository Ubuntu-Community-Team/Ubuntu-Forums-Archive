---
title: "[HOW TO] install ruby, rubygems, and railsfrom source"
date: 2007-09-11
forum: Programming Talk
---

### Post by siraf on 2007-09-11
some of the packages in Ubuntu for ruby are screwed up (to put it lightly):

```
/usr/local/lib/ruby/site_ruby/1.8/rubygems/remote_fetcher.rb:4:in `require': no such file to load — zlib (LoadError)
```

So i've written a guide on how to install ruby from scratch

open a terminal

First, download the required pacakges:

```
wget ftp://ftp.ruby-lang.org/pub/ruby/ruby-1.8.6.tar.gz
wget http://rubyforge.org/frs/download.php/20989/rubygems-0.9.4.tgz
```

next, extract the packages to their directories and copy them to /usr/local/src/

```

sudo cp -r ~/ruby-1.8.6 /usr/local/src/
sudo cp -r ~/rubygems-0.9.4 /usr/local/src/

```

okay, here's the tricky part, we're going to configure ruby and use zlib, but first we have to install it:
```

sudo apt-get install zlib*
cd /usr/local/src/ruby-1.8.6/ext/zlib/

```
As root:
```

ruby extconf.rb --with-zlib-include=/usr/include --with-zlib-lib=/usr/lib
make
make install

```

Now it's time for rubygems, we're doing this in parts.
Once again, as root:
```

cd /usr/local/src/rubygems-0.9.4/
ruby setup.rb config
ruby setup.rb setup
ruby setup.rb install

```

Finally we're going to use gems to install rails (or whatever other gems), it's best to start in the home directory for this.
```

cd
sudo gem install rails --with-dependencies

```

I personally had to repeat that last command, but YMMV

I really hope this helps.

---

### Post by Druke on 2007-10-10
Great howto! my only problem was that in order to run the scripts in rubysrcdir/ext/zlib you need to have ruby already installed, so i just installed from the src dir then did the ruby scripts in ext/zlib.

---

