---
title: "Installing Ruby"
date: 2007-10-22
forum: Programming Talk
---

### Post by bruban on 2007-10-22
Hello,

I'm trying to install ruby on Ubuntu 7.10 so that I can learn the language.

To install, I used the command:

aptitude -y install ruby1.8 ruby1.8-dev ri1.8 rdoc1.8 irb1.8 ruby1.8-examples libdbm-ruby1.8 libgdbm-ruby1.8 libtcltk-ruby1.8 libopenssl-ruby1.8 libreadline-ruby1.8


Now according to the O'Reilly book, Learning Ruby, I can check the installation using:

which ruby


However, ruby doesn't appear to be in my path:

echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin


Apparently the default location is /usr/local/bin/ruby

Is there something obvious that I'm missing here wrt checking that I have ruby set up OK?

Is there something different with the Ubuntu ruby package?

Bruce

---

### Post by germania on 2007-10-22
I've found that 'which' will cache its results and sometimes not give to-the-second accurate answers.  try just typing 'ruby' and see if it says 'not found', or if you get a blank line (if you do, try typing 'puts "Hello World" ' without single quotes and hit ctrl-d... if it says hello world, you just wrote your first ruby program).  You can also type /usr/local/bin/rub and hit tab, and see if it autocompletes for you.

---

### Post by bruban on 2007-10-22
> **germania said:**
> I've found that 'which' will cache its results and sometimes not give to-the-second accurate answers.  try just typing 'ruby' and see if it says 'not found', or if you get a blank line (if you do, try typing 'puts "Hello World" ' without single quotes and hit ctrl-d... if it says hello world, you just wrote your first ruby program).  You can also type /usr/local/bin/rub and hit tab, and see if it autocompletes for you.




Thanks for the reply.

Typing ruby at the command prompt (as root) gives the following:

#  ruby
The program 'ruby' is currently not installed.  You can install it by typing:
apt-get install ruby
bash: ruby: command not found



Bruce

---

### Post by germania on 2007-10-22
I would go back to your initial aptitude command, and prepend ruby to the list of packages... until your post I thought it was just a metapackage for ruby1.8, but maybe not.

HTH

---

### Post by bruban on 2007-10-23
> **germania said:**
> I would go back to your initial aptitude command, and prepend ruby to the list of packages... until your post I thought it was just a metapackage for ruby1.8, but maybe not.

HTH


Thanks for your help. 

Adding the package ruby appears to have done  the trick.


root@thispc# ruby
puts "Hello World"
Hello World



It seems from checking Synaptic that the package 'ruby' is at a different version (1.8.2-1) compared to the rest of the packages e.g ruby1.8 (1.8.6.36-Ubuntu3).

Any thoughts?

---

### Post by germania on 2007-10-23
Glad to see you're off and running.

1.8.2 is very old, comparatively speaking.  The people in charge of the repos usually know what they're doing though, so if it works, I would not worry about it unless / until you find problems with the release you have.  

I think ruby is a fantastic language, and use it whenever I can.  I hope you enjoy it as much as I do :)

---

### Post by bruban on 2007-10-23
Thanks for your help.

I've heard a lot of good things about Ruby, particularly with Rails.

I'm looking forward to getting my hands dirty again.

cheers,

Bruce

---

### Post by baddogtoo on 2007-10-23
"I would go back to your initial aptitude command, and prepend ruby to the list of packages... until your post I thought it was just a metapackage for ruby1.8, but maybe not."

What do you mean "prepend ruby to packages"? 

Ruby on Rails rocks on my Windows computer. I am trying to love Linux, but hassles like this (and the fact that gutsy broke my wireless) really keep me from recommending it to my friends. All recent instructions on how to install/compile Ruby on my Ubuntu 7.10 computer have failed. Very frustrating.

Any help will be appreciated. 

-Mike-

---

### Post by bruban on 2007-10-23
Hi Mike,

I'm glad that you're trying Linux, give it a bit of time and you'll be amazed at how quickly problems are solved and how helpful people can be.


wrt our problems installing ruby, you get these with any product, including windows based.


I prefer to install my apps under script control so that I can easily get my system back to a known state after a problem. You can also use Synaptic if you prefer a GUI (System>Administration>Synaptic Package Manager)

I did the following and I'm now up and running with my attempts to learn ruby:

- in a terminal window (Applications>Accessories>Terminal)

Sudo as root:

```
sudo -s -H                      
  (your password)
```

cut and paste the following code into your terminal:

  ```
 aptitude -y install ruby ruby1.8 ruby1.8-dev ri1.8 rdoc1.8 irb1.8          \
  ruby1.8-examples libdbm-ruby1.8 libgdbm-ruby1.8 libtcltk-ruby1.8          \
  libopenssl-ruby1.8 libreadline-ruby1.8
```

Confirm that ruby is available:

```
which ruby
```

This should return the following:

/usr/bin/ruby


Please note that these steps will probably not install rails as well. (I haven't got that far yet).

HTH

Bruce

---

### Post by jespdj on 2007-10-24
You're making it more complicated than necessary.

You should just do:
```
sudo apt-get install ruby irb rdoc
```
as described on the [Download Ruby](http://www.ruby-lang.org/en/downloads/) page.

This will install Ruby **1.8.6** (not 1.8.2, even though Synaptic says that the "ruby" package is version 1.8.2). You can check that it's 1.8.6 by starting irb and typing: RUBY_VERSION [enter].

---

### Post by bruban on 2007-10-24
Thanks for your comments, I was going by the following ambiguous comment in Synaptic for the package ruby1.8.

> Interpreter of object-oriented scripting language Ruby 1.8 
Ruby is the interpreted scripting language for quick and easy
object-oriented programming.  It has many features to process text
files and to do system management tasks (as in perl).  It is simple,
straight-forward, and extensible.

This package provides version 1.8 series of Ruby.

On Debian, Ruby 1.8 is provided as separate packages.  You can get
full Ruby 1.8 distribution by installing following packages.

  ruby1.8 ruby1.8-dev ri1.8 rdoc1.8 irb1.8 ruby1.8-elisp
  ruby1.8-examples libdbm-ruby1.8 libgdbm-ruby1.8 libtcltk-ruby1.8
  libopenssl-ruby1.8 libreadline-ruby1.8


Also the ruby package seems to install ruby 1.8 even though the package info states that it is at version 1.8.2-1.

```
pc $  ruby --version
ruby 1.8.6 (2007-06-07 patchlevel 36) [i486-linux]
```

---

