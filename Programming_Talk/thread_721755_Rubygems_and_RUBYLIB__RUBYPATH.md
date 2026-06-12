---
title: "Rubygems and RUBYLIB / RUBYPATH"
date: 2008-03-11
forum: Programming Talk
---

### Post by shadowfirebird on 2008-03-11
[Gutsy; Ruby 1.8]

Okay, I've installed rubygems twice now, once from Synaptic and once from Rubyforge.  Same problem both times.

The gem command works fine.  I get the gem I am after.  The problem comes when I try to use the thing.  It doesn't know about it.

Now, I've done a 'gem environment' and I know where gem is putting stuff, and it's genuinely there (/usr/lib/ruby/gems/1.8).  So presumably I need to set RUBYLIB to something.  I've tried /usr/lib/ruby/gems, /usr/lib/ruby/gems/1.8, and /usr/lib/ruby/gems/1.8/gems.  But nothing works.

I'm sure I'm just being thick here.  Any ideas, anyone?

---

### Post by Jessehk on 2008-03-11
In a ruby script that requires a rubygem, make sure you

```

require "rubygems"

```

before anything else. That is most likely the cause of your problem.

---

### Post by shadowfirebird on 2008-03-12
Many thanks.  I thought that that was for getting gem to install things automatically that you don't already have.  Apparently not, since that seems to have got me a little further, at least.

It still looks as if I need to set a path, or do something.:
```
andy@Blake:~$ irb
irb(main):001:0> require 'rubygems'
=> true
irb(main):002:0> require 'sqlite3-ruby'
LoadError: no such file to load -- sqlite3-ruby
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from (irb):2

```

I tried this again with RUBYLIB set, but got exactly the same thing.  Plus, does this mean that 'ri' doesn't work on libraries installed via gem?  That's a bit of a bummer.

---

### Post by shadowfirebird on 2008-03-12
I had to look at the code to figure out it was:
```
require 'rubygems'
require 'sqlite3'

```

Many thanks.

---

