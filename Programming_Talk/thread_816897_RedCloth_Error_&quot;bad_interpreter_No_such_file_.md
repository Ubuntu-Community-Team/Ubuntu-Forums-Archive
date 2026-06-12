---
title: "RedCloth Error?: &quot;bad interpreter: No such file or directory&quot;"
date: 2008-06-03
forum: Programming Talk
---

### Post by Nitroadict on 2008-06-03
Okay.

I'm very new at programming (only read half of Pine's "Learn to Program" via Ruby new), so I apologize if my problem makes anyone reach for some Advil.

I tried installing RedCloth, and after supposedly doing everything right (installing ruby, ruby gems, & dependencies), I finally go into terminal and try typing :

$ redcloth

to start it up, but I keep getting the following:

bash: /usr/bin/redcloth: /usr/bin/ruby18: bad interpreter: No such file or directory

I've tried Googling, but most of what pops up is Ruby talk that I'm afraid is beyond my current ability to decipher. 

I'm probably just not using it right, but I have no clue what I'm doing wrong either.

Thanks.

---

### Post by stevescripts on 2008-06-03
This might help:

[http://whytheluckystiff.net/ruby/redcloth/]("http://whytheluckystiff.net/ruby/redcloth/")

Steve

---

### Post by Nitroadict on 2008-06-03
I've already tried that page, although I think I fudged my original post a bit concerning my problem.

In addition to that error, RedCloth *seems* to install perfectly fine (sudo gem install redcloth gives me "redcloth etc. etc. installed").

HOWEVER, I can't seem to able to start it up in order to use it.  Right now, it seems like I've installed RedCloth, but I have no idea how to start RedCloth.  

If anyone can help me out on how to actually start up redcloth, that would help a lot.

I suppose this might've been more of a "how to use a ruby gem" problem, though.

---

### Post by stevescripts on 2008-06-04
Quickly - something like this:

```

steveo@delldesktop:~/Desktop/RedCloth-3.0.4/bin$ irb
irb(main):001:0> require 'redcloth'
=> true
irb(main):002:0> r = RedCloth.new "*strong text* and _emphasized text_"
=> "*strong text* and _emphasized text_"
irb(main):003:0> r.to_html
=> "<p><strong>strong text</strong> and <em>emphasized text</em></p>"

```

Hope this helps.

Steve
(no time now for something better - will try to find time soon)

---

### Post by Nitroadict on 2008-06-05
Thanks a lot for the reply; the above didn't work for me, surprisingly. 

This is what I got instead: 

```
irb(main):001:0> require 'redcloth'
=> true
irb(main):002:0> r=Redcloth.new "*strong text* and _emphasized text_"
NameError: uninitialized constant Redcloth
	from (irb):2
irb(main):003:0> r = Redcloth.new "*strong text* and _emphasized text_"
NameError: uninitialized constant Redcloth
	from (irb):3
irb(main):004:0> r.to_html
NoMethodError: undefined method `to_html' for nil:NilClass
	from (irb):4
irb(main):005:0> 

```


I'm still a bit confused, but at least this error is more specific than the last, it appears?

---

### Post by stevescripts on 2008-06-05
duh ... 

Redcloth != RedCloth ...

Steve ;)

---

### Post by Nitroadict on 2008-06-05
I deeply apologize for that.  Trying it again with correct spelling this time :oops:


*Edit:  Excellent, the above seems to work.  



Thanks a lot, I'm happy to see I won't be procrastinating using ruby any further.

As for redcloth, you wouldn't know how to export something like the above into an html file, would you? 

Although, I suppose at this point it's up to me and Google :).

---

### Post by stevescripts on 2008-06-05
apology unnecessary ... the is nobody here who hasn't made the same sort of mistake...

No time to help further right now, maybe later

Steve

---

### Post by stevescripts on 2008-06-05
This should help: [http://faq.rubygarden.org/entry/show/87?controller_prefix=faq%2F]("http://faq.rubygarden.org/entry/show/87?controller_prefix=faq%2F")

```

irb(main):001:0> require 'redcloth'
=> true
irb(main):002:0> r = RedCloth.new "*strong text* and _emphasized text_"
=> "*strong text* and _emphasized text_"
irb(main):003:0> res = r.to_html
=> "<p><strong>strong text</strong> and <em>emphasized text</em></p>"
irb(main):004:0> myfile = open('test.html', 'w')
=> #<File:test.html>
irb(main):005:0> myfile.print(res)
=> nil
irb(main):006:0> myfile.close
=> nil
irb(main):007:0> exit

```

Hope this helps.

Steve

---

### Post by Nitroadict on 2008-06-05
Excellent, now I can learn Ruby while doing something immediately useful.  Thanks again! :)

---

### Post by stevescripts on 2008-06-06
My Pleasure !

Steve
(BTW, I had not heard of RedCloth prior to your post - it appears that it may be
quite useful, so, Thanks to you too!)

---

