---
title: "Migrating a repo from SVN to Git on Ubuntu"
date: 2013-01-18
forum: Programming Talk
---

### Post by lads on 2013-01-18
Hello everyone,

I need to migrate a repo (including releases) from SVN to Git. I found out that a tool called [svn2git]("https://github.com/nirvdrum/svn2git") does just that. It's wrapped in ruby and installed with rubygems; here's what I get when I do it:

```
$ sudo gem install svn2git
Successfully installed svn2git-2.2.2
1 gem installed
Installing ri documentation for svn2git-2.2.2...
Installing RDoc documentation for svn2git-2.2.2...
```

But when I try to use it I get a load of errors:

```
$ svn2git
/usr/lib/ruby/vendor_ruby/1.8/rubygems/dependency.rb:247:in to_specs': Could not find svn2git (>= 0) amongst [actionmailer-3.2.1, actionmailer-3.1.0, actionpack-3.2.1, actionpack-3.1.0, activemodel-3.2.1, activemodel-3.1.0, activerecord-3.2.1, activerecord-3.1.0, activeresource-3.2.1, activeresource-3.1.0, activesupport-3.2.1, activesupport-3.1.0, ansi-1.4.2, ansi-1.3.0, arel-3.0.2, arel-2.2.1, bcrypt-ruby-3.0.1, best_in_place-1.0.6, blankslate-3.1.2, builder-3.0.0, bundler-1.0.18, client_side_validations-3.1.4, coderay-1.0.6, coderay-1.0.5, coffee-rails-3.2.2, coffee-rails-3.1.1, coffee-script-2.2.0, coffee-script-source-1.3.1, coffee-script-source-1.1.2, erubis-2.7.0, execjs-1.3.0, execjs-1.2.9, execjs-1.2.8, execjs-1.2.6, ffi-1.0.11, hike-1.2.1, i18n-0.6.0, journey-1.0.3, jquery-rails-2.0.2, jquery-rails-1.0.14, json-1.6.6, json-1.6.1, libv8-3.3.10.4-x86_64-linux, mail-2.4.4, mail-2.3.0, method_source-0.7.1, method_source-0.7.0, mime-types-1.18, mime-types-1.16, multi_json-1.3.2, multi_json-1.0.3, pg-0.13.2, pg-0.12.2, pg-0.11.0, polyglot-0.3.3, polyglot-0.3.2, postgres-pr-0.6.3, pry-0.9.9.2, pry-0.9.8.1, puma-1.6.3, rack-1.4.1, rack-1.3.4, rack-1.3.3, rack-cache-1.2, rack-cache-1.0.3, rack-mount-0.8.3, rack-ssl-1.3.2, rack-test-0.6.1, railroady-1.0.7, railroady-1.0.2, rails-3.2.1, rails-3.1.0, railties-3.2.1, railties-3.1.0, rake-0.9.2.2, rake-0.9.2, rdoc-3.12, rdoc-3.10, rdoc-3.9.4, rubypython-0.6.2, sass-3.1.15, sass-3.1.10, sass-3.1.8, sass-3.1.7, sass-rails-3.2.5, sass-rails-3.1.4, sass-rails-3.1.2, simple_form-2.0.1, simple_form-1.5.2, slop-2.4.4, slop-2.4.3, sprockets-2.1.2, sprockets-2.0.2, sprockets-2.0.0, sqlite3-1.3.6, sqlite3-1.3.4, therubyracer-0.10.1, therubyracer-0.9.9, thor-0.14.6, tilt-1.3.3, treetop-1.4.10, turn-0.9.5, turn-0.8.3, turn-0.8.2, tzinfo-0.3.33, tzinfo-0.3.30, tzinfo-0.3.29, uglifier-1.2.4, uglifier-1.0.3] (Gem::LoadError)
from /usr/lib/ruby/vendor_ruby/1.8/rubygems/dependency.rb:256:into_spec'
from /usr/lib/ruby/vendor_ruby/1.8/rubygems.rb:1208:in `gem'
from /usr/local/bin/svn2git:18
```

Can anyone help deciphering the cause of these errors? Or maybe suggest an alternative way to migrate a SVN repo to Git?

Thanks.

---

### Post by MadCow108 on 2013-01-18
unfortunately I can't help with the ruby problem
have you tried git-svn? It works very well for me and it is packaged in ubuntu.

---

### Post by lads on 2013-01-22
> **MadCow108 said:**
> unfortunately I can't help with the ruby problem
have you tried git-svn? It works very well for me and it is packaged in ubuntu.

Hi MadCow, I´ve fideled around with git-svn, but the svn tags are always lost. The best I can do is to import the tag folders, which replicates a lot of code. That's why I tried svn2git, since it claims it can deal with tags. Other suggestions are welcome. Thanks.

---

### Post by lads on 2013-01-24
It took a good deal of searching and enquiring, but I finally got to a recipe that does what I need. The issue here is that *git svn clone* doesn't deal with tags by default, but it can eventually do the job. Read the full recipe [at my blog]("http://attheedgeoftime.blogspot.com/2013/01/migrate-svn-repository-to-git.html").

Thank you for the help.

---

