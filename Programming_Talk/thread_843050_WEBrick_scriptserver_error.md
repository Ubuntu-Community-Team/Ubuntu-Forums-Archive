---
title: "WEBrick script/server error"
date: 2008-06-27
forum: Programming Talk
---

### Post by mcbgun on 2008-06-27
The following happens when I enter script/server:

=> Booting WEBrick...
/usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/initializer.rb:225:in `require_frameworks': no such file to load -- openssl (RuntimeError)
	from /usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/initializer.rb:113:in `process'
	from /usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/initializer.rb:93:in `send'
	from /usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/initializer.rb:93:in `run'
	from /home/marc/Projects/emporium/config/environment.rb:13
	from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
	from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
	from /usr/local/lib/ruby/gems/1.8/gems/activesupport-2.1.0/lib/active_support/dependencies.rb:509:in `require'
	from /usr/local/lib/ruby/gems/1.8/gems/activesupport-2.1.0/lib/active_support/dependencies.rb:354:in `new_constants_in'
	from /usr/local/lib/ruby/gems/1.8/gems/activesupport-2.1.0/lib/active_support/dependencies.rb:509:in `require'
	from /usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/commands/servers/webrick.rb:59
	from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
	from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
	from /usr/local/lib/ruby/gems/1.8/gems/activesupport-2.1.0/lib/active_support/dependencies.rb:509:in `require'
	from /usr/local/lib/ruby/gems/1.8/gems/activesupport-2.1.0/lib/active_support/dependencies.rb:354:in `new_constants_in'
	from /usr/local/lib/ruby/gems/1.8/gems/activesupport-2.1.0/lib/active_support/dependencies.rb:509:in `require'
	from /usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/commands/server.rb:39
	from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
	from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
	from script/server:3


LOL no idea what this means. Had a quick look on the net. Made sure I installed the full ruby package using synaptic package manager.

I'm a total noob with both rails and linux which is why i'm following a rails book to the letter however this problem has arose.

PLEASE HELP!!

---

### Post by rye_ on 2008-06-28
Edit:

---

### Post by mcbgun on 2008-06-28
Sorry but I don't understand? 

I've tried every method I can to install and run it. I still get the same SSL error. 

Has anyone got any ideas??

---

### Post by rye_ on 2008-06-28
try this.

sudo apt-get install libopenssl-ruby

---

### Post by rye_ on 2008-06-28
also. 

how did you install rails?
I ask because I don't have any such errors and I installed rubygems via source (not via synaptic) and using rubygems I then installed rails.
This also allows you to control the version of rails installed since ubuntu 8.04 has rails 2.0 in the repos and I suspect the book you use uses rails 1.2.x?

sudo gem install rails -v '<2.0'

---

### Post by doll on 2008-07-10
I am having a similar error. 

I am working on Fedora core 6.

ruby script/generate controller App
/usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/initializer.rb:225:in `require_frameworks': no such file to load -- openssl (RuntimeError)
        from /usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/initializer.rb:113:in `process'
        from /usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/initializer.rb:93:in `send'
        from /usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/initializer.rb:93:in `run'
        from /home/videodoll/rubydev/hello/config/environment.rb:13
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/gems/1.8/gems/rails-2.1.0/lib/commands/generate.rb:1
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from script/generate:3

We must be reading the same book. I had a ton of problems getting rubygems to install and work properly. Now that it is finally working and I was able to get rails installed, I have this new problem.

Did you ever figure out what to do to fix this?

---

### Post by doll on 2008-07-10
I just searched around a bit more and I found the fix.

This is taken from: 
[http://www.ruby-forum.com/topic/90083](http://www.ruby-forum.com/topic/90083)

Go into your Ruby install folder. Go into the folder called ext/openssl

> ruby extconf.rb
> make
> make install

Hope it helps anyone else who has this problem.

---

