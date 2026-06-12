---
title: "ruby on rails3 beta4 basic error"
date: 2010-06-10
forum: Programming Talk
---

### Post by c2h2 on 2010-06-10
hi, im trying to experiment a rails3 on my ubuntu10.04 32bit, with installation guide from rails official website

have installed all packages, when i try to run script/rails server

it showed my following errors:



root@c2h2vaio:~/a# script/rails s
/root/a/config/boot.rb:9:in `rescue in <top (required)>': uninitialized constant Bundler (NameError)
        from /root/a/config/boot.rb:5:in `<top (required)>'
        from script/rails:5:in `require'
        from script/rails:5:in `<main>'


anyone got any ideas? or where should i post this?

---

### Post by sanso on 2010-06-18
interesting, I get the following:

---%<---
$ rails foo
/usr/local/lib/site_ruby/1.9.1/rubygems.rb:213:in `activate': undefined method `requirement' for <Gem::Dependency type=:runtime name="rails" requirements=">= 0">:Gem::Dependency (NoMethodError)
        from /usr/local/lib/site_ruby/1.9.1/rubygems.rb:1082:in `gem'
        from /usr/bin/rails:18:in `<main>'
$
---%<---

not sure if they are related

Ubuntu seems to be a bit - hesitant - to work with rails in higher versions. I had to hack a bit to get rubygems 1.3.7 installed.

Any clues anyone?

---

