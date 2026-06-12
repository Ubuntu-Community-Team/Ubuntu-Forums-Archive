---
title: "How-To Install Ruby 1.9 and Ruby Gems into Ubuntu"
date: 2010-08-02
forum: Programming Talk
---

### Post by lindsay_keir on 2010-08-02
How to get Ruby 1.9 and Gems working under Ubuntu drove me bonkers ( *"bonk" is the sound you get when hitting your head against a wall*).  I have nothing against the Debian philosophy, nothing against the Ruby philosophy, nothing against the Gems philosophy - **SEPARATLY!**; but they do **NOT** play well together. Ah well ...

**DISCLAIMER:** I wrote this as I was doing the install; but I had to back-track so many times I cannot guarantee these steps are perfect. Also, as part of my WTF process I wiped out all other versions of Ruby, etc. ... *and I'm sure this is going to come back and bite me.*

```
sudo -i  # Go root

aptitude install ruby1.9.1 irb1.9.1 ruby-dev1.9.1 rdoc1.9.1 rubygems1.9.1

cd /usr/bin
ln -s ruby1.9.1 ruby
ln -s irb1.9.1 irb
ln -s rdoc1.9.1 rdoc
ln -s rubygems1.9.1 rubygems
```
***and Check ***
```
**ls -l ruby irb rdoc rubygems gem**
[I]lrwxrwxrwx 1 root root 21 2010-07-31 01:22 gem -> /etc/alternatives/gem
lrwxrwxrwx 1 root root  8 2010-07-31 01:26 irb -> irb1.9.1
lrwxrwxrwx 1 root root  9 2010-07-31 01:26 rdoc -> rdoc1.9.1
lrwxrwxrwx 1 root root  9 2010-07-31 01:26 ruby -> ruby1.9.1
lrwxrwxrwx 1 root root 13 2010-07-31 01:35 rubygems -> rubygems1.9.1[/I]

```

* Debian apt-get install uses INSTALLATION DIRECTORY: /var/lib/gems/1.9.1
* Rubygems       install uses   INSTALLATION DIRECTORY: /usr/lib/ruby/gems/1.9.1
**VIP! READ!** The Debian directories are "deflected" to the Rubygems directories. I could have done this the other way around, but didn't.

**Rename the Debian directories to *.orig - (just because).**

```

cd /var/lib/gems/1.9.1
mv cache         cache.orig
mv doc            doc.orig
mv gems           gems.orig
mv specifications specifications.orig

```

**Link from Debian (/var/lib/gems/1.9.1) to Rubygems (/usr/lib/ruby/gems/1.9.1)**

```

ln -s  /usr/lib/ruby/gems/1.9.1/cache /var/lib/gems/1.9.1
ln -s  /usr/lib/ruby/gems/1.9.1/doc /var/lib/gems/1.9.1
ln -s  /usr/lib/ruby/gems/1.9.1/gems /var/lib/gems/1.9.1
ln -s  /usr/lib/ruby/gems/1.9.1/specifications /var/lib/gems/1.9.1

```
***and Check ***
```
**ls -l /usr/lib/ruby/gems/1.9.1**
[I]lrwxrwxrwx 1 root root   30 2010-07-31 16:57 cache -> /usr/lib/ruby/gems/1.9.1/cache
drwxr-xr-x 2 root root 4096 2010-02-03 13:13 cache.orig
lrwxrwxrwx 1 root root   28 2010-07-31 16:58 doc -> /usr/lib/ruby/gems/1.9.1/doc
drwxr-xr-x 2 root root 4096 2010-02-03 13:13 doc.orig
lrwxrwxrwx 1 root root   29 2010-07-31 16:58 gems -> /usr/lib/ruby/gems/1.9.1/gems
drwxr-xr-x 2 root root 4096 2010-02-03 13:13 gems.orig
lrwxrwxrwx 1 root root   39 2010-07-31 16:58 specifications -> /usr/lib/ruby/gems/1.9.1/specifications
drwxr-xr-x 2 root root 4096 2010-02-03 13:13 specifications.orig[/I]

```

**Update gems to the latest and install some for checking ...**
```

gem update --system
gem install rubygems-update facets hpricot net-ssh openurl

```
* **hpricot** because it does a make using the ruby-dev headers.
* **facets**  because it's "handy" ...  [http://facets.rubyforge.org/](http://facets.rubyforge.org/)

***and Check ***
```

**gem list**
[I]*** LOCAL GEMS ***
facets (2.8.4)
hpricot (0.8.2)
net-ssh (2.0.23)
openurl (0.1.0)
rubygems-update (1.3.7)[/I]

```
**You can go and look at the (r)doc-umentation if you want to...**
```

gem server # ***IN A NEW TERMINAL WINDOW***

```
[http://localhost:8808/](http://localhost:8808/)

**Finally, make a test program somewhere** ... I used home/test/rcheck.rb
[php]
#!/usr/bin/env ruby1.9.1
sw = require 'rubygems'
puts  sw.inspect + ' rubygems'
sw = require 'facets'  # which is a rubygem
puts  sw.inspect + ' facets'
sw = require 'yaml'  # which is NOT a rubygem
puts  sw.inspect + ' yaml'
sw = require 'hpricot'  # which is a rubygem complied with ruby-dev headers
puts  sw.inspect + ' hpricot'
[/php]
```

chmod a+x /home/test/rcheck.rb **# make executable**
/home/test/rcheck.rb **# and try (w/o using the ruby execute)**

```
***and Check * ... All of the requires should and must return "true"**

---

### Post by jdonnell on 2010-08-21
The best way to install various versions of ruby is [rvm]("http://rvm.beginrescueend.com/")

---

### Post by grick on 2010-12-05
> **lindsay_keir said:**
> 


```
**ls -l /usr/lib/ruby/gems/1.9.1**
[I]lrwxrwxrwx 1 root root   30 2010-07-31 16:57 cache -> /usr/lib/ruby/gems/1.9.1/cache
drwxr-xr-x 2 root root 4096 2010-02-03 13:13 cache.orig
lrwxrwxrwx 1 root root   28 2010-07-31 16:58 doc -> /usr/lib/ruby/gems/1.9.1/doc
drwxr-xr-x 2 root root 4096 2010-02-03 13:13 doc.orig
lrwxrwxrwx 1 root root   29 2010-07-31 16:58 gems -> /usr/lib/ruby/gems/1.9.1/gems
drwxr-xr-x 2 root root 4096 2010-02-03 13:13 gems.orig
lrwxrwxrwx 1 root root   39 2010-07-31 16:58 specifications -> /usr/lib/ruby/gems/1.9.1/specifications
drwxr-xr-x 2 root root 4096 2010-02-03 13:13 specifications.orig[/I]

```


Thanks for your share, but i think in this part the command should be "**ls -l /var/lib/gems/1.9.1**"

---

