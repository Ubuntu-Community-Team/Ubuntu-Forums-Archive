---
title: "Ruby gem, problem with installing rmagick"
date: 2006-09-17
forum: Programming Talk
---

### Post by mdurham on 2006-09-17
Hi, I have this problem when trying to install 'rmagick' with gem.
Any clues as to what the problem could be? or more to the point, how to fix it?
I thought that a gem contained everything necessary to install it's self.
Thanks, Mike

> mike@station1:~$ sudo gem install -r rmagick
Bulk updating Gem source index for: [http://gems.rubyforge.org](http://gems.rubyforge.org)
Building native extensions.  This could take a while...
configure: error: Can't install RMagick. Can't find Magick-config or GraphicsMagick-config program.

ERROR:  While executing gem ... (RuntimeError)
    ERROR: Failed to build gem native extension.
Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/rmagick-1.13.0 for inspection.


Results logged to /usr/lib/ruby/gems/1.8/gems/rmagick-1.13.0/gem_make.out


---

### Post by revlob on 2006-10-31
I was given the same error message the first time I tried to install rmagick. I did a bit of research, and came across:

[http://blog.pomozov.info/posts/adventure-with-rmagick-and-mongrel.html](http://blog.pomozov.info/posts/adventure-with-rmagick-and-mongrel.html)

It mentions you need to install the magick development library package first. I tried to install libmagick6-dev as suggested, however apt said libmagick9-dev replaced it so I installed that instead.

That fixed the error for me, but I still can't install rmagick because something's still not right. During the Gem install, Ruby begins to eat my CPU, and it eventually falls over and gives "broken pipe" errors.

Gem... it kinda sucks.

I'll have a further probe, see if I can work out what's going on, but I thought I'd bump this thread and see if anyone had run into the same problem.

---

### Post by revlob on 2006-11-01
Ok, so various ruby packages in Edgy were updated very recently. I tried installing the rmagick gem again...

```
sudo gem install rmagick
```

...but it spits out the same error I've been getting. Backpeddling, I uninstall libmagick9-dev:

```
sudo apt-get remove --purge libmagick9-dev
```

Following that, I try to install the rmagick gem again, and it works! Not even going to try working out why.

---

