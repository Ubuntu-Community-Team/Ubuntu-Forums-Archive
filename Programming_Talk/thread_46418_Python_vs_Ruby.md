---
title: "Python vs Ruby"
date: 2005-07-04
forum: Programming Talk
---

### Post by karthik085 on 2005-07-04
Among Python vs Ruby, which is the best to learn first? 
Also, I am a Java fanatic. Is it better to learn Python or Ruby vs Jython or JRuby?

---

### Post by Quest-Master on 2005-07-04
I've gone through most of both languages, and I still wave my support for Python.

The biggest reason was mainly readability. Simply compare a Ruby and a Python file for the same task, and IMO, the Python one is simply more readable. I mean, a lot of the Ruby stuff looks like Brainfuck, I'm sorry to say. :P

---

### Post by ltmon on 2005-07-04
I would have to advocate Ruby.  As a Java programmer you will be amazed at the internal consistency of Ruby, and sad that we in the Java world miss out on it.  Also Ruby-on-Rails is a fun web framework to play with (it makes J2EE/Struts etc. seem positively painful).

That said, Python runs a close second for me and whichever you learn you can't go to wrong.  More stuff is written in Python (and it's Ubuntu's language of choice) which gives it  an advantage.

L.

---

### Post by buffbikedude on 2005-07-04
[QUOTE=karthik085]Among Python vs Ruby, which is the best to learn first? 
Also, I am a Java fanatic. Is it better to learn Python or Ruby vs Jython or JRuby?[/QUOTE]
 It depends. I prefer Python but will use Ruby on Rails for web apps.

---

### Post by bonega on 2005-07-06
Is it only me that finds the object-orientation in python to be kind of an afterthought?
Ruby  is objectoriented from the ground up.

---

### Post by thumper on 2005-07-06
[QUOTE=bonega]Is it only me that finds the object-orientation in python to be kind of an afterthought?
Ruby  is objectoriented from the ground up.[/QUOTE]
Objects in python are definitaly not an afterthought, however some encapsulation details take a little while to get accustomed to (especially if you come from C++ or Java).

After reading all the chatter on these forums about Ruby I decided to read the online book everyone was quoting and take a look at it.  Personally I would rather have the exposed member variables than the warts all through the code.  It is one of the main reasons that I prefer python to perl is that I don't have to worry about the $ or @ prefixs to the variable names based on their type.  Ruby has different ones based on visiblility.

Python has a very clean readable style, and I prefer it.

---

### Post by Quest-Master on 2005-07-06
People seem to think that object-orientation EVERYWHERE is what we need.

And, personally, I say keep object-orientation where it is needed, and other things like functionally-based programming to where they should be. Exactly what is allowed in Python. ;)

---

### Post by DJ_Max on 2005-07-06
I'll have to side with Ruby. Python is a somewhat cleaner language, though its OOP was added as an afterthought, which you can clearly see in it's quirks. It comes down to Blocks and a lot better OO, i.e the difficulty in modifying classes. I spent some serious time looking into Python and didn't care for it much. 

Both languages are high level, GarbageCollected, and DynamicallyTyped.  Ruby will make more sense if you're from a Smalltalk or Perl background. Python makes more sense if your background is in Algol68 derived language, such as Java or C++. Writing "for" and "while" loops is rare in Ruby. But, the less error-prone and cleaner constructs, like "each", are it's replacement.

Ruby & Pythons syntax are similar, except that Python depends on white space for concatenation. But they are implemented a bit differently. While Python, the construct "a.b" means lookup "b" in the dictionary "a". Ruby "a.b" means send a *message* named "b" to the object represented by "a", similar to Smalltalk.

Python is still an ok language, and if you find it more familar than Ruby, then use Python, there isn't a significant difference aside from the OO features.

---

### Post by wtd on 2005-07-06
I say learn both.  They're both worthwhile to know, and they're both easy enough that it's feasible.

---

### Post by DJ_Max on 2005-07-06
[QUOTE=Quest-Master]I mean, a lot of the Ruby stuff looks like Brainfuck, I'm sorry to say. :P[/QUOTE]
Just to clarify, he means [Brainfuck](http://www.muppetlabs.com/~breadbox/bf/). As I've had people flip when I mentioned that word. 

BTW, I don't think Ruby syntax is similar to 
```
++++++++++++++++++++++++++++++++[>+>+<<-]
>>+++++++++++++++++++++++++<<
++++++++++[>>.-<.<-]
```
[http://cydathria.com/bf/bf_ex1.html](http://cydathria.com/bf/bf_ex1.html)
;-)

---

### Post by fierarul on 2005-07-07
You could also give Jython a try. It's really nice to be able to program in Python and have access to all the java goodies (some gui toolkit seems handy among others).

Plus that in the end you may compile everything to java bytecode.

It really helps you develop a little faster.

Ruby is nice but it doesn't seem that robust yet (don't know what libs are available). I've looked into ruby because of all the buzz behind RoR but stuck with Python/Jython.

---

### Post by dataw0lf on 2005-07-08
Honestly, to me, Ruby looks too much like Perl (explicit scope declaration with weird ass characters, etc) for me.  Ruby on Rails is some great stuff;  but that isn't a language specific framework.  Also, Python just has so much more available in terms of modules, libraries, and frameworks.

---

### Post by nonphasis on 2005-07-08
[QUOTE=bonega]Is it only me that finds the object-orientation in python to be kind of an afterthought?
Ruby  is objectoriented from the ground up.[/QUOTE]

This is a cliche, often brought up by Ruby fans, which is not true, plain and simple. The very first version of Python was object oriented, and Ruby is not any more OO in the "everything is an object" sense than Python. The fact that Python has "real" first-class functions doesn't take away from the fact that those functions are objects as well.

One thing that Ruby has currently going for it are anonymous "code blocks". Python will allow you to program in similar fashion in the next version (2.5), which introduces the "with" statement. But all things considered, the languages are quite similar but Python is much more popular which can be a factor in your decision.

---

### Post by regeya on 2005-07-08
[QUOTE=dataw0lf]Honestly, to me, Ruby looks too much like Perl (explicit scope declaration with weird ass characters, etc) for me.  Ruby on Rails is some great stuff;  but that isn't a language specific framework.  Also, Python just has so much more available in terms of modules, libraries, and frameworks.[/QUOTE]

Ruby on Rails isn't language-specific?  The mind boggles.    :smile:

Yeah, there's some Perl-isms in Ruby; iirc the original plan was to cater to Perl users.  That's slowly going away.

I loved Python when I first worked with it; for my own needs, though, I was looking for something that did some Perl-type things without being Perl-type ugly. ;-)  Ruby fit the bill nicely.  Now, if I was doing application development and had the choice between the two, I'd more than likely...choose Perl.  I hate Perl, but it has more modules, libraries, and frameworks than either of the two, and as convenient as RubyGems is, CPAN is more convenient.

To each their own.  Given the type of stuff I've been doing of late, the Ruby code I've been cranking out is a lot cleaner than the Python code I was pumping out.  Is that the language's fault, or my fault?  Probably the latter, but having built-in regexps in Ruby (look, maw, I don't have to use a library to do a regexp!) has a bit to do with the cleaner code. ;-)  It also helps that everything I'm doing is actually just short helper scripts, so I'm not delving deep into OO.

Eh, use what works for you, and everything will be fine. :-)

BTW, I apologize for not having an example for you.  I thought I had some of the code I moved from Python to Ruby, but I guess I trashed the Python code.  D'oh!  As I said before, it's all simple stuff, so the code I wrote wouldn't look that foreign to beginning Pythonistas...

Well, here's one that inputs a YAML file from a specific location, and exports CSV to stdout.  Most the lifting is done by stuff in the standard library so it's really excessively boring.

Please be kind; bear in mind that you're reading code written by someone who technically isn't a programmer (I work in the composition department of a small newspaper.)  Constructive criticism is always welcome. :-)

```

#!/usr/bin/env ruby

require 'yaml'
require 'csv'

data = YAML.load_file('/Users/shane/Documents/Workspace/contacts/contacts.yml')

outdata = []
line = []
people = data["people"]

for peeps in people.keys:
	dept = people[peeps]
	for depts in dept.keys:
		person = dept[depts]
		addresses = person["addresses"]
			for addrs in addresses:
				line << peeps
				line << person["firstname"]
				line << person["lastname"]
				line << addrs["address"]
				line << addrs["password"]
				outdata << line
				line = []
			end
	end
end

CSV::Writer.generate(STDOUT, ',') do |csv|
	outdata.each {|i| csv << i }
end

```

And here's an edited example of the contacts.yml file:

```

people:
    adv:
        bbaggins:
            computer: ad1
            firstname: Bilbo
            lastname: Baggins
            title: Advertising Manager
            cell: 867-5309
            icom: '409'
            addresses:
                - address: advertising@example-one.com
                  password: booyah6
                - address: advertising@one-example.com
                  password: yahboo9

```

Other than all the 'end's it shouldn't bee too foreign. :-)

---

### Post by Quest-Master on 2005-07-08
> BTW, I don't think Ruby syntax is similar to <Brainfuck>

I wasn't speaking of their similarities in syntax, moreso on how similarly they can both sometimes be completely unreadable unless thoroughly dug into for a while to decipher what is being done.

---

### Post by DirtDawg on 2005-07-08
[QUOTE=regeya]
```

people:
    adv:
        bbaggins:
            computer: ad1
            firstname: Bilbo
            lastname: Baggins
            title: Advertising Manager
            cell: 867-5309
            icom: '409'
            addresses:
                - address: advertising@example-one.com
                  password: booyah6
                - address: advertising@one-example.com
                  password: yahboo9

```
[/QUOTE]

Bilbo is an advertising manager now? Sounds like he's succumed to the evil powers of Mordor. Poor bastard.

---

### Post by regeya on 2005-07-08
[QUOTE=DirtDawg]Bilbo is an advertising manager now? Sounds like he's succumed to the evil powers of Mordor. Poor bastard.[/QUOTE]

 :roll:   :grin:   

Thanks, I needed that.   :)

---

### Post by zeroK on 2005-07-09
If you have the time what speaks against trying both? When I first learned Ruby and Python I tried to play with them at the same time to be able to compare them easily :-) I can't really recommend one language because I like both :-)

---

### Post by dataw0lf on 2005-07-13
[QUOTE=regeya]Ruby on Rails isn't language-specific?  The mind boggles.    :smile:
[/QUOTE]

No, the _framework_ isn't language-specific. e.g., simple object publisher, etc.

---

### Post by judabuddhist on 2005-07-16
Ruby is a very pretty language. It holds up to its claim of being a pure object oriented language better than anything else I know of (although I could complain for a while about the scope of code blocks and the disparity between proc objects and functions). It's probably my favorite language, aesthetically. But I've yet to find a use for it myself, so I can't really speak to its practical nature.

---

### Post by Quest-Master on 2005-07-16
[QUOTE=judabuddhist]Ruby is a very pretty language. It holds up to its claim of being a pure object oriented language better than anything else I know of (although I could complain for a while about the scope of code blocks and the disparity between proc objects and functions). It's probably my favorite language, aesthetically. But I've yet to find a use for it myself, so I can't really speak to its practical nature.[/QUOTE]
 3.times { put "Hello World!" }

No matter how "purely OO" and awesome that may be, it's one more reason why I believe object-orientation shouldn't be absolutely everywhere.

---

