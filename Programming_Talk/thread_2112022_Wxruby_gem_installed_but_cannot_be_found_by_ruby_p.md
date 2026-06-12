---
title: "Wxruby gem installed but cannot be found by ruby program."
date: 2013-02-03
forum: Programming Talk
---

### Post by ntzrmtthihu777 on 2013-02-03
Ok, Getting into ruby programming, wanted to try out this program and learn from its source code. It required several gems, which I installed with the following command, output included:

[spoiler=original error]```
ntzrmtthihu777@bt:~/RMXP/rxdataed$ sudo gem install wxruby rake rubyscript2exe archive-tar archive-zip gettext
Fetching: wxruby-2.0.0-x86_64-linux.gem (100%)
Successfully installed wxruby-2.0.0-x86_64-linux
Fetching: rake-10.0.3.gem (100%)
Successfully installed rake-10.0.3
Fetching: rubyscript2exe-0.5.3.gem (100%)
WARNING: rubyscript2exe-0.5.3 has an invalid nil value for @cert_chain
Successfully installed rubyscript2exe-0.5.3
Fetching: archive-tar-0.9.0.gem (100%)
Successfully installed archive-tar-0.9.0
Fetching: io-like-0.3.0.gem (100%)
Fetching: archive-zip-0.5.0.gem (100%)
Successfully installed io-like-0.3.0
Successfully installed archive-zip-0.5.0
Fetching: locale-2.0.8.gem (100%)
Fetching: levenshtein-0.2.2.gem (100%)
Building native extensions.  This could take a while...
Fetching: gettext-2.3.7.gem (100%)
Successfully installed locale-2.0.8
Successfully installed levenshtein-0.2.2
Successfully installed gettext-2.3.7
9 gems installed
Installing ri documentation for wxruby-2.0.0-x86_64-linux...
Installing ri documentation for rake-10.0.3...
Installing ri documentation for rubyscript2exe-0.5.3...
Installing ri documentation for archive-tar-0.9.0...
Installing ri documentation for io-like-0.3.0...
Installing ri documentation for archive-zip-0.5.0...
Installing ri documentation for locale-2.0.8...
Installing ri documentation for levenshtein-0.2.2...
Installing ri documentation for gettext-2.3.7...
Installing RDoc documentation for wxruby-2.0.0-x86_64-linux...
Installing RDoc documentation for rake-10.0.3...
Installing RDoc documentation for rubyscript2exe-0.5.3...
Installing RDoc documentation for archive-tar-0.9.0...
Installing RDoc documentation for io-like-0.3.0...
Installing RDoc documentation for archive-zip-0.5.0...
Installing RDoc documentation for locale-2.0.8...
Installing RDoc documentation for levenshtein-0.2.2...
Installing RDoc documentation for gettext-2.3.7...

```But, on attempt to run said program, I get the following error:
```
ntzrmtthihu777@bt:~/RMXP/rxdataed/src$ ruby rxdataed.rb 
/usr/lib/ruby/vendor_ruby/1.8/rubygems/dependency.rb:247:in `to_specs': Could not find wxruby (<= 1.9.8) amongst [archive-tar-0.9.0, archive-zip-0.5.0, gettext-2.3.7, io-like-0.3.0, levenshtein-0.2.2, locale-2.0.8, rake-10.0.3, rubyscript2exe-0.5.3, wxruby-2.0.0-x86_64-linux] (Gem::LoadError)
    from /usr/lib/ruby/vendor_ruby/1.8/rubygems/dependency.rb:256:in `to_spec'
    from /usr/lib/ruby/vendor_ruby/1.8/rubygems.rb:1208:in `gem'
    from rxdataed.rb:34

```[/spoiler]I have obviously installed it, it just seems ruby does not know where it is, perhaps because it is looking in 1.8 but the gem is version 2.0

Any help/feedback would be appreciated.

[EDIT] Ok, learned about the rvm, installed into that instead, turns out I just derped and installed the wrong version of wxruby. I got the right version now, but I now have an additional error:
```
ntzrmtthihu777@bt:~/RMXP/rxdataed/src$ ruby rxdataed.rb 
ruby: symbol lookup error: /home/ntzrmtthihu777/.rvm/gems/ruby-1.9.3-p374@rxdata/gems/wxruby-1.9.8-x86_64-linux/lib/wxruby2.so: undefined symbol: Init_wxMediaCtrl
```

Seems the creator of the script made an error; the script was asking for <= 1.9.8 which is just plain unusual. I could understand ==1.9.8 if only that version worked, but <= 1.9.8 can even return 0.0.1, which is even less likely to work

---

