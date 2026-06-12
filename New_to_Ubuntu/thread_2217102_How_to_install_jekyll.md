---
title: "How to install jekyll"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by Niels_Rasmussen on 2014-04-15
Hi all,

how do i install jekyll the right way?

[http://jekyllrb.com/](http://jekyllrb.com/)

No matter what I do it comes up with a lot of error messages.

It's driving me insane!! Apparantly the jekyll build from the repos is deprecated. I also tried to:
```
sudo gem install jekyll
```

That doesnt help either!!

Right now I have:
```

niels@ThinkLinux ~ $ dpkg --get-selections | grep ruby
libruby                         install
libruby1.8                    install
libruby1.9.1                    install
libruby1.9.1-dbg                install
ruby                        install
ruby-albino                    install
ruby-classifier                    install
ruby-coderay                    install
ruby-directory-watcher                install
ruby-fast-stemmer                install
ruby-kramdown                    install
ruby-liquid                    install
ruby-maruku                    install
ruby-posix-spawn                install
ruby1.8                        deinstall
ruby1.8-dev                    install
ruby1.9.1                    install
ruby1.9.1-dev                    install
ruby1.9.1-examples                install
ruby1.9.1-full                    install
rubygems                    deinstall 

```

And this is the output from jekyll server:
```

niels@ThinkLinux ~/jekyll-sites $ jekyll server
/usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': iconv will be deprecated in the future, use String#encode instead.
Configuration from /home/niels/jekyll-sites/_config.yml
Building site: /home/niels/jekyll-sites -> server
/home/niels/jekyll-sites/_plugins/rssgenerator.rb:54:in `block (3 levels) in generate': undefined method `title' for <Post: /2014/03/29/Transition>:Jekyll::Post (NoMethodError)
    from /usr/lib/ruby/1.9.1/rss/maker/base.rb:57:in `new_item'
    from /home/niels/jekyll-sites/_plugins/rssgenerator.rb:51:in `block (2 levels) in generate'
    from /home/niels/jekyll-sites/_plugins/rssgenerator.rb:49:in `each'
    from /home/niels/jekyll-sites/_plugins/rssgenerator.rb:49:in `block in generate'
    from /usr/lib/ruby/1.9.1/rss/maker/base.rb:438:in `make'
    from /usr/lib/ruby/1.9.1/rss/maker/base.rb:402:in `make'
    from /usr/lib/ruby/1.9.1/rss/maker.rb:9:in `make'
    from /home/niels/jekyll-sites/_plugins/rssgenerator.rb:39:in `generate'
    from /usr/lib/ruby/vendor_ruby/jekyll/site.rb:184:in `block in generate'
    from /usr/lib/ruby/vendor_ruby/jekyll/site.rb:183:in `each'
    from /usr/lib/ruby/vendor_ruby/jekyll/site.rb:183:in `generate'
    from /usr/lib/ruby/vendor_ruby/jekyll/site.rb:39:in `process'
    from /usr/bin/jekyll:250:in `<main>'
```

I tried to remove the rssgenerator.rb plugin, but of course that didnt help either.

How did YOU install jekyll??

/Niels

---

### Post by Niels_Rasmussen on 2014-04-15
Never mind got it sorted :-)

---

### Post by Vladlenin5000 on 2014-04-15
> **Niels_Rasmussen said:**
> Never mind got it sorted :-)

Nice :)

Now there are two things you should do: First of all post here HOW did you solve it as it might be useful for other users. And secondly, use the thread tools to mark this one as "solved".

---

