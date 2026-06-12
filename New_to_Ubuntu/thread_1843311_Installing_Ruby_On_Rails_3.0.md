---
title: "Installing Ruby On Rails 3.0"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by IWilNotGivUpIWilNotGivUp on 2011-09-13
Hi,

Newby here. I've got Ubuntu 11.4, Ruby 1.9.2, and RubyGems 1.8.10, and I've got RVM installed, if that's any help!

I tried to install Rails 3.0 and when I did a $ rails -v I got Rails 2.3.5

I then entered: 
$ sudo gem install rails --no-ri --no-rdoc
$ [password]
Then got the message:
Successfully installed rails-3.1.0
1 gem installed

Delighted, I then checked with $ rails -v and it said: Rails 2.3.5

Any help would be much appreciated.  Please break things down as if you were talking to an idiot.

Kind regards

GS :)

---

### Post by IWilNotGivUpIWilNotGivUp on 2011-09-14
I guess this is the wrong place.  Never mind.  Sorry to have troubled you. :(

---

### Post by Dangertux on 2011-09-14
The procedure that works for me for installing RoR on Ubuntu is the following.

```

sudo apt-get install build-essential ruby rdoc libopenssl-ruby
wget http://production.cf.rubygems.org/rubygems/rubygems-1.8.10.tgz
tar xzvf rubygems-1.8.10.tgz
cd rubygems-1.8.10
sudo ruby setup.rb
sudo ln -s [FONT=Verdana]/usr/bin/gem1.8 /usr/local/bin/gem
[/FONT]sudo gem install rails

```

Let me know if that works for you.

---

### Post by IWilNotGivUpIWilNotGivUp on 2011-09-30
Thanks.  I'd waited 2 or 3 days for an answer, then gave up.  I ended up going to Site5 to ask for help.  I got even less.  They should rename their site obtuse5.

I appreciate you getting back to me and I've cut and pasted your message on a document to save, but I'm removing Ubuntu and VirtualBox from my system and starting again.  I think I tried so many peoples ideas of what to do on the Internet that I think I completely ruined my installation.  I've got Hartl's book Ruby on Rails 3 Tutorial.  How he got 5 stars on Amazon I'll never know.  With the installation he goes to great pains to distance himself from Windows (as do all developers - I'm sure you'll admit).  If you have Linux, then he points you to the minefield called Google, and if you have a Mac OS10 (which he wears like a badge) then you're OK, as long as you've also taught Quantum Physics at Caltech. 

Kind regards :)

GS

---

### Post by IWilNotGivUpIWilNotGivUp on 2011-10-03
With a new installation I put in:

sudo apt-get install build-essential ruby rdoc libopenssl-ruby 
wget [http://production.cf.rubygems.org/rubygems/rubygems-1.8.10.tgz](http://production.cf.rubygems.org/rubygems/rubygems-1.8.10.tgz) 
tar xzvf rubygems-1.8.10.tgz 
cd rubygems-1.8.10 
sudo ruby setup.rb
sudo ln -s [FONT=Verdana]/usr/bin/gem1.8 /usr/local/bin/gem[/FONT]

All was going well.. 

Then I put in:

sudo gem install rails

and it would have none of it. 

Any ideas please?

Thanks

GS :)

---

