---
title: "Jruby problem thank you"
date: 2009-02-04
forum: Programming Talk
---

### Post by babyboss on 2009-02-04
Hello:
I did 'Jruby script/generate controller home index', and I got "Rails requires RubyGems >= 1.3.1 (you have 1.2.0). Please 'gem update --system' and try again" message. I follwed, and did 'gem update --system', but it tells me there is nothing to update. My rails version is 2.2.2, I tried to install lower version, but did 'gem query --remote --name-matches rails', only rails 2.2.2 version comes up, which is the one I am having. Thank you very much.

---

### Post by crush304 on 2009-02-04
need to add -a to list all versions

'gem query --remote --name-matches rails -a'

should be able to 

gem install rails -v 2.1.2

---

