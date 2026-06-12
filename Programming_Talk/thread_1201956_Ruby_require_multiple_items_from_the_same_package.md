---
title: "Ruby require: multiple items from the same package?"
date: 2009-07-01
forum: Programming Talk
---

### Post by Squid Spectre on 2009-07-01
I'm about three weeks into Ruby coming from C++ and Java and enjoying it so far. I've spent a lot of time reading "The Ruby Way" 2nd ed from about cover to cover but the old brain is still very much in the beginner's stage of understanding some of subtleties  

The problem I'm trying to solve is that I am writing a rather large application that consists of about 8 packages each with their own set of Ruby classes. It kind of looks like this:

Project
[INDENT]Commo[/INDENT]
[INDENT][INDENT]-Main.rb[/INDENT][/INDENT]
[INDENT][INDENT]-Designator.rb[/INDENT][/INDENT]
[INDENT]-Interpreter[/INDENT]
[INDENT][INDENT]-DomainInterpreter.rb[/INDENT][/INDENT]

           ...(more packages with more classes/modules)

In most instances I have to require one or more item from the same (or other) package for each given class to do its job. However, in some cases a class requires an entire package. While it isn't a problem to require each one individually, it is a bit of a nuisance. In java you can do 'import java.io.*' and import a whole set of items at once. 

The question I have is, "Is there a way to require multiple items from the same package in one line of code in Ruby 1.8.6?" 

Thanks in advance for the time and help!

---

### Post by Squid Spectre on 2009-07-01
This worked for the record:

Dir.glob("../Path/*/*.rb").each {|mod| require mod}

---

### Post by rlzyoner on 2009-07-01
How's it going.
Good to know you got it working.
Another way that I sometimes do this is to add the directory containing the files that you need to the load path

$LOAD_PATH << "#{FILE.dirname(__FILE__)}/../.."

Load path is simply an array containing all the files that are to be loaded when the program is executed.
This will add ALL the files located 2 directories up the load path.
If it's only a select few files then this is probably overkill

Rlzyoner

---

