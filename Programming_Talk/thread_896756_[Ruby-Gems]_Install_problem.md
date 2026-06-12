---
title: "[Ruby-Gems] Install problem"
date: 2008-08-21
forum: Programming Talk
---

### Post by samtx on 2008-08-21
Hi,

After searching my *** off for a solution to my problem, I decided to post my problem, maybe someone knows directly what command to run or what setting to edit, I'm very curious...

I followed the Ubuntu tutorial ([https://help.ubuntu.com/community/RubyOnRails#RubyGems%201.2.0](https://help.ubuntu.com/community/RubyOnRails#RubyGems%201.2.0)) to install ruby, gems and rails but got stuck after installing rubygems. It gave me the name-error at first and I fixed it (enough information about that one) and next problem came up. When trying to run a gem command other than gem -v or gem , I get the following error:

```
root@station:/usr/bin/rubygems-1.1.0# gem install rails
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': /usr/lib/ruby/1.8/net/http.rb:2105: syntax error, unexpected $end, expecting '\n' or ';' (SyntaxError)
    def error!
              ^ from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/site_ruby/1.8/rubygems/remote_fetcher.rb:1
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/site_ruby/1.8/rubygems/source_info_cache_entry.rb:3
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/site_ruby/1.8/rubygems/source_info_cache.rb:4
         ... 11 levels...
        from /usr/local/lib/site_ruby/1.8/rubygems/command_manager.rb:103:in `process_args'
        from /usr/local/lib/site_ruby/1.8/rubygems/command_manager.rb:74:in `run'
        from /usr/local/lib/site_ruby/1.8/rubygems/gem_runner.rb:39:in `run'
        from /usr/bin/gem:24
root@station:/usr/bin/rubygems-1.1.0#

```

The problem persists after re-installing ruby and rubygems. I'd really appreciate it if anyone can help me with this or point me in the right direction...

Thanx in advance!

---

### Post by mssever on 2008-08-21
Have you tried the rubygems package in the repos (as opposed to the one from rubyforge)? Also, installing the rubygems package doesn't automatically get you ruby-dev, which you need for some gems.

---

### Post by samtx on 2008-08-21
Thanks for your reply,

I installed using apt-get rubygems and I tried downloading the archive from the rubyforge.net website.

I installed the ruby-full package before downloading rubygems.

And did the install of the ruby1.9-dev package.

But I still get the same error...

---

### Post by samtx on 2008-08-22
It looks like it already produces and error before finishing the installation after running sudo ruby setup.rb

Anyone else a suggestion of what it might be?

---

### Post by mssever on 2008-08-22
> **samtx said:**
> And did the install of the ruby1.9-dev package.
ruby-full gives you Ruby 1.8.6 (currently), including ruby1.8-dev. So installing ruby-1.9-dev doesn't help you.

As far as your problem goes, I really don't know what more to tell you. :(

---

### Post by samtx on 2008-08-22
Pity! Thanks for your advice anyway, I'll try to start from scratch again :)

It's so strange I couldn't find anything more about this error :(

---

### Post by lyceum on 2008-09-10
When I install from RubyForge, it stats gems is not installed. When I install from the apt-get or a package manager, is says error and will not work. ruby 1.8.6 works fine, just not gems. Can anyone help?

---

### Post by mssever on 2008-09-10
> **lyceum said:**
> When I install from RubyForge, it stats gems is not installed. When I install from the apt-get or a package manager, is says error and will not work. ruby 1.8.6 works fine, just not gems. Can anyone help?
Have you installed rubygems? ```
sudo aptitude install rubygems ruby1.8-dev build-essential
```

---

### Post by lyceum on 2008-09-11
> **mssever said:**
> Have you installed rubygems? ```
sudo aptitude install rubygems ruby1.8-dev build-essential
```

Yes, when I do that they do not work at all, I just get an error. The Ruby forums stated that I install from RubyForge to avoid the error.

> 
:~$ RubyGems --version
bash: RubyGems: command not found
:~$ sudo gem install RedCloth
/usr/bin/gem:23: uninitialized constant Gem::GemRunner (NameError)


---

### Post by mssever on 2008-09-11
> **lyceum said:**
> Yes, when I do that they do not work at all, I just get an error. The Ruby forums stated that I install from RubyForge to avoid the error.
I always insall rubygems using aptitude. As far as the RubyGems command goes, that command doesn't exist for me, either, yet rubygems works fine. Are you sure you have all the names spelled right (including capitalization)?

---

### Post by Ruhe on 2008-09-11
I have a long time expirience with rubygems, and I can say, that in 9 of 10 cases installing gems from sources is the best way. I know that installing programs not from apt isn't good, but look:
currently available in apt rubygems version - 0.9.2 (or so).
currently stable version - 1.2

Try to update that 0.9.2 version with "gem update --system" and you'll receive bunch of different errors. Most common - your computer hangs for a while. Apt installs gems to /var/lib/gems, is it good? I think that directory where ruby installed is much better, maybe I'm wrong?

I usually install gems from source. This gives me more control on the system.

And this guide is very good:
[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

---

### Post by lyceum on 2008-09-12
Thank you both. I think I am going to re-install Ruby and gems so I can start fresh.

---

