---
title: "installing ruby, gems on Ubuntu Gutsy 7.10"
date: 2008-03-05
forum: Programming Talk
---

### Post by Robert Citek on 2008-03-05
Thought I would post my notes on how I installed Ruby and Gems on Ubuntu Gutsy 7.10

```
sudo apt-get install ruby ruby1.8-examples rdoc ri libruby-extras rubygems

sudo ruby  -i.bak \
 -lne 'print "require \047rubygems/gem_runner\047" \
 if /^require /; print' /usr/bin/gem

sudo gem update --system

```

```
$ ruby -v
ruby 1.8.6 (2007-06-07 patchlevel 36) [i486-linux]

$ gem -v
1.0.1

```

Thanks to these posts on the web:

[http://www.ruby-forum.com/topic/136806#608707](http://www.ruby-forum.com/topic/136806#608707)

[http://www.nickpeters.net/2007/12/31/fix-for-uninitialized-constant-gemgemrunner-nameerror/](http://www.nickpeters.net/2007/12/31/fix-for-uninitialized-constant-gemgemrunner-nameerror/)

Regards,
- Robert

---

### Post by rye_ on 2008-03-06
Here's how I did it (It works falwlessly)

1. Install ruby on Ubuntu

```
sudo apt-get install ruby rdoc irb libyaml-ruby libzlib-ruby ri libopenssl-ruby 
```

2. Install RubyGems via Source
Note: Use source (.tar etc) rather than synaptic.  Synaptic will complain about changes made to rubygems from within rubygems.  I.e. rubygems is a package manager.
wget [http://rubyforge.org/frs/download.php/29548/rubygems-1.0.1.tgz](http://rubyforge.org/frs/download.php/29548/rubygems-1.0.1.tgz) 
```

	tar xzvf rubygems-1.0.1.tgz
	cd rubygems-1.0.1
	sudo ruby setup.rb
	sudo ln -s /usr/bin/gem1.8 /usr/bin/gem
	sudo gem update --system

```
3.Install Rails (to latest stable)
```
sudo gem install rails -y
``` 

Ryan

---

