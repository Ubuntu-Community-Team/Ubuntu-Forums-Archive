---
title: "Error on running irb1.9"
date: 2008-06-26
forum: Programming Talk
---

### Post by jan247 on 2008-06-26
Hi guys. I'm new with Ruby. I have initially installed ruby1.8 and irb1.8. I wanted to try out ruby1.9 and irb1.9. However, irb1.9 won't start stating that it's reading from the 1.8 ruby libraries. Any help would be appreciated. It reads:

```

~$ irb1.9
/usr/lib/ruby/1.8/e2mmap.rb:51:in `<top (required)>': uninitialized constant VERSION (NameError)
	from /usr/lib/ruby/1.8/irb.rb:12:in `require'
	from /usr/lib/ruby/1.8/irb.rb:12:in `<top (required)>'
	from /usr/bin/irb1.9:10:in `require'
	from /usr/bin/irb1.9:10:in `<main>'

```

---

### Post by rye_ on 2008-06-27
I just installed irb1.9 to look for the error and its runs fine on my laptop.  did you let all the required dependencies be installed?

Alternatively, you can try removing 1.8

---

### Post by jan247 on 2008-06-27
I'm afraid that didn't do the trick. After removing ruby1.8 and irb1.8, I was left with the following instead:

```

/usr/lib/ruby/1.8/e2mmap.rb:51:in `<top (required)>': uninitialized constant VERSION (NameError)
	from /usr/lib/ruby/1.9.0/irb.rb:12:in `require'
	from /usr/lib/ruby/1.9.0/irb.rb:12:in `<top (required)>'
	from /usr/bin/irb1.9:10:in `require'
	from /usr/bin/irb1.9:10:in `<main>'

```

---

### Post by jan247 on 2008-06-27
Sorry, it actually did work. I just forgot to remove libruby1.8. Problem is, after I reinstall ruby1.8, The problem comes back.

---

### Post by jan247 on 2008-06-29
anyone?

---

