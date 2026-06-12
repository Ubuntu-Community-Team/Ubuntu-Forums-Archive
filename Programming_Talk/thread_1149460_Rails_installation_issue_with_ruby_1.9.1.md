---
title: "Rails installation issue with ruby 1.9.1"
date: 2009-05-05
forum: Programming Talk
---

### Post by aliov_85 on 2009-05-05
I've installed( Ubuntu 9.04-Jaunty Jackalope) ruby 1.9.1 according to [http://u.nu/6674]("http://u.nu/6674") from source.

Know I've issues for installing rails. When execute the following command, 

> sudo gem install rails --no-rdoc --no-ri

I get:

> /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/package.rb:10:in `require': no such file to load -- zlib (LoadError)
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/package.rb:10:in `<top (required)>'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/format.rb:9:in `require'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/format.rb:9:in `<top (required)>'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/installer.rb:11:in `require'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/installer.rb:11:in `<top (required)>'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/dependency_installer.rb:3:in `require'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/dependency_installer.rb:3:in `<top (required)>'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/commands/install_command.rb:4:in `require'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/commands/install_command.rb:4:in `<top (required)>'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/command_manager.rb:167:in `require'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/command_manager.rb:167:in `rescue in load_and_instantiate'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/command_manager.rb:159:in `load_and_instantiate'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/command_manager.rb:88:in `[]'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/command_manager.rb:144:in `find_command'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/command_manager.rb:131:in `process_args'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/command_manager.rb:102:in `run'
	from /usr/local/lib/ruby/site_ruby/1.9.1/rubygems/gem_runner.rb:58:in `run'
	from /usr/local/bin/gem:21:in `<main>'


best regards

---

### Post by jk.cheng on 2009-05-29
Do you have any previous version on Ruby on your box? Try this:
ruby -v
ruby1.9 -v

If same then check your /usr/local directory and check the existence of the required file and folder.

---

### Post by trivialpackets on 2009-05-29
I know I'm not much help, I stayed with 1.8.7 as I know it works and all libraries are ported for it.  I'm not a quick jumper in a lot of things.  I figure in 6 months with the next Ubuntu iteration, I may be ready to jump.

Although, you may want to try to ```
sudo apt-get install libzlib-ruby build-essential
```You probably already have build-essential, but that may be useful as I always install it when I set up ruby and rails.

---

