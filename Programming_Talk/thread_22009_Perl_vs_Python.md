---
title: "Perl vs Python"
date: 2005-03-25
forum: Programming Talk
---

### Post by defkewl on 2005-03-25
I know that some people here are Python mania. But is Python much better than Perl in getting the job done: making easy job easier and making difficult job possible. I have learned Perl some time ago and it is quite nice especially the regular expressions. I'm thinking about making Python a solution maker upon Perl and I need some considerations.

What do you people think? Is Python a better solution than Perl? Or is it uncomparable since they both have their own purposes?

---

### Post by jamin_l on 2005-03-25
Have you considered Ruby?  Regular expression support on par with and possibly exceeding Perl, and an object model that's at least on par with Python's.  Plus, cleaner syntax.

---

### Post by dataw0lf on 2005-03-25
Ah, ye old Perl versus Python debate.  
As far as regular expressions go, Python has regular expressions just like Perl does.  Python, however, deals with regexs much like it does everything else: as objects, with methods, etc.  
Python is much, much easier to read than Perl, even Wall has stated that "there are too many ways to accomplish a simple task in Perl.".  This isn't a feature;  it tends to make code unreadable, and as the old joke goes, go back and try to read your Perl code 6 months after writing it.
I'd invite you to read Eric Raymond's amazing [essay](http://www.linuxjournal.com/article/3882)  on Perl versus Python.
It really depends on the programmer, but, personally, I don't write anything in Perl anymore.  Python, and on the web side, PHP, fulfill everything I used to use Perl for.

---

### Post by defkewl on 2005-03-26
[QUOTE=dataw0lf]Ah, ye old Perl versus Python debate.  
[/QUOTE]

No I'm not making a debate just a discussion for a better solution. As I noted before whether Perl and Python are simply two different tools for accomplishing two different tasks. 

Yes indeed Python has a very clean syntax, but is that much more important than the language feature. What I don't get quite comfortable with Perl is the OOP concept, it's a modification from what it already has.

Anybody else has some experience with these two? I've never used it in real world scenario yet, I've only learn the language. I'll get back more on this after I study them both.

Thnx

---

### Post by TjaBBe on 2005-03-26
Too bad you didn't make this a poll ;). I love polls :D. This would be an interesting thread for me to follow, as I am trying to learn more of both languages. So keep it up :D.

---

### Post by Quest-Master on 2005-03-26
I still prefer Python over just about every language I've learned up till today.

That should tell you something. :)

---

### Post by defkewl on 2005-03-26
Python would be much more nicer if it has a large repository like CPAN.

---

### Post by jamin_l on 2005-03-26
[QUOTE=defkewl]Anybody else has some experience with these two? I've never used it in real world scenario yet, I've only learn the language. I'll get back more on this after I study them both.[/QUOTE]

Python has a bit more syntactic supprt for object-oriented programming.  Ok, a *lot* more, but, it's still fairly hackish.  Prepending an instance member name with underscores to make it private?  That's absurd.

Additionally, it's not that difficult to do OO programming in Perl.  Tedious at times, yes, but not difficult.

[That said...](http://www.ruby-lang.org)  ;)

---

### Post by thumper on 2005-03-26
[QUOTE=defkewl]No I'm not making a debate just a discussion for a better solution. As I noted before whether Perl and Python are simply two different tools for accomplishing two different tasks. 

Yes indeed Python has a very clean syntax, but is that much more important than the language feature. What I don't get quite comfortable with Perl is the OOP concept, it's a modification from what it already has.

Anybody else has some experience with these two? I've never used it in real world scenario yet, I've only learn the language. I'll get back more on this after I study them both.

Thnx[/QUOTE]
 I use both python and perl at work.  However perl mostly for updating and modifying existing scripts, and python for any new work.

Both languages can be used to handle the same sort of tasks.  I know a lot comes down to personal preference, however I don't know many people who know both perl and python that don't prefer python.

Tim

---

### Post by defkewl on 2005-03-28
Many said that you use Perl for system administration task and reporting while for bigger scale project use Python instead. For larger project using Perl could get really nifty since the readibility is not as good as Python. 

Also, is it much easier for web programming using Python? Also for GUI programming with Tk, which one is easier? Anyone has got comments on this?

Thnx

---

### Post by poster_nutbag on 2005-03-29
I vote for Python, but for text-orientated stuff (parsers and the like) I'd still choose Perl. However, at 1000+ lines of code python becomes much easier to manage.

---

### Post by defkewl on 2005-03-30
Speaking of code management I got confused with the Class syntax in Python.

fibo.py
```
class Fibo:
	def __init__(self,n):
		self.n=n
		
	def fib(n):    # write Fibonacci series up to n
		a, b = 0, 1
		while b < n:
			print b,
			a, b = b, a+b

	def fib2(n): # return Fibonacci series up to n
		result = []
		a, b = 0, 1
		while b < n:
			result.append(b)
			a, b = b, a+b
		return result
```

How do I make an instance from Fibo class and call fib(n)?

---

### Post by Quest-Master on 2005-03-30
[QUOTE=defkewl]Speaking of code management I got confused with the Class syntax in Python.

fibo.py
```
class Fibo:
	def __init__(self,n):
		self.n=n
		
	def fib(n):    # write Fibonacci series up to n
		a, b = 0, 1
		while b < n:
			print b,
			a, b = b, a+b

	def fib2(n): # return Fibonacci series up to n
		result = []
		a, b = 0, 1
		while b < n:
			result.append(b)
			a, b = b, a+b
		return result
```

How do I make an instance from Fibo class and call fib(n)?[/QUOTE]
 ```

x = Fibo()
x.fib(22)

```

---

### Post by poster_nutbag on 2005-03-30
[QUOTE=defkewl]

fibo.py
```
class Fibo:
	def __init__(self,n):
		self.n=n
		
	def fib(n):    # write Fibonacci series up to n
		a, b = 0, 1
		while b < n:
			print b,
			a, b = b, a+b

	def fib2(n): # return Fibonacci series up to n
		result = []
		a, b = 0, 1
		while b < n:
			result.append(b)
			a, b = b, a+b
		return result
```

How do I make an instance from Fibo class and call fib(n)?[/QUOTE]

```

new_instance=Fibo(n)
new_instance.fib(n)

```

However, your code defines self.n in the constructor, and then never uses it, so you can cut out that init() and instead use

```

new_instance=Fibo()

```

Hope that helps

---

### Post by scoon on 2005-03-30
Hey All, 

For me there is no question.  I have been using perl since 1998, I am a Senior Application Dev at a bio-tech company and I am there to code Perl.  I am also a sun certified java programmer but prefer Perl to java.  I have looked at python but really just came up with "if it aint broke, don't fix it".  I think the tendency for one person to use perl or python really comes from the situation that they get introduced to it.  Perl was introduced to me in college and I stuck with it.  Whos to say if python was introduced then that I'd be using Perl now.  


scoon

---

### Post by defkewl on 2005-03-31
No you it doesn't even work if I take out the init()

When I tried it it gave out this message:
```
Traceback (most recent call last):
  File "cobafibo.py", line 4, in ?
    print x.fib(5)
TypeError: fib() takes exactly 1 argument (2 given)
```

Why does it say that I gave two argument? See this is what's so weird about python.

---

### Post by vague- on 2005-03-31
[QUOTE=defkewl]No you it doesn't even work if I take out the init()

When I tried it it gave out this message:
```
Traceback (most recent call last):
  File "cobafibo.py", line 4, in ?
    print x.fib(5)
TypeError: fib() takes exactly 1 argument (2 given)
```

Why does it say that I gave two argument? See this is what's so weird about python.[/QUOTE]

I am no Python expert, but I think the problem lies in you not having declared the method with two arguments.  Python instance method declarations need an explicit reference to the object, the parameter is often named "self".  If you want to create static methods, then you need to go on a little dance -- I would suggest Google or the tutorial for that.

To answer directly, it says you need two arguments because the method does.  It needs an "n" passed explicitly to perform it's calculations, it needs an instance reference passed implicitly because it is an instance method.

If you intend to use the "n" from your constructor, then you only need the instance argument at the method definition and no argument at invocation.  You can just use the instance member to hold the value.

Sorry if that is not clear, just say what is not and I'll try to fix it.

---

### Post by defkewl on 2005-03-31
Okay I've fixed it.

Here we go:
fibo.py
```
class Fibo:
	def __init__(self,n):
		self.n=n
		
	def fib(self):    # write Fibonacci series up to n
		a, b = 0, 1
		while b < self.n:
			print b,
			a, b = b, a+b

	def fib2(self): # return Fibonacci series up to n
		result = []
		a, b = 0, 1
		while b < self.n:
			result.append(b)
			a, b = b, a+b
		return result
```

tryfibo.py
```
x=Fibo(5)
x.fib()
print x.fib2()
```

Okay here is my question:
1. In tryfibo.py, x.fib does not take any argument while in the fibo.py I have defined one parameter which is self. See this is very confusing and inconsistent. Any other programming lang do not do this.

---

### Post by jdonnell on 2005-03-31
[QUOTE=defkewl]
Okay here is my question:
1. In tryfibo.py, x.fib does not take any argument while in the fibo.py I have defined one parameter which is self. See this is very confusing and inconsistent. Any other programming lang do not do this.[/QUOTE]

Huh? It's really not complicated. When declaring a method of an object the first paramater has to be self and is required. When you use the method self is passed automatically. Note that I only pass one argument with instance.myMethod('hello world') but I declare it as def myMethod(self, x):


```

#!/usr/bin/python

class TestClass:
    def myMethod(self, x):
        print x

instance = TestClass()
instance.myMethod('hello world')

```

It is different, but it only takes a second to figure out what is going on unlike perl which has all kinds of craziness like 

open(outfile, ">/some/directory/file.out");
or
```
while () {
    print outfile "$_\n";
}
```
or
```
while (<>) {
    print $_;
}
```

---

### Post by mr_ed on 2005-03-31
That's not true.  **Smalltalk** uses self as well.  That's the language I used the most in university.  Very nice.
Python's syntax reminds me of it; that's probably why Python is my favourite language now.

---

### Post by defkewl on 2005-03-31
[QUOTE=jdonnell]
```

#!/usr/bin/python

class TestClass:
    def myMethod(self, x):
        print x

instance = TestClass()
instance.myMethod('hello world')

```

[/QUOTE]

In Perl:
```

package Hello;

use warnings;
use strict;

sub new{
  my $class= shift @_;
  my $self={@_};
  bless($self, $class);
  return $self;
}

sub mymethod{
  my $self=shift @_;
  my ($x)=($self->{x});
  return $x;
}

1;

```

```

BEGIN{
  push @INC, './lib';
}

use warnings;
use strict;
use Hello;

my $instance=Hello->new(x=>'Hello World');
print $instance->mymethod();

```

See I insert the same amount of parameters as the argument. Much more easier to understand.

---

### Post by wtd on 2005-03-31
[QUOTE=mr_ed]That's not true.  **Smalltalk** uses self as well.  That's the language I used the most in university.  Very nice.
Python's syntax reminds me of it; that's probably why Python is my favourite language now.[/QUOTE]

If you liked Smalltalk you'd probably like Ruby even more.  :)

---

### Post by jdonnell on 2005-04-01
[QUOTE=defkewl]
See I insert the same amount of parameters as the argument. Much more easier to understand.[/QUOTE]

In general the python code I posted looks a lot easier than your perl code :)
If you like perl me then go ahead and stick with it. I think a newbie could look at our two code examples and get an idea of which they like better. I personally like that python code much more than the perl code.

---

### Post by defkewl on 2005-04-02
Perhaps I must admit that Perl OO is not as good as Python which already started as an OO lang.

---

### Post by scoon on 2005-04-02
[QUOTE=defkewl]Perhaps I must admit that Perl OO is not as good as Python which already started as an OO lang.[/QUOTE]


What does "not that good" mean to you ?

scoon

---

### Post by stateq2 on 2005-04-02
Perl seems fine while writing....but when I work w/ it over time, I find myself hating it.  Compared to python, it looks like chicken scratch

---

### Post by scoon on 2005-04-02
hey there, 

ha.  chicken scratch.  that is funny. 

i call that obfuscation.

scoon

---

### Post by defkewl on 2005-04-04
So I conclude that most people accept Python better and tend to leave the cryptic Perl.

How is Python for CGI Programming?

---

### Post by jdonnell on 2005-04-04
[QUOTE=defkewl]
How is Python for CGI Programming?[/QUOTE]

Python is fine for cgi, but why would you want to do cgi where the interpreter is started for every page request? Personally, I think php is far more mature for web stuff than python so I use php even though I like python better as a language.

---

### Post by JeffS on 2005-04-04
I've never done serious work with either Python or Perl, just minor scripts in my spare time. 

Looking at both, Python has by far the easier, cleaner, more maintainable syntax, but Perl has the greater flexiblity, and seems superior at parsing text (probably it's greatest strength).  

And by all benchmark tests I've ever read, Perl is definetly faster and uses less computer resources.   However, when it comes scripting and using any halfway modern hardware, the difference is negligable.

If I were to do a small scale project  that requried lot's of text parsing, I would go with Perl.  If I were doing dynamic server side web pages, I would go with PHP.  Anything else, I would go with Python.

Python seems to be the scripting language with most of the momentum these days.  It's clean syntax, easy maintainablity, full OOP, good expressions, relative flexibility, and quick development, all seem to attracting developers in droves.  It seems there is a very large Perl to Python migration going on, but nothing in the other direction (although Perl usage remains strong).  This says quite a lot.

It seems that Python meets most higher level, rapid development needs.  The only area where it fails is speed.  But again, that is usually negligable.

---

### Post by jdonnell on 2005-04-04
[QUOTE=JeffS]  The only area where [python] fails is speed.  But again, that is usually negligable.[/QUOTE]

It's more than negligable when man hours are much more expensive than hardware. I encourage all my competitors to use c++ while I use python ;)

---

### Post by JeffS on 2005-04-04
[QUOTE=jdonnell]It's more than negligable when man hours are much more expensive than hardware. I encourage all my competitors to use c++ while I use python ;)[/QUOTE]

I know you're kind of kidding because of the wink, but one would never use Python and C++ for the same type of project.  C++ is best for systems level programming, or programming games.  A scripting language like Python would be terrible for those application domains.  However, for dynamic, rapidly developed applications that maninpulate data, and where speed is not essential, there is hardly anything around that would be better than Python.

As the saying goes, the different languages are just different tools in the programmer's toolbox.

---

### Post by defkewl on 2005-04-04
[QUOTE=jdonnell]Python is fine for cgi, but why would you want to do cgi where the interpreter is started for every page request? Personally, I think php is far more mature for web stuff than python so I use php even though I like python better as a language.[/QUOTE]
 Ok thanks for the input. I'm using PHP too currently, but it's very difficult to manage the code when the application grows bigger. For that I use JSP too, but the problem is that there is a small number of hosting that support JSP as cheap as PHP hosting.

---

### Post by defkewl on 2005-04-05
So would you guys share with me what do you use python for since python is not proper for CGI programming.

thnx

---

### Post by jdonnell on 2005-04-05
You can use python for the same type of stuff as cgi, just not via cgi. Look up mod_python, spyce, cherrypy, subway, webware, etc. These are all options for doing web sites with python where the interpreter isn't started and stopped for each request. 

I use python for everything other than web stuff which I use php for. Often I'll only use php as a frontend for a python script :) I do SEO work so I use python for all the SEO tools I make.

---

### Post by wtd on 2005-04-05
[QUOTE=defkewl]So would you guys share with me what do you use python for since python is not proper for CGI programming.[/QUOTE]


The thing is... very few people still do straight CGI programming.  Most work these days is done through some web application development framework.  Things like Ruby on Rails are where it's at these days.

---

### Post by bfree on 2007-06-05
Use the right tool for the right reason. If you choose to use Python because it enforces a particular coding style, or its syntax simply makes more sense to you - great. 

My distaste for Python stems from the fact that it breaks with C/C++ syntax - without adding any new functionality that is not already supported by Perl, Java and JavaScript. If you are going to change paradigms and learn a new language, Ruby makes far more sense, as it actually offers new features not offered by these languages. 

Another consideration regarding Perl vs Python: performance. [Benchmarks]("http://graphcomp.com/pogl.cgi?v=0111s3B2") show that Python has some serious issues dealing with arrays. To work around this problem, developers have introduced a ctypes module, and Python has recently introduced NumPy (Numerical Python) arrays - however, performance continues to lag in certain applications such as OpenGL (see [http://graphcomp.com/opengl/benchmarks](http://graphcomp.com/opengl/benchmarks)). 

I use Perl mainly for building LAMP-based online services - which relies heavily on string handling and templates (blocks of text with embedded variables/functions). Perl is designed/tuned for this. 

Python automatically adds an EOL at the end of each print; if you disable this, it automatically adds a space at the end... you end up using write, instead - it feels like programming in BASIC. Python's print provides no way to enable unbuffered I/O - you need to flush each call. You need to convert lists to tuples before you can print. There's no easy way to embed variables within a multi-line text block (Perl's qq). 

For all the positive things that one might say about Python, string handling and output is not one of them. 

A personal nit is the lack of a way to ifdef out code for prototype/debugging purposes. In Perl you can just wrap your code block in an "if" - in Python, you have to reformat the entire code block, then reformat again once you remove the ifdef - wreaks havoc on source control and diffs. 

The one positive thing I would say about Python is that it forces all parameter passing to be by reference, rather than by value - which is a good thing in an interpretive language (that's not to say you can't do this in Perl, as well). 

This is offset by the fact that there is no easy way to retrieve a key from a hash (dict) reference - you are forced to enumerate the dict - whereas in Perl, you can treat a single-element hashref as an arrayref to retrieve its key - and this becomes critical in Python since you can only pass by reference.

---

### Post by pmasiar on 2007-06-05
It was interesting to read Python warts from 2 years ago... most of them solved.

[http://cheeseshop.python.org/pypi](http://cheeseshop.python.org/pypi) is Python's CPAN, distutils improved a lot, we have leading web frameworks: Django, TurboGears and Pylons (for different niches), and looks like Python 3000 will be out in 2008, way before Perl6 (which still does not have timeline), see [Python 3000 timeline](http://www.python.org/dev/peps/pep-3000/#timeline)

Other for historical/compatibility reasons, I do not see reason to use Perl over Python for any serious new development. Perl is obviously being replaced by Python and Ruby. It will take some time, but it will happen - Perl lost the most important asset: mindshare as "duct tape of the internet".

But there are still people who love and prefer Perl, and misunderstand Python. Let's see the facts:

> **bfree said:**
> My distaste for Python stems from the fact that it breaks with C/C++ syntax - without adding any new functionality that is not already supported by Perl, Java and JavaScript.

New language may make sense if allows to access functionality in simpler, cleaner, easier to use way. Perl, Java and Javascript have serious warts, and Python tried (and IMHO succeeded) to have positives without the negatives. There is no shame in stealing good features and packing them in better way.

> If you are going to change paradigms and learn a new language, Ruby makes far more sense, as it actually offers new features not offered by these languages. 

Any examples what important features are lacking in Python?

> Another consideration regarding Perl vs Python: performance. 

Neither Perl or Python are fastest languages as-is. But Python has compiler and efforts to improve speed are ongoing. I already mentioned status of Perl development.

> Python automatically adds an EOL at the end of each print;

Looks like your code prints HTML string by string. No wonder you have a mess: Use MVC and templates instead.

> Python's print provides no way to enable unbuffered I/O - you need to flush each call. 

This one is valid AFAICT - anyone knows a fix?

> You need to convert lists to tuples before you can print. 

It's not a bug, it is a feature. :-) Why you need that?

> There's no easy way to embed variables within a multi-line text block (Perl's qq). 

Tripple-quote creates multi-line string, and standard text interpolation with % works like in normal strings. So i am not sure what is the problem.

> For all the positive things that one might say about Python, string handling and output is not one of them. 

What? Seems to me you do not know Python too deeply. What exactly is the problem? Of course string handling is little different - it is more object oriented, and regex are in library and not part of the language - but being in library adds flexibility - development at different speed.

> A personal nit is the lack of a way to ifdef out code for prototype/debugging purposes. In Perl you can just wrap your code block in an "if" - in Python, you have to reformat the entire code block, then reformat again once you remove the ifdef - wreaks havoc on source control and diffs. 

Did you tried this trick? Why it is not enough?
```

if 1=0: 
    # disabled block

```

> The one positive thing I would say about Python is that it forces all parameter passing to be by reference, rather than by value - 

Not true. immutable objects pass by value (scalars, tuples, strings)

> This is offset by the fact that there is no easy way to retrieve a key from a hash (dict) reference - you are forced to enumerate the dict - whereas in Perl, you can treat a single-element hashref as an arrayref to retrieve its key 

Not sure why you need that trick, but you can do (off top my head without thinking hard):
```

>>> dd = dict(k='val')
>>> dd[dd.keys()[0]]
'val'

```

Why is this not good enough? Am I missing something?

Seems to me that you are old Perl hacker, set in his ways and reluctant to accept that in lew language there are new ways to accomplish same effects. I might be wrong - but let's try solve misunderstandings on facts, without flames.

I know I missed fancy Perl slices @hashname{@listname} IIRC syntax. In Python you have list comprehension instead: 
[ hashname[x] for x in listname] gives the same result, is more universal and easier to read for ocasional user too.

IMHO, YMMV. maybe i am not as sophisticated perl hacker like you and i do not miss the deep hacks you do. :-)

---

### Post by bfree on 2007-06-05
> **pmasiar said:**
> Seems to me that you are old Perl hacker

Actually, no - I'm an old C/C++ developer (and Java, Forth, APL, assember, etc).  I simply believe Ruby is a better language than Python.

If anyone is inclined to migrate away from Perl - it's my bias that they should go to a language that actually provides new functionality, and is not hampered by Python's performance issues.

But I'm not here to convince you or anyone else to switch from Python, Perl or any other language that you hold dear ;)

---

### Post by pmasiar on 2007-06-05
> **bfree said:**
> If anyone is inclined to migrate away from Perl - it's my bias that they should go to a language that actually provides new functionality, and is not hampered by Python's performance issues.

Second time you claim new functionality and performance issues where Ruby is better than Python. Any details, references, links? Or is it just a bias too? :-)

---

### Post by bfree on 2007-06-05
> **pmasiar said:**
> Second time you claim new functionality and performance issues where Ruby is better than Python.

My background is 3D software development (been doing it since 1973) - which makes performance and portability key criteria for me.

My performance comments were regarding Perl vs Python; my initial post referred to recent OpenGL benchmarks comparing C, Perl and Python - where Python's array handling suffers in comparison.  While some of this is due to PyOpenGL's implementation (see comments by PyOpenGL's author), and the benchmark's design (Trislam) - Python's ctypes and NumPy are clearly slower than Perl's equivalent.  I do hope to post Ruby benchmarks shortly.  [http://graphcomp.com/opengl/benchmarks](http://graphcomp.com/opengl/benchmarks)

Aside from performance, I'll happily accept bias on my part regarding language preference.  In my line of work, I am constantly sharing/porting code between languages.  Many math implementations are still in C, or even FORTRAN; researchers still use Perl or even APL.

As such, part of my bias is due to a premise of Python's: do things one way; Perl/Ruby's approach of allowing multiple methods for doing things may lead to messier code - but it does improve time-to-market and allows for incremental porting between languages.

As for features supported in Ruby and not Python - they mainly involve Python's general bias against functional programming, anonymous blocks, closures, open classes.

Aside from performance - the real argument is whether or not limiting developer choices in terms of style/paradigm is a good thing or not.  It's my impression that the Python community believes this is a good thing; to me it's a throwback to PASCAL.

---

### Post by pmasiar on 2007-06-05
> **bfree said:**
> My performance comments were regarding Perl vs Python; my initial post referred to recent OpenGL benchmarks comparing C, Perl and Python - where Python's array handling suffers in comparison. 

Perl is older, so libraries might be more optimized. Work on Python is continuing - companies like Google pay for developers and to work on it (and for sprints). Seems like you have no *real hard data* on Ruby being faster than Python yet. We'll see.

> I'll happily accept bias on my part regarding language preference.  In my line of work, I am constantly sharing/porting code between languages. 

I accept that Ruby is closer to Perl than Python is - IMHO being closer to Perl is a bug :-)

> As such, part of my bias is due to a premise of Python's: do things one way; Perl/Ruby's approach of allowing multiple methods for doing things may lead to messier code - but it does improve time-to-market and allows for incremental porting between languages.

Seems like you have no data about this, just gut feeling. OTOH improved readability (in opinion of many) increases "speed to the market" and simplifies maintenance.

> As for features supported in Ruby and not Python - they mainly involve Python's general bias against functional programming, 

Python is considered as multi-paradigm language. You can write procedural, OOP, or even functional code if you want: [Functional programming in Python](http://www.ibm.com/developerworks/library/l-prog.html). It might be not Lisp, but I do not see any obvious huge gaps, comparing to Ruby or Perl.

> anonymous blocks, 

[	The "with" Statement](http://www.python.org/dev/peps/pep-0343/) is not 100%, but in opinion of many solves most of use cases. Added in Python 2.5

> closures, 

[Closures](http://www.ibm.com/developerworks/library/l-prog2.html) and [ Memento Closure recipe](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/413838) - and Python also has yield statement, so it's possible to define generators.

> open classes.

I am not such OOP expert myself, but this is I found about lack of  [open classes](http://mail.python.org/pipermail/python-list/2006-July/394942.html) in Python: it is not a bug - it is a feature (with explanation why). 

> Aside from performance - the real argument is whether or not limiting developer choices in terms of style/paradigm is a good thing or not.  It's my impression that the Python community believes this is a good thing; to me it's a throwback to PASCAL.

This is IMHO pure gut feeling, I really like Python mantra "there should be one obvious way to do it right" and "do it right" is often the simplest and "most elegant" way. Reuse round wheel provided by the system to get things done, fast.

I do not intend to convert you to Python if you don't like it. Reason why I wasted this time is if someone else will be deciding between Perl, Ruby and Python, and would read only your opinion, she might get (IMHO) single-sided understanding of the issues.

I myself do not use those esoteric features you "miss" in *my* daily programming, I might be not sophisticated enough to miss them in any language :-) I like that I can write code without constant checking libraries and reference - Python syntax is so obvious it fits nicely in my overwhelmed brains...

---

### Post by KaeseEs on 2007-06-05
Coming from a background primarily in C/++ and Java, I have issues with Python's basic philosophy, wherein developers are expected to do things the 'pythonic' way.  It's conceptually similar to having an application framework (or perhaps a number of mini-frameworks) built into the language, in that it is by nature a restrictive measure included for simplicity's sake when tackling common problems,and it runs into the same basic problem that a framework has.  When one is expected to tackle given problems in a single accepted manner, it becomes more difficult to solve other problems that are not anticipated by the makers of coding conventions.  One is forced to shove square pegs into round holes, and the result is often less than satisfactory.

    As an example of this issue in another context, when I first began working in Java, I was irked by the language's object-oriented constraints.  I couldn't just write a script or a function; I had to wrap everything in a class with a special static method to execute it (the main() interface common to C and its derivatives is a much lighter version of this same annoyance), shoehorning solutions to tasks that were by nature functional or procedural into an object-oriented model.  Eventually, I learnt to simply not use Java to solve problems that didn't fit the OO model well.  This is the common weakness of all languages that try to browbeat the programmer into following a specific paradigm, style, model or framework.  

    Now, the above is not to be understood as an attack on programmatic idioms or patterns; in many (perhaps the majority!) of cases, such things are quite useful tools to the programmer, and their commonality is a strength.  This is what makes the criticism of Perl by Python programmers so ironic - *the very thing that often makes Perl code hard for the uninitiated to read is its heavy reliance on idioms*.  Dense Perl code is usually generated by relying on automatic features of the language that are idiomatic to anybody who's read the Camel book, taken a good class or even just worked with Perl under good tutelage for a while.  I'm calling out the automatic behaviors of <>, $_, $@array &c. that make programming in Perl much simpler and easier, along with numerous other touches.  

    With respect to readability, I will admit readily that badly written Perl is harder to read than badly written Python, if only because any Python that compiles will follow a common indentation style, and the programmer's freedoms in many areas are restricted such that one can generally grok what his code is doing.  However, well-written idiomatic Perl with a sane brace & indent style will be just as readable to a Perl hacker as well-written 'pythonic' Python would be to a Python hacker.

Essentially, I realize that Python's strict adherence to the dogmas of the core language devs is intentional; I am arguing not that it is a bug, but that it is a misfeature, a deliberate but poor decision.

Finally, with respect to the article by Eric Raymond referenced earlier: [fetchmail](http://www.fetchmail.info/design-notes.html).


EDIT:  I forgot to mention, I consider Python to be in its element doing graphical frontends to utilities, and consider it the equal of (and use it before) any other language for this and similar tasks.  Similarly, if I had an accounting app, I wouldn't hesitate to use Java, as that problem fits its OO model perfectly and thus shoehorning issues wouldn't surface.

---

### Post by earobinson on 2007-06-05
python

---

### Post by n0dl on 2007-06-06
Depends on what I am writing. If it has to do something with a Graphical front end or a game, I use python. However, I find myself using Perl more often. Sometimes all i need is a one time run script or a quick cron job that i can use over several computers. Perl is a glue language in the unix world, almost taking over the realm of shell scripting. While Python is more readable (in most cases anyway), I must agree with KaeseEs' arguments about forcing the use of the OOP paradigm. In a sense it robs the flexibility to solve other sorts of problem (which is probably why C style languages are still alive today). OOP is a bit overrated IMO.

---

### Post by guinex on 2007-06-06
Perl and Python are more similar than they are different.  They both have similar performance and latent-typing.   Python has some whitespace-sensitive syntax that some people seem to think is important.  Other people like myself think that program "readability" has much more to do with design and modularity than with whether or not a line needs to end in a semicolon.

Perl has a larger and more mature set of community-maintained libraries (CPAN) than Python.  Perl has real closures (and has had them for a long time).   Perl has optional dynamic-scoping that is occasional quite useful.  Perl has more historical cruft than Python for sure, but it is mostly a non-issue after you figure it out.

Many Perl users take the position that their language should be multi-paradigm, rather than (for example) obsessively object-oriented.  If you want religious (shudder) purity, you are probably better off with ruby or something more esoteric like smalltalk.  That said, you can do OO programming in Perl quite conveniently.  Most of the posts to this thread seem to have been written by people who know little about Perl and are mostly rehashing what they have heard from others.   Here is a more modern example on how to define a couple of classes in Perl (code copied from the CPAN Moose package).


```

package Point;
use Moose;

has 'x' => (isa => 'Int', is => 'ro');
has 'y' => (isa => 'Int', is => 'rw');

sub clear {
    my $self = shift;
    $self->{x} = 0;
    $self->y(0);
}

package Point3D;
use Moose;

extends 'Point';

has 'z' => (isa => 'Int');

after 'clear' => sub {
    my $self = shift;
    $self->{z} = 0;
};

```

Point3D derives from Point and updates its base class's "clear" method to account for its extra "z" attribute.  The "x", "y", and "z" accessors perform validation and will only accept integers.

---

### Post by LaRoza on 2007-06-06
I have been reading this thread for a while, and am wondering if anyone expects to change anyone's mind?

---

### Post by hitodenashi on 2008-12-14
> **pmasiar said:**
> 
I do not intend to convert you to Python if you don't like it. Reason why I wasted this time is if someone else will be deciding between Perl, Ruby and Python, and would read only your opinion, she might get (IMHO) single-sided understanding of the issues.


There you go. You're sounding like a self admitted cultist. If anything your mindset threw me off investing time in learning Python.

---

### Post by mssever on 2008-12-14
> **hitodenashi said:**
> There you go. You're sounding like a self admitted cultist. If anything your mindset threw me off investing time in learning Python.
You're resurrecting a year-and-a-half-old thread just to say that?

---

### Post by pmasiar on 2008-12-14
> **hitodenashi said:**
> There you go. You're sounding like a self admitted cultist. If anything your mindset threw me off investing time in learning Python.

Be my guest. 

The more people wate time pushing bits in C++ the more would be people being able to actually solve problem valuable.

---

### Post by nvteighen on 2008-12-14
Given the traditional issues between Monks and Pythonistas, I really please, please, please, please ask this thread to be closed, please, please, please, please. [-o<

---

### Post by nielz on 2008-12-14
> **jdonnell said:**
> Python is fine for cgi, but why would you want to do cgi where the interpreter is started for every page request? Personally, I think php is far more mature for web stuff than python so I use php even though I like python better as a language.

I'm interested in learning why php would be more mature for web stuff than python?

---

### Post by badperson on 2008-12-14
I voted for perl, despite having zero experience using python...:lolflag:

I use perl mainly for what I believe is its great strong point; text manipulation on large xml files. 

I've done only a little OO perl programming, but for me personally, once you start thinking about objects, it's time to start thinking about java. 

As an aside, I'm wondering why ruby, python, and php have outpaced java on the web? 

Also, I've talked to a couple people who work on enterprise scale applications for financial shops that are written in perl, which totally surprised me...I can't imagine what the advantage of perl over java would be. 

edit: just re-read this thread looking at the dates...interesting....

bp

---

### Post by samjh on 2008-12-14
Thread necro FTW!

Is this a record? :p

I vote Python. :D  I have only minimal exposure to Perl, but from what I've read, Python can do anything (useful) Perl can do, with easier and more maintainable code.

---

### Post by pmasiar on 2008-12-14
> **samjh said:**
> Thread necro FTW!

Is this a record? :p

All thank-you notes please to be forwarded to hitodenashi :twisted:

---

### Post by Greyed on 2008-12-15
> **thumper said:**
> Both languages can be used to handle the same sort of tasks.  I know a lot comes down to personal preference, however I don't know many people who know both perl and python that don't prefer python.

This is me.  I wrote Perl professionally for 5 years.  During that time I learned Python.  When I left that company I stopped programming in Perl.  If I absolutely have to I can do it again.  So far, however, I have been able to give a pass to all Perl development jobs.  I'll be ever grateful for my years spent programming Perl but do not at all regret leaving it in the past now that Python is in my toolbox.

BTW, if one wants a general view of this trend of Perl/Python hackers moving to Python take a look at Ohloh.net's stats for Perl and Python.  I included Ruby in the mix since some people have mentioned it here.

[http://www.ohloh.net/languages/compare?commit=Update&l0=python&l1=perl&l2=ruby&l3=-1&l4=-1&measure=commits&percent=](http://www.ohloh.net/languages/compare?commit=Update&l0=python&l1=perl&l2=ruby&l3=-1&l4=-1&measure=commits&percent=)

[http://www.ohloh.net/languages/compare?commit=Update&l0=python&l1=perl&l2=ruby&l3=-1&l4=-1&measure=contributors&percent=](http://www.ohloh.net/languages/compare?commit=Update&l0=python&l1=perl&l2=ruby&l3=-1&l4=-1&measure=contributors&percent=)

[http://www.ohloh.net/languages/compare?commit=Update&l0=python&l1=perl&l2=ruby&l3=-1&l4=-1&measure=projects&percent=](http://www.ohloh.net/languages/compare?commit=Update&l0=python&l1=perl&l2=ruby&l3=-1&l4=-1&measure=projects&percent=)

Monthly contributors, lines of code, number of commits, Perl has been declining since 2001 while Python has been on the rise since about 2001.  Since about late 2005 Python has had more active use in the projects that ohloh tracks than Perl.

Cripes, this was a necro!?  Grrr.  Wasted all that good verbage on a Necro!!!!  >.<

---

