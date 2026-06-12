---
title: "RMagick problems + solution"
date: 2006-11-24
forum: Programming Talk
---

### Post by Peturrr on 2006-11-24
Had a lot of trouble getting rmagick to work with Ubuntu. This is my solution. 

Do **not** use ```
sudo gem install rmagick
```Somehow the gem doesn't work on Edgy. It does install correctly but in IRB 'require RMagick' leads to 
```
irb(main):001:0> require 'RMagick'
LoadError: no such file to load -- RMagick
        from (irb):1:in `require'
        from (irb):1
```I solved this by uninstalling the gem and installing the precompiled rmagick ubuntu package from the universe repos.: ```
sudo gem uninstall rmagick
sudo apt-get install librmagick-ruby
```

---

### Post by yarox on 2007-04-24
Thanks! Works great for me (under Ubuntu Feisty). Only one thing, when you install a gem, before you can use it, you have to  **require 'rubygems'**  first.

---

### Post by marmistead on 2007-10-22
Thanks, this finally solved my problems with rmagick!

---

### Post by Railsbuntu on 2007-11-01
Thank you. This worked for me with Ubuntu Gutsy Gibbon 7.10 :popcorn:

---

