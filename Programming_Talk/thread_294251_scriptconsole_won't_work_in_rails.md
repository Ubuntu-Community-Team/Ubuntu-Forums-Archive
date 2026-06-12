---
title: "script/console won't work in rails"
date: 2006-11-06
forum: Programming Talk
---

### Post by daz4126 on 2006-11-06
Hi,

When I run the script/console command in a rails application, instead of launching irb, I get the following error message:

/usr/lib/ruby/gems/1.8/gems/rails-1.1.2/lib/commands/console.rb:25:in `exec': No such file or directory - irb  -r irb/completion -r script/../config/../config/environment -r console_app -r console_with_helpers --simple-prompt (Errno::ENOENT)
        from /usr/lib/ruby/gems/1.8/gems/rails-1.1.2/lib/commands/console.rb:25
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/lib/ruby/gems/1.8/gems/activesupport-1.3.1/lib/active_support/dependencies.rb:147:in `require'
        from script/console:3

Any ideas of how to fix this anybody?

DAZ

---

### Post by _lynX on 2006-11-06
How did you go about installing Rails?

It's recommended that you use apt-get/aptitude to install ruby, rdoc, irb, and ri before installing Rails through [RubyGems](http://rubyforge.org/frs/?group_id=126).

```

sudo aptitude install ruby rdoc irb ri
cd
wget http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz
tar -zvfx rubygems-0.9.0.tgz
cd rubygems-0.9.0/
sudo ruby setup.rb
sudo gem install rails

```

You should be good to go after that!

---

### Post by daz4126 on 2006-11-06
Hi,

Thanks for that. Can't remember how I did the install (probably with synaptic).

Bit of a newbie question here ... If I run the code you suggested, will it be okay if some of the stuff is already installed or do I have to uninstall my current setup first?

Thanks,

DAZ

---

### Post by _lynX on 2006-11-06
You will probably want to run 

```

sudo aptitude remove rails

```

just to make sure that the RubyGems install of Rails won't conflict, but other than that, you should be fine.

---

### Post by daz4126 on 2006-11-07
Hi _Lynx,

Sorry for the delay. I've been working all day and only just managed to get home and onto my linux box. It worked like a charm. Thanks so much for the help.

DAZ:D

---

### Post by _lynX on 2006-11-07
> **daz4126 said:**
> Hi _Lynx,

Sorry for the delay. I've been working all day and only just managed to get home and onto my linux box. It worked like a charm. Thanks so much for the help.

DAZ:D

Glad it worked out! :)

---

