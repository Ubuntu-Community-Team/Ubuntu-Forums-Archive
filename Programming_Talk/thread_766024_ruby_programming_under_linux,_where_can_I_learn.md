---
title: "ruby programming under linux, where can I learn?"
date: 2008-04-24
forum: Programming Talk
---

### Post by Taleman on 2008-04-24
Does anyone where I can find how to program in ruby under linux. There are pleny off books/guides for c++, python, etc however I can't seem to find any for ruby.

---

### Post by LaRoza on 2008-04-24
> **Taleman said:**
> Does anyone where I can find how to program in ruby under linux. There are pleny off books/guides for c++, python, etc however I can't seem to find any for ruby.

My wiki.

(Ruby is the same basically no matter the OS)

---

### Post by Taleman on 2008-04-25
> **LaRoza said:**
> My wiki.

(Ruby is the same basically no matter the OS)

thanks, what is needed in order to compile ruby code?

all I've been able to find is ruby-gnome2 but that doesn't seem to be a compiler

---

### Post by crush304 on 2008-04-25
sudo apt-get install ruby-full
sudo apt-get install rubybook

no need to compile,

just run 
```
ruby yourfile.rb
```

---

### Post by LaRoza on 2008-04-25
> **Taleman said:**
> thanks, what is needed in order to compile ruby code?

all I've been able to find is ruby-gnome2 but that doesn't seem to be a compiler

Ruby is interpreted. There is an interactive interpreter also for Ruby.

See this: [http://ubuntuforums.org/showthread.php?t=692720](http://ubuntuforums.org/showthread.php?t=692720) (it is in the Programming Talk FAQ ;))

My wiki has a link to another wiki for programming in Ubuntu, it also had this information.

---

### Post by mssever on 2008-04-25
```
sudo aptitude install ruby irb ri
```irb is the Ruby shell. Put the following in ~/.irbrc to enable tab completion (very handy for exploring):```
require "irb/completion"
```ri is a CLI documentation browser.

Also, bookmark [http://ruby-doc.org/](http://ruby-doc.org/). There are several good tutorials out there to get you started. Beyond that, ruby-doc has all the core and standard library documentation. Pay special attention to the core section.

---

### Post by jespdj on 2008-04-25
Ruby homepage: [http://www.ruby-lang.org/](http://www.ruby-lang.org/)
Programming Ruby book: [http://www.rubycentral.com/pickaxe/](http://www.rubycentral.com/pickaxe/)
Ruby documentation: [http://www.ruby-doc.org/](http://www.ruby-doc.org/)
Why's (Poignant) Guide to Ruby: [http://poignantguide.net/ruby/](http://poignantguide.net/ruby/)

---

### Post by Taleman on 2008-04-25
Thank you for all the help.

---

### Post by untermensch on 2008-06-01
Running ruby is the same no matter the os. Chris pine's book "learn to program" was GREAT! I very much enjoyed it. And of course another vote for the pickaxe, "learn to program" by the pragmatic programmers.

---

