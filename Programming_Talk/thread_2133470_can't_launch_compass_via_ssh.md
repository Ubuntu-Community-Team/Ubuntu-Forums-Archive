---
title: "can't launch compass via ssh"
date: 2013-04-08
forum: Programming Talk
---

### Post by c-m on 2013-04-08
I'm currently developing a website and using SCSS to handle my stylesheets.

I'm used to running compass to monitor changes and compile stylesheets on the fly.

This works locally, but when I SSH into my development machine I get an error trying to run compass.

```
carl@DGN2200:/var/www/modx$ compass watch
/usr/lib/ruby/1.9.1/rubygems/dependency.rb:247:in `to_specs': Could not find compass (>= 0) amongst [actionmailer-3.2.8, actionpack-3.2.8, activemodel-3.2.8, activerecord-3.2.8, activeresource-3.2.8, activesupport-3.2.8, arel-3.0.2, builder-3.0.3, bundler-1.1.4, coffee-rails-3.2.2, coffee-script-2.2.0, coffee-script-source-1.3.3, erubis-2.7.0, execjs-1.4.0, hike-1.2.1, i18n-0.6.1, journey-1.0.4, jquery-rails-2.1.3, jquery-rails-2.0.2, json-1.7.5, mail-2.4.4, mime-types-1.19, multi_json-1.3.6, polyglot-0.3.3, rack-1.4.1, rack-cache-1.2, rack-ssl-1.3.2, rack-test-0.6.1, rails-3.2.8, railties-3.2.8, rake-0.9.2.2, rdoc-3.12, rubygems-bundler-1.0.2, rvm-1.11.3.3, sass-3.2.1, sass-rails-3.2.5, sprockets-2.1.3, sqlite3-1.3.6, sqlite3-1.3.5, thor-0.16.0, tilt-1.3.3, treetop-1.4.10, tzinfo-0.3.33, uglifier-1.3.0, uglifier-1.2.3] (Gem::LoadError)
	from /usr/lib/ruby/1.9.1/rubygems/dependency.rb:256:in `to_spec'
	from /usr/lib/ruby/1.9.1/rubygems.rb:1210:in `gem'
	from /usr/local/bin/compass:18:in `<main>'
```

Can anyone help with this at all?

---

