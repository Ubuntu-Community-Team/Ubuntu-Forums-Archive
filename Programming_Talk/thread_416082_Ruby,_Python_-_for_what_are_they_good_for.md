---
title: "Ruby, Python - for what are they good for?"
date: 2007-04-20
forum: Programming Talk
---

### Post by kukibl on 2007-04-20
I am using Linux for 5+ years, but I never tried to learn (actively) some programming language. I know a little bit of Python and C++ syntax (know how to write simple functions nothing more complex), but now I would like to learn some programming language in proper way (sorry on my English).

I find Ruby and Python quite interesting, so I would like to know for what are they good for (what type of programming; what can I program with them in concrete)? Also, I would appreciate if you would be kind to write some examples from real life, specially for Ruby.

Thank you very much for your time and patience!

---

### Post by JT673 on 2007-04-20
Ruby is known for its full blown OO (it has a Proc object, for Pete's sake!) and its flexibility.  Rails is based off of Ruby, and is a fast Web2.0 development tool we've probably unknowningly used.

Python is an equally fast-development language, though I next dabbled too much in it.

---

### Post by ghostdog74 on 2007-04-20
not again.

---

### Post by pmasiar on 2007-04-21
Years ago, [Perl](http://en.wikipedia.org/wiki/Perl) was the ducktape language what hold internet together. It was very popular, because it has extremely powerful operators for manipulating/parsing text, and real guru can whip a 10-line or one page program quickly and make incredible things happen. Perl was first language with philosophy "make simple things easy, and hard things possible". More traditional languages like Java and C/C++ have approach "make hard things possible, even if it makes simple things complicated".

Perl was jokingly called "write-only language" - it is 'easy' to write programs, but it is sometimes hard to read even your own code: too many subtle tricks, like sigils: $x, @x and %x are three different variables (scalar, list and dict), and so on.

[Python](http://en.wikipedia.org/wiki/Python_%28programming_language%29) was inspired by Perl, but made very readable: whitespace is significant, and if program with wrong intendation has syntax error, no sigils, just enough flexibility but not too much.

[Ruby](http://en.wikipedia.org/wiki/Ruby_%28programming_language%29) is about half-way between Perl and Python.

Ruby is mostly used for web apps - Rails made it popular, and needs of Rails drive development of Ruby. 

Python was more popular than Ruby, but web app solutions were too fractioned - joke was that Python has more web app frameworks than keywords. :-) Now dust settled, there is less than half a dozen :-) mainstream Python web app frameworks, Django ("pronounced" as first choice) and Turbogears being also  popular. 

BTW Ruby is developed in Japan, many deep devel maillists are in Japanese. Perl is American, Python was European (Dutch) but author Guido van Rossum moved to USA and now works for Google, all development is in English.

Both Python and Ruby compete in web apps niche and about equally powerful, Python  has more libraries (than Ruby) for specialized areas outside web apps, like numerical processing, images etc, and because it is slightly older and more popular, they say it is faster than Ruby - which you might not care and will make no difference until your website gets 10K hits per sec. :-)

Interesting development recently is that both Microsoft and Sun realized that they need complement their static competing languages (C# and Java) with flexible dynamically, [duck typed](http://en.wikipedia.org/wiki/Duck_typing) language. MSFT woke up first and snatched Python - has own "shared source" version for .NET, [IronPython](http://en.wikipedia.org/wiki/IronPython). Sun woke up later, and got Ruby build on top of Java - JRuby.

I would say that Python as powerful as Ruby and is cleaner looking. OOP purist insist that Ruby is more pure OO, Pythonistas claim Python is more pragmatic and easier to learn. Also, significant whitespace feels strange (first couple hours) and scares people away - I know it scared me, and I wasted couple years on Perl. :-( I also like backing by Google Google uses Python extensively and employs many key Python developers) - many [SoC](http://en.wikipedia.org/wiki/Summer_of_code) projects are for Python or in Python. Ubuntu and Canonical uses Python as main development language.

IMHO Python's focus on readability will win: read [The hundred year language](http://www.paulgraham.com/hundred.html) - and while there, check [Paul Graham](http://en.wikipedia.org/wiki/Paul_Graham) excellent and insightful [essays](http://www.paulgraham.com/articles.html) - he clearly knows what he is talking about.

Try look at links, code examples and make your own choice. To help Python learners I maintain a small wiki with links to useful resources (there are so many:  - I  need to filter out :-) ) - link in my sig.

---

### Post by finer recliner on 2007-04-21
^great response. you helped me as well. thanks :)

---

### Post by kukibl on 2007-04-21
Thank you very much for your answers!

---

### Post by dsl on 2007-04-21
> **kukibl said:**
> I am using Linux for 5+ years, but I never tried to learn (actively) some programming language. I know a little bit of Python and C++ syntax (know how to write simple functions nothing more complex), but now I would like to learn some programming language in proper way (sorry on my English).

I find Ruby and Python quite interesting, so I would like to know for what are they good for (what type of programming; what can I program with them in concrete)? Also, I would appreciate if you would be kind to write some examples from real life, specially for Ruby.

Thank you very much for your time and patience!

If I understand, you don't _need_ to learn a programming language but you wish to do so, just for the sake of learning.

I then suggest Smalltalk. It is an old yet very modern language. The object oriented paradigm is born with Smalltalk. It is easy to learn, many tutorials are available, and some free implementations have good graphical capabilities.

I suggest you try Squeak, which is also in the Ubuntu repositories.

---

### Post by vitality- on 2007-04-22
I can only speak about Python since I use it regularly and have never touched Ruby.  Python to me is great for scripting.  It has has a nice set of libraries for doing things at the system level and requires very few lines of code for the equivalent in other languages.  It's also readable - which is its biggest boon over perl.  I enjoy being able to coherently read my python quick hacks a few months after writing them.

---

