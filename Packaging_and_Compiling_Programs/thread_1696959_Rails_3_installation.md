---
title: "Rails 3 installation"
date: 2011-02-28
forum: Packaging and Compiling Programs
---

### Post by mindaslab on 2011-02-28
Hello Ubuntu People,

I am a Ruby on Rails programmer. I would like to use ruby 1.9.2 with rails 3.x and have Rmagick and Imagemagick for ruby work perfectly for my rails application.

Can any one tell me how to do it. All I find is ruby 1.8.x is supported by Debian systems and some how full blown rails 3.x development is impossible.

---

### Post by jeff61 on 2011-03-10
I don't know if you're still stuck on this, but I'd use RVM. 

Once you [install RVM]("http://rvm.beginrescueend.com/rvm/install/"), it will give you directions to install Ruby, and from there you should probably be able to do the rest by installing gems and having bundler install and build prerequisites from source.

Yes, RVM is one more tool to learn ... but it takes care of so many details that it's pretty much indispensable.

---

