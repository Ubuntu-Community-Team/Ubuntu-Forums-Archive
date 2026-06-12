---
title: "Ruby + Builder"
date: 2008-11-19
forum: Programming Talk
---

### Post by Tk0680 on 2008-11-19
I'm trying to use Ruby's Builder gem to produce some XML, but - having installed the gem apparently fine (builder.rb is there, no errors other than a documentation issue, which is apparently common) - it flatly refuses to run.

Google hasn't turned anything up to give me any hints here - can anyone else shed any light?

```
$ ruby -v
ruby 1.8.7 (2008-08-11 patchlevel 72) [i486-linux]

```

```
>> require 'rubygems/builder'
NameError: uninitialized constant Gem::Builder::UserInteraction
	from /usr/lib/ruby/1.8/rubygems/builder.rb:15
	from (irb):1:in `require'
	from (irb):1

```

---

