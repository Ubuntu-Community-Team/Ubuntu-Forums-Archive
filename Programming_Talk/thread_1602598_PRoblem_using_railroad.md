---
title: "PRoblem using railroad"
date: 2010-10-21
forum: Programming Talk
---

### Post by Blackbug on 2010-10-21
I am trying to create class diagrams of my application using railroad but i am getting following error:
I am trying to create class diagram using railroad but getting error:

Error loading application environment.
  (Are you running railroad on the aplication's root directory?)

/usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require': no such file to load -- config/environment (LoadError)
	from /usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `require'
	from /home/ubuntu/.gem/ruby/1.8/gems/railroad-0.5.0/lib/railroad/app_diagram.rb:73:in `load_environment'
	from /home/ubuntu/.gem/ruby/1.8/gems/railroad-0.5.0/lib/railroad/app_diagram.rb:18:in `initialize'
	from /home/ubuntu/.gem/ruby/1.8/gems/railroad-0.5.0/lib/railroad/models_diagram.rb:14:in `initialize'
	from /home/ubuntu/.gem/ruby/1.8/gems/railroad-0.5.0/bin/railroad:36:in `new'
	from /home/ubuntu/.gem/ruby/1.8/gems/railroad-0.5.0/bin/railroad:36
	from /home/ubuntu/.gem/ruby/1.8/bin/railroad:19:in `load'
	from /home/ubuntu/.gem/ruby/1.8/bin/railroad:19



any clue?
any clue?

---

