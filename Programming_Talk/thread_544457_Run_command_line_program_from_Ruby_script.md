---
title: "Run command line program from Ruby script?"
date: 2007-09-06
forum: Programming Talk
---

### Post by mysticrider92 on 2007-09-06
Hi, I have been learning how to use Ruby lately and had a question about it. How would I run a command-line program from Ruby and get the script to print out the result? I specifically want to get it to tell me the result of hddtemp in a GUI, just as a simple experiment. 

Sorry if this has been asked before, I haven't been able to find anything about it.

[edit] Also, is there a way to integrate Ruby with Glade? I have heard that this should be possible, but haven't found any documentation for it.

---

### Post by Awalton on 2007-09-06
I'm not a Ruby expert (I don't know anything about the language truthfully), but have you tried "system()"? Just about every language out there has a system() function that lets you run shell commands; I'm not sure if Ruby has them namespaced or how you'd get to it, though.

At least that should get you started.

---

### Post by geraldm on 2007-09-06
Code:
bb = IO.popen("command")
b = bb.readlines
puts b.join
/code

for glade, get the ruby-libglade from 
[http://www.ruby-lang.org/en/raa.html](http://www.ruby-lang.org/en/raa.html) 

Gerald

---

### Post by DeadEyes on 2007-09-06
In ruby you can use
system("tar xzf test.tgz") ->true
or
backquotes
result = `date` -> "Thur Sep 06"

If you want more interaction have a look at IO::popen

Edit: on top of what geraldm said

[http://ruby-gnome2.sourceforge.jp/hiki.cgi?ruby-glade-create-template](http://ruby-gnome2.sourceforge.jp/hiki.cgi?ruby-glade-create-template) this might be of interest

---

### Post by mysticrider92 on 2007-09-07
Ok, thanks. I just need the basic way to run it, but I will look into the other function you suggested.

---

