---
title: "Help my ruby (script/console) work"
date: 2007-09-09
forum: Programming Talk
---

### Post by tefflox on 2007-09-09
I don't get that sinking "here comes a three hour headache" anymore when something like this happens . . .

```

jess@linux:~/rails_space$ ruby script/console
Loading development environment.
/usr/local/lib/ruby/1.8/irb/completion.rb:10:in `require': no such file to load -- readline (LoadError)
        from /usr/local/lib/ruby/1.8/irb/completion.rb:10
        from /usr/local/lib/ruby/1.8/irb/init.rb:252:in `require'
        from /usr/local/lib/ruby/1.8/irb/init.rb:252:in `load_modules'
        from /usr/local/lib/ruby/1.8/irb/init.rb:250:in `each'
        from /usr/local/lib/ruby/1.8/irb/init.rb:250:in `load_modules'
        from /usr/local/lib/ruby/1.8/irb/init.rb:21:in `setup'
        from /usr/local/lib/ruby/1.8/irb.rb:54:in `start'
        from /usr/local/bin/irb:13
jess@linux:~/rails_space$ 

```

How do I fix this?

Also, anyone wanna help out with my idea?  Right now it only hurts, can often be painful, but I would need some real help to make it "killer."

Come help me prizefight facebook.  (Yes, on a deferred payment plan :-)

(Craigslist doesn't like jobs offered on deferred payment... I hope ubuntu forums doesn't mind.)

(we even have a project mgmt site.)

[http://denacht.blogspot.com](http://denacht.blogspot.com)

---

### Post by winch on 2007-09-09
Try installing libreadline-ruby package.

---

### Post by tefflox on 2007-09-09
still nothing, after installing libreadline-ruby . . .

---

### Post by tefflox on 2007-09-09
SOLVED

```

after installing libreadline-ruby (i guess)

cd path_to/ruby_source/ext/readline
ruby extconf.rb
make
sudo make install

```

---

