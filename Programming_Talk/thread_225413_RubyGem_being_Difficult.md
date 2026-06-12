---
title: "RubyGem being Difficult"
date: 2006-07-29
forum: Programming Talk
---

### Post by wcbaker on 2006-07-29
I managed to install RubyGem but it absolutely refuses to install Rails because it believes the ActiveSupport isnt up to the version that Rails requires. When i look at [http://gems.rubyforge.org/](http://gems.rubyforge.org/) it seems to have the correct version (1.3.1).

Here is the error message. Any help would be appreciated.

wes@wes-laptop:~$ sudo gem install rails -y
ERROR:  While executing gem ... (Gem::GemNotFoundException)
    Could not find activesupport (= 1.3.1) in the repository

---

