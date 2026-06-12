---
title: "Ruby -&gt; Python"
date: 2007-06-18
forum: Programming Talk
---

### Post by Ubuntist on 2007-06-18
I've been bouncing back and forth between Ruby and Python, learning a little of each and trying to decide which I like best by applying each to successively larger projects.

At this point, I like Ruby a little better on the whole, but I think Python's greater maturity and larger community outweigh Ruby's advantages.  The thing is, I'm now in the midst of a project for which I've written about 2000 lines of Ruby.  So...[LIST=1]
[*]Is there a Ruby-to-Python converter available?
[*]Is it possible to call Ruby from Python or *vice versa?*
[*]One Ruby feature I'm really going to miss is code blocks; has anyone figured out how to fake these in Python (the way that implicit accessors can be faked)?[/LIST]

---

### Post by pmasiar on 2007-06-18
> **Ubuntist said:**
> I've been bouncing back and forth between Ruby and Python, learning a little of each and trying to decide which I like best by applying each to successively larger projects.

At this point, I like Ruby a little better on the whole, but I think Python's greater maturity and larger community outweigh Ruby's advantages.  

You are right. Ruby was first language with really clever rapid web app development framework. Ruby == Rails, it is not used outside Rails much.

Python lacked such a clever framework in 2005, which gave Ruby opening and lead. Not anymore, either Django or Turbogears are comparable (and in Python spirit, deliberately use less magic). 

It is interesting to watch how big companies started hiring key developers of Python and Ruby. Microsoft has it both ways, support both Python (IronPython) and nor Ruby (RubyOnSteel). Sun blinked when JPython developer was looking for a sponzor (and let MSFT snach him), now Sun pretends it does not matter and supports JRuby instead. Google settled on Python couple years ago, as also did Canonical + Ubuntu.

Recent success was selecting Python as main development language for OLPC, so millions on future Python hackers are getting ready... :-)

> Is there a Ruby-to-Python converter available?

I don't believe it is possible or even feasible. People smart enough and knowledgeable enough to do it are busy doing something profitable. :-) 

For better or worse, be *very* carefull when deciding about how to implement your code: **Code is like tatoo: will stick on you for a *long* time **

> Is it possible to call Ruby from Python or *vice versa?*

http GET/POST is easy enough and ignorant to implementation language - you can move your app from Ruby to Python in stages. Of course you will have maintain ie. Ruby's and Python's versions of ORM, which is pain - and will force you to migrate quicker. :-)


> One Ruby feature I'm really going to miss is code blocks; 

Python has lambda to create anonymous functions, list comprehension, and iterator expressions. You can also pass function pointer as parameter. It might not cover 100% of use cases, but might fit easier to brain :-)

As the zen says: If it is not easy to explain, it is not a good idea. 

BTW next version of Ruby will lack closures....

---

### Post by ssam on 2007-06-18
> **Ubuntist said:**
> Is it possible to call Ruby from Python or *vice versa?*

have a look a xml-rpc. it lets you call a function in another program, and work between many languages.

(just to note python is much better than ruby ;-) )

---

### Post by Jessehk on 2007-06-18
> **ssam said:**
> 
(just to note python is much better than ruby ;-) )


There are enough fanboys around spreading nonsense. Care to elaborate (ie, why you feel this way)?

EDIT: That's not to say I don't prefer Python. But common, don't just make blanket statements like that.

---

### Post by ssam on 2007-06-19
> **Jessehk said:**
> There are enough fanboys around spreading nonsense. Care to elaborate (ie, why you feel this way)?

EDIT: That's not to say I don't prefer Python. But common, don't just make blanket statements like that.

sorry, i though the wink would show that i was joking.

the thread is about making ruby and python work together, and thats a good thing.

i do have a preference for python, but i have not used ruby enough to make a fair comparison. though python is great for what i use it for (scientific stuff, and small gtk apps).

---

### Post by vexorian on 2007-06-19
> **Ubuntist said:**
> I've been bouncing back and forth between Ruby and Python, learning a little of each and trying to decide which I like best by applying each to successively larger projects.

At this point, I like Ruby a little better on the whole, but I think Python's greater maturity and larger community outweigh Ruby's advantages.  The thing is, I'm now in the midst of a project for which I've written about 2000 lines of Ruby.  So...[LIST=1]
[*]Is there a Ruby-to-Python converter available?
[*]Is it possible to call Ruby from Python or *vice versa?*
[*]One Ruby feature I'm really going to miss is code blocks; has anyone figured out how to fake these in Python (the way that implicit accessors can be faked)?[/LIST]
I don't think it is a good idea at all to switch programming languages in the middle of a project, besides the fact that the reasons you used to pick python are quite meaningless.

If you like code blocks so much you shall stick to ruby.

---

### Post by daniel of sarnia on 2007-06-19
> **Jesse said:**
> There are enough fanboys around spreading nonsense. Care to elaborate (IE, why you feel this way)?

EDIT: That's not to say I don't prefer Python. But common, don't just make blanket statements like that.


I heard that ruby is not even threaded.

And by the way rails really is not that new of special, their are a number of good web framework for perl right in cpan. Their are also a number of web frameworks in python, everything I've seen also shows performance gains with using python over Ruby.

---

### Post by vexorian on 2007-06-19
> **Ubuntist said:**
> I've been bouncing back and forth between Ruby and Python, learning a little of each and trying to decide which I like best by applying each to successively larger projects.

At this point, I like Ruby a little better on the whole, but I think Python's greater maturity and larger community outweigh Ruby's advantages.  The thing is, I'm now in the midst of a project for which I've written about 2000 lines of Ruby.  So...[LIST=1]
[*]Is there a Ruby-to-Python converter available?
[*]Is it possible to call Ruby from Python or *vice versa?*
[*]One Ruby feature I'm really going to miss is code blocks; has anyone figured out how to fake these in Python (the way that implicit accessors can be faked)?[/LIST]
I think ruby's syntax is much cleaner and much more useful, not to mention it doesn't use python's only and most horrible flaw that would prevent me and many from ever using it.

And code blocks, so lovely against lambdas ...

---

### Post by pmasiar on 2007-06-19
> **vexorian said:**
> I think ruby's syntax ... doesn't use python's only and most horrible flaw that would prevent me and many from ever using it.

What  is this flaw?

---

### Post by finer recliner on 2007-06-19
i  havent used python. but my experience with ruby has been given me mixed feelings.

pros:
code blocks, easy loops, OO, built in debugger

cons,
-block comments look like code
-do-while loops are terrible
-using variables in strings were better implemented in perl. in ruby its confusing to use the #, and the { } makes it hard to read. ie:
```
 x = "dave"
puts "hello, #{x}! how are you?" 
```

---

### Post by Smygis on 2007-06-19
> **pmasiar said:**
> What  is this flaw?

That you cant write clean code like:
```
int main(){int i=0;char c;while(i<200){
int b=10;
    while(b>0)
         cout << b;
         b--;
 c=i;
    cout<< c;i++;
}}
```

;)

---

### Post by LaRoza on 2007-06-19
I hope your are not serious. I use similar styles for all of my coding.

---

### Post by Ubuntist on 2007-06-19
Thanks for the hints.  Just to clarify, I'm not using Ruby for web development (I don't even know how to do that) -- just for some numerical work.

---

### Post by Doovoo on 2007-06-19
> **finer recliner said:**
> i  havent used python. but my experience with ruby has been given me mixed feelings.

pros:
code blocks, easy loops, OO, built in debugger

cons,
-block comments look like code
-do-while loops are terrible
-using variables in strings were better implemented in perl. in ruby its confusing to use the #, and the { } makes it hard to read. ie:
```
 x = "dave"
puts "hello, #{x}! how are you?" 
```
You can always do 
```
puts "hello " + x + "! how are you?"
```
as well, but isn't Perl's method of putting variables in strings almost the same (only using $ instead of #)?

---

### Post by pmasiar on 2007-06-19
> **Smygis said:**
> That you cant write clean code like:


And how much worse is the Python variant? I do not see any obvious significant difference - especially in 5-liners like that.

Only thing you might miss is b++ instead of b+=1. What else?

---

### Post by Smygis on 2007-06-19
> **pmasiar said:**
> And how much worse is the Python variant? I do not see any obvious significant difference - especially in 5-liners like that.

Only thing you might miss is b++ instead of b+=1. What else?

I think somebody missed the 100x20 meter sign with the text *SARCASM* on it ;)
I think you shuld read my nice peace of C++ code again. its a 13-liner, Not a 5-liner.

---

### Post by LaRoza on 2007-06-19
> **pmasiar said:**
> 
Only thing you might miss is b++ instead of b+=1. What else?

You can increment with +(+b) also.

---

### Post by Dylnuge on 2007-06-19
...Its an 8-liner, smygis.

---

### Post by Smygis on 2007-06-19
> **Dylnuge said:**
> ...Its an 8-liner, smygis.

If it had ben correctly indented it would be 14 lines. But one interesting thing is that the inner while-loop is correctly indented. But thers no {} around it, I figured not many wuld see that. Thats an interestig point. Many complain about that you control the blocks of code with spaces xor tabs in Python.

But hey, You write your [language] code the same way. And expect it to look that way. And dont realy see the HERETHEWHILELOOPBEGINSIFYADINTNOICE and OMFGTHEWHILELOOPENDSHEREFTW.

---

### Post by Ubuntist on 2007-06-21
> **vexorian said:**
> [T]he reasons you used to pick python are quite meaningless.

Python's greater maturity and larger community matter to me, because they mean that there are more pre-existing solutions to problems I want to solve.  For example, for numerical work there's the SciPy project. Ruby has something similar, namely SciRuby, but last time I checked its website it was more of an aspiration than a reality. Or if I want to use the R statistics package within my code, there is already an R-Python interface. To my knowledge, nothing of the sort exists for Ruby.

As I mentioned before, on the whole I like the Ruby language itself just a little better than the Pyhton language itself. To me (and this is just a personal opinion), programming in Ruby is just a bit more fun and free flowing.  Ruby sacrifices a bit of purity and consistency for ease of writing code (although maybe not for reading it). But I like Python too; both languages are big improvements on others that I've used in the past.

---

### Post by pmasiar on 2007-06-21
> **Ubuntist said:**
> Ruby sacrifices a bit of purity and consistency for ease of writing code (although maybe not for reading it).

One of the key insights Guido has was: code is being read much more times than being written, so optimizing for writing is missing the real point.

I think this point is easier to understand if you have Perl experience (which is jokingly called "write-only" language for a reason :-) )

---

### Post by Jessehk on 2007-06-21
> **Ubuntist said:**
> Python's greater maturity and larger community matter to me, because they mean that there are more pre-existing solutions to problems I want to solve.  For example, for numerical work there's the SciPy project. Ruby has something similar, namely SciRuby, but last time I checked its website it was more of an aspiration than a reality. Or if I want to use the R statistics package within my code, there is already an R-Python interface. To my knowledge, nothing of the sort exists for Ruby.

As I mentioned before, on the whole I like the Ruby language itself just a little better than the Pyhton language itself. To me (and this is just a personal opinion), programming in Ruby is just a bit more fun and free flowing.  Ruby sacrifices a bit of purity and consistency for ease of writing code (although maybe not for reading it). But I like Python too; both languages are big improvements on others that I've used in the past.

That's the reason I prefer Python too. :)

```

class String
  def strip_whitespace
    gsub( /\s+/m, '' )
  end
end

puts "Hello,\t  there!\n".strip_whitespace

```

May be lots of fun to write, but something like this:

```

import re

def strip_whitespace( string ):
    whitespace = re.compile( "\s+", re.MULTILINE );
    return re.sub( whitespace, '', string )
    
print strip_whitespace( "Hello,\t there!\n" )

```

Is, in my opinion, far better in the long term.

---

### Post by pmasiar on 2007-06-21
Of course this is using brute force of regular expression.

To remove witespaces, you can do just: 
```

sss = "Hello,\t there!\n"
print ''.join(sss.split())

```

because split with no arguments splits on any whitespace. This is another example of Python sensible defaults which work 80% of the time.

---

### Post by ButteBlues on 2007-06-21
> **Jessehk said:**
> That's the reason I prefer Python too. :)

```

class String
  def strip_whitespace
    gsub( /\s+/m, '' )
  end
end

puts "Hello,\t  there!\n".strip_whitespace

```

May be lots of fun to write, but something like this:

```

import re

def strip_whitespace( string ):
    whitespace = re.compile( "\s+", re.MULTILINE );
    return re.sub( whitespace, '', string )
    
print strip_whitespace( "Hello,\t there!\n" )

```

Is, in my opinion, far better in the long term.
It can be much cleaner.

Try this (Ruby):

```
puts("What is your name?\n\n")
name = gets.strip
puts("Hello there, #{name}!")
```

---

### Post by Jessehk on 2007-06-21
The specific code was not what was being hightlighted, only the look and feel of a solution. I'm aware that other solutions exist (even built-in methods), but the point was to contrast a similar intent in both languages, not to compare features themselves.

---

### Post by ButteBlues on 2007-06-21
> **Jessehk said:**
> The specific code was not what was being hightlighted, only the look and feel of a solution. I'm aware that other solutions exist (even built-in methods), but the point was to contrast a similar intent in both languages, not to compare features themselves.
Fair enough. :)

---

### Post by winch on 2007-06-21
If the point was to compare a similar intent why was the same approach not used in both languages?

```

def strip_whitespace( string )
    whitespace = Regexp.new( '\s+', Regexp::MULTILINE )
    string.gsub( whitespace, '' )
end

puts strip_whitespace( "Hello,\t there!\n" )

```

```

import re

def strip_whitespace( string ):
    whitespace = re.compile( "\s+", re.MULTILINE );
    return re.sub( whitespace, '', string )
    
print strip_whitespace( "Hello,\t there!\n" )

```

---

### Post by Jessehk on 2007-06-21
> **winch said:**
> If the point was to compare a similar intent why was the same approach not used in both languages?
<SNIP>


That's a good point. :)

 I guess my only defence is that seeing Ruby code like that would be very uncommon. Most people in the Ruby community (and I know I'm making a generalization here) would probably write it more similar to the way I did. In other words, my impression is that the less clear, though more concise solution is almost proffered by the community.

Keep in mind, I love Ruby. I think it's a lot of fun, and certainly very elegant. The only complaint I have is the mindset of the community which seems to prefer cleverness over readability and straightforwardness (new word? ;) ) (and I say that with **very** limited experience, so take it with a grain of salt.)

---

### Post by Reb on 2009-04-25
> **LaRoza said:**
> You can increment with +(+b) also.Ok, dredging something up here, but: you can't increment like that in C++, can you? Was/is that what he's talking about? That'll just return you b. Same would happen in Python or Ruby, iirc.

---

### Post by yktula on 2010-03-10
> **Ubuntist said:**
> I've been bouncing back and forth between Ruby and Python, learning a little of each and trying to decide which I like best by applying each to successively larger projects.

At this point, I like Ruby a little better on the whole, but I think Python's greater maturity and larger community outweigh Ruby's advantages.  The thing is, I'm now in the midst of a project for which I've written about 2000 lines of Ruby.  So...
[LIST=1]
[*]Is there a Ruby-to-Python converter available?
[*]Is it possible to call Ruby from Python or *vice versa?*
[*]One Ruby feature I'm really going to miss is code blocks; has anyone figured out how to fake these in Python (the way that implicit accessors can be faked)?
[/LIST]

A response to your first two questions: see
[http://stackoverflow.com/questions/2413878/calling-python-from-ruby](http://stackoverflow.com/questions/2413878/calling-python-from-ruby)
and [http://www.goto.info.waseda.ac.jp/~fukusima/ruby/python/doc/]("http://www.goto.info.waseda.ac.jp/%7Efukusima/ruby/python/doc/")
The latter would be great, but it's hasn't been updated in over 10 years.

An idiomatic solution to the problem mentioned in your third question would be to (usually) just use lambdas and list comprehensions in Python.

Also, someone offered the insight that code is being read more often than it is written in support of Python. This is in fact mentioned in the PEP 8, but it's also why brevity is important. At a more superficial level, this, and the notion of the "Principle of Least Surprise" are two of the reasons I like Ruby. They are not reasons I prefer it as a language compared to Python, nor are they reasons that push me away from Ruby.

---

