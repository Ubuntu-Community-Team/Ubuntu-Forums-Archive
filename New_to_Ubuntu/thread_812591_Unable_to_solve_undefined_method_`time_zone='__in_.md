---
title: "Unable to solve undefined method `time_zone='  in Ruby on Rails install"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Milo82 on 2008-05-30
I finally just went ahead and generated a new project with Rails 2.0.2 and took its environment file. This may cause issues later, but for now its working again, which is enough at the moment.


--- Original -----

I have just updated to 8.04 and am now encountering problems with my Ruby on Rails install(Eclipse/Aptana/RadRails as well, but hopefully I'll be able to fix that later). After updating Ubuntu I also updated to Ruby 1.8.6 and after first getting the error below I also reinstalled rubygems from source. The error I am getting happens when running "ruby script/server start." 

```
name@ubuntu:~/directory/$ ruby script/server start
=> Booting Mongrel (use 'script/server webrick' to force WEBrick)
=> Rails application starting on http://0.0.0.0:3000
=> Call with -d to detach
=> Ctrl-C to shutdown server
** Starting Mongrel listening at 0.0.0.0:3000
** Starting Rails with development environment...
Exiting
/home/name/directory/project_name/config/environment.rb:44: undefined method `time_zone=' for #<Rails::Configuration:0xb78e47a4> (NoMethodError)
	from /usr/lib/ruby/gems/1.8/gems/rails-2.0.2/lib/initializer.rb:47:in `run'
	from /home/name/directory/project_name/config/environment.rb:13
	from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
	from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
	from /usr/lib/ruby/gems/1.8/gems/activesupport-2.0.2/lib/active_support/dependencies.rb:496:in `require'
	from /usr/lib/ruby/gems/1.8/gems/activesupport-2.0.2/lib/active_support/dependencies.rb:342:in `new_constants_in'
	from /usr/lib/ruby/gems/1.8/gems/activesupport-2.0.2/lib/active_support/dependencies.rb:496:in `require'
	from /usr/lib/ruby/gems/1.8/gems/mongrel-1.1.5/bin/../lib/mongrel/rails.rb:147:in `rails'
	 ... 20 levels...
	from /usr/lib/ruby/gems/1.8/gems/rails-2.0.2/lib/commands/server.rb:39
	from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
	from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
	from script/server:3

```

Output from "gem env"

```
  - RUBYGEMS VERSION: 1.1.1
  - RUBY VERSION: 1.8.6 (2007-09-24 patchlevel 111) [i486-linux]
  - INSTALLATION DIRECTORY: /usr/lib/ruby/gems/1.8
  - RUBY EXECUTABLE: /usr/bin/ruby1.8
  - RUBYGEMS PLATFORMS:
    - ruby
    - x86-linux
  - GEM PATHS:
     - /usr/lib/ruby/gems/1.8
  - GEM CONFIGURATION:
     - :update_sources => true
     - :verbose => true
     - :benchmark => false
     - :backtrace => false
     - :bulk_threshold => 1000
     - :sources => ["http://gems.rubyforge.org"]
  - REMOTE SOURCES:
     - http://gems.rubyforge.org

```

"gem env gempath" returns

```
/usr/lib/ruby/gems/1.8

```

Almost all of the help I found searching online was for Mac users, and it didn't help much. Its now been almost a week since I have been able to work on my rails project and I'm desperate to get this working so I can get back to it. 

Thank you for any help you can provide.

---

