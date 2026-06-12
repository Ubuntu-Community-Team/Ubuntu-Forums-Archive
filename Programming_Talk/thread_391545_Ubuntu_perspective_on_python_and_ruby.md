---
title: "Ubuntu perspective on python and ruby"
date: 2007-03-23
forum: Programming Talk
---

### Post by mac.ryan on 2007-03-23
I wish to get back into programming (many years ago I was rather fluent in turbopascal and C, but it's now ages i don't write a single line...).

Having read previous various posts on "what language is the best", I would be interested in starting with python or ruby. What I understood, in the debate "python vs ruby" is that ruby seems to be conceptually based on more recent paradigmas, while python seems to be much more mature.

My preference would therefore be for Ruby as it sounds like studying it is a better investment (and however - for the moment - I don't need to do anything particularly advanced).

However - before to invest my time and energy in learning ruby - I would like to have some** feedback specifically on how well python and ruby fit into the ubuntu scenario**, as I noticed that the vast majority of devs who post here are into python.

Thanks for your help! :)

---

### Post by stokedfish on 2007-03-23
Well, the Amarok devs love ruby.

[http://amarok.kde.org/wiki/Script-Writing_HowTo](http://amarok.kde.org/wiki/Script-Writing_HowTo)

I think you should be fine with both python and ruby though.

---

### Post by pmasiar on 2007-03-23
> **mac.ryan said:**
> What I understood, in the debate "python vs ruby" is that ruby seems to be conceptually based on more recent paradigmas, while python seems to be much more mature.

My preference would therefore be for Ruby as it sounds like studying it is a better investment (and however - for the moment - I don't need to do anything particularly advanced).

Not sure what do you mean by "more recent paradigmas". Ruby migh have 20% more object methods where Python uses standard build-in functions, and lacks some esoteric constructs like closures, but Python is every inch as OOP as Ruby.  

Ie Python uses len("string") while Ruby "string".lenght(). So what? Python has better library support in avarage. Also, Ruby is more close to Perl, with it's quirky syntax peppered by special characters. Python makes goal to be obvious.

> However - before to invest my time and energy in learning ruby - I would like to have some** feedback specifically on how well python and ruby fit into the ubuntu scenario**, )

That one is easy: **Ubuntu uses Python as main language, not Ruby** :-). Also One Laptop Per Child project uses Python. Ruby is more popular with book publishers (because they can sell more books) - many excellent Python books are free dowloads and those do not register at publisher radar at all. Ruby is developed mostly in Japan, and important maillist are in japanase, if you care about stuff like that. Python is used by Google and Google employs/sponsors many top Python developers, including Guido van Rossum, its author.

Ruby has it's big hype intake with Ruby on Rails (RoR) web app framework in 2005, whan Python did not have comparable frameworks, but it was solved since then (after Google hired Guido and his first job there was to implement web-based app :-) ) and now Python has 2 leading excellent frameworks comparable with RoR: Django and TurboGears, and many others, optimized for different niches. 

One of key Python features is **significant whitespace**, and many people dislike it at the first sight (I know it from personal experience: I lost couple of years to perl because of that). But in any big project, coding standards include proper intendation - and if your code is intended properly, syntax is valid. So Python lover says: "it is not a bug, it is a feature". And yes, everyone's code looks the same, and you can read code of other people. Significant whitespace increases readability.

Another excellent feature missing in Ruby is **Python shell**: you can execute any code, import modules, instantiate objects, execute methods, all in command line. So instead of writing half-page scaffolding just to try one method, you can do it in command line in Python. Including trying out code from tutorials, one line at a time.

IMHO (and it is very personal belief :-) ) big part of Ruby popularity is with Java developers, who had first experience with dynamically typed languages in Ruby, whan they realized that Java with Struts is really, really hard way to create simple web apps quickly, found RoR, and they preferred Ruby to Python, because accepting Python would be accepting a mistake - Python was around almost as long as Java, Ruby is newer. :-)

This ("switch from Java to Ruby and not Python")is just my personal belief and I do not intend to respond to any flames - if you think it is otherwise, fine with me :-)

---

### Post by Mirrorball on 2007-03-23
I like Python because the code is clear, explicit and organized (OK, and the standard library is huge). On the other hand, Ruby tries to be more practical and more like a natural language. But, really, I'm trying to write code, not a poem. And I really dislike all of those weird characters : @ $ | and whatever. Ruby doesn't look like line noise like Pearl, but almost. It's actually a nice language, but I prefer Python. I would only learn Ruby for Ruby On Rails.

---

### Post by winch on 2007-03-23
Try them both and see which you prefer. I'm more of a ruby fan but I don't think I could really describe why. I just don't really get on with python. Ruby is not as popular but it's becoming less of an issue. It's only really a problem if you want to use an obscure library or the like, python is more likely to have bindings.

---

### Post by rickardg on 2007-03-23
> **pmasiar said:**
> 

Another excellent feature missing in Ruby is **Python shell**: you can execute any code, import modules, instantiate objects, execute methods, all in command line. So instead of writing half-page scaffolding just to try one method, you can do it in command line in Python. Including trying out code from tutorials, one line at a time.

A small nit:

Ruby does have a REPL (shell), it's called irb

```

$ irb
irb(main):001:0> puts "Hello, World"
Hello, World
=> nil
irb(main):002:0> 1+2
=> 3

```

It seem that python is used for Ubuntu infrastructure, but if you want to write programs that run on Ubuntu ruby would serve you equally well. 

I'm not being of much help, am I? Just pick one and get on with the coding. :-)

---

### Post by pmasiar on 2007-03-24
> **rickardg said:**
> A small nit: Ruby does have a REPL (shell), it's called irb

That's cool. I was under the impression you need to write a page of Ruby code to try anything. Can you also import modules into irb, instantiate objects, and execetute their methods?  Now I see why Java coders flocked to Ruby - shell is rather cool and sooo missing in Java.

Another feature of Python shell I like: you can instantiate an object, and then you interrogate it in shell: > dir(objname) - it will print all methods object has, including inherited, and > help(objname.method) will print docstring. More fun than reading the docs :-)

---

### Post by blanky on 2007-03-24
I think of Python as really productive (*Personally, not saying Ruby isn't*), and Ruby as being very fun and elegant. Check out the [Ruby Site]("http://www.ruby-lang.org/en/"), you can try Ruby out on a web page [here]("http://tryruby.hobix.com/"). Ruby seems to really teach Object Oriented Programming really well since it treats practically everything like an Object. Although I have no favorite, I usually write in Python more, but that's because I haven't really taken the time to learn Ruby, something I'd really like to do, since it seems like a neat little sexy language.

---

### Post by rickardg on 2007-03-24
> **pmasiar said:**
> That's cool. I was under the impression you need to write a page of Ruby code to try anything. Can you also import modules into irb, instantiate objects, and execetute their methods? 

Sure, 

```

$ irb
irb(main):001:0> require 'net/http'
=> true
irb(main):002:0> h = Net::HTTP.new('planet.ubuntulinux.org',80)
=> #<Net::HTTP planet.ubuntulinux.org:80 open=false>
irb(main):003:0> resp, data = h.get('/index.html', nil)

<snip loads of http and html>

irb(main):004:0> resp.code
=> "200"
irb(main):005:0> resp.message
=> "OK"
irb(main):006:0> data[0..100]
=> "<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Transitional//EN\" \"http://www.w3.org/TR/xhtml1/DTD/xhtml"

```

> **pmasiar said:**
> Another feature of Python shell I like: you can instantiate an object, and then you interrogate it in shell: > dir(objname) - it will print all methods object has, including inherited, and > help(objname.method) will print docstring. 

```
irb(main):025:0> ObjectSpace.each_object(Net::HTTP) {|o| print o}
#<Net::HTTP:0x12038c5e0>=> 1
irb(main):026:0> h.methods[0..5]
=> ["methods", "proxy_pass", "port", "instance_eval", "read_timeout", "start"]
irb(main):027:0> h.respond_to?("get")
=> true
irb(main):028:0> h.respond_to?("make_coffee")
=> false

```


Almost like python (except for the docstring)... :-)

---

### Post by pmasiar on 2007-03-24
Nice try, but Python libraries are little more convenient to use. Just little nitpicking:

f = liburl2.urlopen(url[, data]) returns file object, so you can read it by line or whatever you need, instead of flooding shell with page dump.

analog of h.methods prints whole list, or I can create a copy of that list using h.methods[:]

h.respond_to?("get") - what is the sign '?' doing there? Checks if method exists?

Docstring is great, and best part is that you can provide it to your own methods/procedures and then it is just used like for system ones.

In summary, Ruby is almost as good as Python, and without doubt I would prefer Ruby over Java for average web any day. But I would still *slightly* prefer Python over Ruby, based on: 
(1) coding standards: no fight with what indent standard to adopt 
(2) less 'line noise' characters in code - I had all line noise I can handle in Perl
(3) opening and closing {} take extra line of code - I want that line on my screen back  :-) 
(4) off-hand chance to get hired by Google :-)

But thank you for explanation, given chance I would be more interested in Ruby project now - it is not as bad as I was afraid

---

### Post by mac.ryan on 2007-03-24
Thanks to all for the answers, all of them welcome and some of them very useful! Thanks especially to those who kept the "ubuntu perspective" in the answers... that was exactly the kind of info I was looking for! :)

---

### Post by Mirrorball on 2007-03-24
> **pmasiar said:**
> 
(1) coding standards: no fight with what indent standard to adopt 
(2) less 'line noise' characters in code - I had all line noise I can handle in Perl
(3) opening and closing {} take extra line of code - I want that line on my screen back  :-) 
(4) off-hand chance to get hired by Google :-)
These are also the reasons why I prefer Python to Ruby, except I don't want to be hired by Google.

---

### Post by rickardg on 2007-03-24
> **pmasiar said:**
> Nice try, but Python libraries are little more convenient to use. Just little nitpicking:

Well I'm not trying to convince anyone to USE ruby, I'm only remarking that the languages are quite similar for most purposes and the OP really have to try them both and make up his/her own mind. In fact I probably use python more than ruby myself.

> analog of h.methods prints whole list, or I can create a copy of that list using h.methods[:]
 
The stuff in the brackets is just array indices, in python it would be h.methods[:6], if you say h.methods you get all of them.

> h.respond_to?("get") - what is the sign '?' doing there? Checks if method exists?

Huh? The '?' is part of the method name. I think ruby follows the same [naming convention as scheme]("http://community.schemewiki.org/?variable-naming-convention"): methods ending in '?' are predicates and those ending in '!' are destructive.

> Docstring is great, and best part is that you can provide it to your own methods/procedures and then it is just used like for system ones.

No argument there, that's one of the reasons I like [lispy]("http://www.cliki.net/index") [languages]("http://www.schemers.org/").

> In summary, Ruby is almost as good as Python, and without doubt I would prefer Ruby over Java for average web any day. 

For someone choosing a new language it's more a matter of taste than anything else. I'd checkout the mailing list and forums for both languages and see where I'd fit best in.

Unless  I specifically wanted to work on Ubuntu infrastructure, then I'd choose python.

---

### Post by pmasiar on 2007-03-24
> **rickardg said:**
> Well I'm not trying to convince anyone to USE ruby, I'm only remarking that the languages are quite similar for most purposes and the OP really have to try them both and make up his/her own mind. In fact I probably use python more than ruby myself.

Sorry for misunderstanding. I know that you do not want to convert me from Python to Ruby. In fact I really appreciate your comments and showing me how close Python and Ruby is. You did the hard work learning both languages and being able to compare features.
 
> The stuff in the brackets is just array indices, in python it would be h.methods[:6], if you say h.methods you get all of them.

OK. Skip this part if you are not language lawyer:

There is very subtle difference between using listvariable and listvariable[:]. First passes reference to a list, second creates copy of whole list and passes reference to that copy. So if I do myfunction(listvariable), myfunction can change original listvariable (it is passed be reference), but if I do myfunction(listvariable[:]), myfunction has own copy and cannot change original listvariable.

In ruby, can you make copy of whole list, like h.methods[..] - from beginning to end? Or do you have to put explicit index boundaries, like h.methods[0..] (from beginning)? In Python I can do array slices h.methods[0:] or h.methods[3:] or such (where [0:] is same as [:] )

I know I should just look it up in Ruby book, but I am lazy you already know the answer :-)

> Huh? The '?' is part of the method name. I think ruby follows the same naming convention as scheme: methods ending in '?' are predicates and those ending in '!' are destructive.

Ah OK. Sorry for misunderstanding. I have mixed feelings on that. I sorta like that I can tel from method name if it changes something or just return a value, but I dislike the special characters needed to accomplish that. You are right, it comes to taste and preference.

---

### Post by Ramses de Norre on 2007-03-25
> **pmasiar said:**
> That's cool. I was under the impression you need to write a page of Ruby code to try anything. Can you also import modules into irb, instantiate objects, and execetute their methods?  Now I see why Java coders flocked to Ruby - shell is rather cool and sooo missing in Java.

Another feature of Python shell I like: you can instantiate an object, and then you interrogate it in shell: > dir(objname) - it will print all methods object has, including inherited, and > help(objname.method) will print docstring. More fun than reading the docs :-)

Java has an interactive shell too: bsh (beanshell), by which you can also instantiate objects, import modules etc.
```
ramses@icarus:~$ bsh
Picked up _JAVA_OPTIONS: -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel
BeanShell 2.0b4 - by Pat Niemeyer (pat@pat.net)
bsh % import java.io.File;
bsh % File f = new File("/home/ramses/test.txt");
bsh % System.out.println(f.getPath());
/home/ramses/test.txt
bsh % 
```

---

### Post by pmasiar on 2007-03-25
> **Ramses de Norre said:**
> Java has an interactive shell too: bsh (beanshell), by which you can also instantiate objects, import modules etc.

This is seriously cool, I wonder why it is not promoted more in any of Java books I read. :-(

---

### Post by Jessehk on 2007-03-25
I've been flip-flopping between the two. Right now, I'm a fan of Ruby.

I personally predict that Ruby is going to overtake Python eventually, but with the rising popularity of Ubuntu as **the** Linux to use (and its preference for Python), I'm not entirely sure.

Don't take my predictions too seriously though. I'm just a hobbyist. :)

---

### Post by ceeg on 2007-03-26
Really, it all comes down to personal preference. The languages are so alike. Personally, I've come to use Ruby for Rails development and Python for software development. Although, recently I've been getting in the habit of writing perlish sysadmin-type programs in ruby (which is what i've been using python for mostly).

Really it just boils down to significant whitespace vs special characters (python vs ruby) Both languages have a pattern of thought associated with each one. Which do you fit into?

---

