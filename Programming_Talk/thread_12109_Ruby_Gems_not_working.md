---
title: "Ruby Gems not working"
date: 2005-01-22
forum: Programming Talk
---

### Post by offby1 on 2005-01-22
I had my interest in Ruby server side development piqued by an article on slashdot today, and I decided where better to try and set up ruby than on the laptop I run Ubuntu on.

However, I ran into some serious issues with it that have more or less completely torpedoed my hopes of trying out Rails et al.

Essentially, there are some fundamental flaws with the way that Ruby is packaged for Ubuntu, as far as I can tell.  The Ruby equivalent to CPAN -- Gems -- is not included by default, and even when I have installed it, I still cannot install some of the packages.  After, for example, installing actionpack, from there on out I can get no closer to installing Rails.

Can anyone who is using Ruby on Ubuntu maybe offer some tips on how you got your setup to work?  I'm on warty, if it makes a difference.

---

### Post by wtd on 2005-01-22
I solved this problem just today.  Grab the latest source for Ruby from [http://www.ruby-lang.org](http://www.ruby-lang.org) and compile it.  You probably want to configure it to install in /usr instead of /usr/local so it'll overwrite the Ruby you already have.

Then try installing gems again.  Worked fine for me.  Just make sure you run "ruby setup.rb" as super user.

---

### Post by offby1 on 2005-01-22
[QUOTE=wtd]I solved this problem just today.  Grab the latest source for Ruby from [http://www.ruby-lang.org](http://www.ruby-lang.org) and compile it.  You probably want to configure it to install in /usr instead of /usr/local so it'll overwrite the Ruby you already have.

Then try installing gems again.  Worked fine for me.  Just make sure you run "ruby setup.rb" as super user.[/QUOTE]
 Thanks, that's just right.

Works like a charm!

---

### Post by regeya on 2005-02-01
[QUOTE=offby1]I had my interest in Ruby server side development piqued by an article on slashdot today, and I decided where better to try and set up ruby than on the laptop I run Ubuntu on.

However, I ran into some serious issues with it that have more or less completely torpedoed my hopes of trying out Rails et al.

Essentially, there are some fundamental flaws with the way that Ruby is packaged for Ubuntu, as far as I can tell.  The Ruby equivalent to CPAN -- Gems -- is not included by default, and even when I have installed it, I still cannot install some of the packages.  After, for example, installing actionpack, from there on out I can get no closer to installing Rails.

Can anyone who is using Ruby on Ubuntu maybe offer some tips on how you got your setup to work?  I'm on warty, if it makes a difference.[/QUOTE]

There are more flaws than gems being missing; take a look some time and see how many different directions the ruby standard library is split.

I got this hint from the Ruby on Rails website.  It requires installing wajig, of course.

```
wajig install `wajig list-names ruby1.8` irb1.8 rdoc1.8 ri1.8
```

If I had it to do over again, I'd rather do the following (warning, not tested):

```
aptitude --with-recommends --with-suggests install `wajig list-names ruby1.8` irb1.8 rdoc1.8 ri1.8
```

Then you can install Gem by hand (go on, it won't hurt.)

That should be a more-or-less complete Ruby install.  It was complete enough for me to install Ruby on Rails (though truth be told I'm still evaluating it and am a complete Ruby n00b.  :D

---

### Post by TheOtherShoe on 2005-03-05
Thanks for the tip regeya, I was getting really frustrated trying to get rails going. However the command,

```
aptitude --with-recommends --with-suggests install `wajig list-names ruby1.8` irb1.8 rdoc1.8 ri1.8
```
did not work for me for some reason. I got the same errors when installing rubygems that I had gotten after building ruby myself, that the zlib library could not found. Everything did work after I tried,

```
wajig install `wajig list-names ruby1.8` irb1.8 rdoc1.8 ri1.8
```

---

### Post by Retrix on 2005-03-06
These instructions worked for me ... straight from the source...
[http://wiki.rubyonrails.com/rails/show/RailsOnDebianUnstable](http://wiki.rubyonrails.com/rails/show/RailsOnDebianUnstable)

---

