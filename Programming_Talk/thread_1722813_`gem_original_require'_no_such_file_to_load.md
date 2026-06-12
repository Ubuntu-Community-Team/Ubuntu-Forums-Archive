---
title: "`gem_original_require': no such file to load"
date: 2011-04-06
forum: Programming Talk
---

### Post by mvmacd on 2011-04-06
**[color=red]edit: I suppose I should have put "Ruby" in the title.. If a mod sees this, can you edit my thread title? Thx![/color]**

hey, I downloaded the ruby script [color=blue][here](http://9seats.com/2011/04/archiving-gmail-chat-logs-with-ruby/)[/color], installed Mechanize, DataMapper and rubygems from synaptic... so I run the script, and I get this error:

```

matt: ~/chat_logs/ruby $ ruby gmail_export.rb 
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require': no such file to load -- dm-core (LoadError)
	from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:36:in `require'
	from gmail_export.rb:8

```

so I even went to rubyforge and downloaded 'rubygems' [1.7.2] and ran the setup.rb as root and I'm pretty sure it ran without errors and said ```
RubyGems installed the following executables:
	/usr/bin/gem1.8
```

I've googled the gem_original_require but I could not get any solution to work! :confused::confused: if someone can help I'd appreciate it  :KS
Matt

---

