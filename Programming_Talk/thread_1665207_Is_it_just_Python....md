---
title: "Is it just Python..."
date: 2011-01-12
forum: Programming Talk
---

### Post by memilanuk on 2011-01-12
...or do other languages like Perl, Java, PHP, C/C++, etc. have the sort of schism between releases like that between Python 2.x and 3.x?

I like most everything about the language but the ongoing foot-dragging of the community where 3.x has been out for a couple *years* now and there are still major projects out there that are on 2.5 or 2.6 (Google App Engine, wxpython and BeautifulSoup are a few that come to mind) is kind of getting old.  New users want to use 3.x but have to learn 2.x as well because of the amount of legacy code still in active use.  Kind of wish that they'd found a way to make the transition a little smoother, or else some way to force a clean break (probably not feasible).

Is it just Python, or is this kind of internal muck normal/common with other languages at some point in their growth?

---

### Post by Reiger on 2011-01-12
It's common. It's called legacy for a reason.

---

### Post by shadylookin on 2011-01-12
most languages deprecate things, but never actually remove them. 

Though python generally has a philosophy of simplicity and having 1 right way to do things. Supporting legacy stuff tends to break that philosophy.

---

### Post by nvteighen on 2011-01-12
The problem with the transition to Python 3.x is that the changes affect very basic parts of the language. This is a quite unique case, actually: most languages new "releases" just add stuff or modify subtle features that aren't that basic. Take for example, the transition from C89 to C99, which essentially added some C++ features to the standard.

IMO, this was a very unwise move. This is perfectionism: ok, some features weren't quite coherent with Python's design lines (e.g. print as a statement and the range/xrange duplicity), but programming languages are full of these little incoherences or ad hoc features, because they are designed by humans not machines. Python 3.0 seems like another attempt to create the "perfect" programming language by ignoring what people have been doing for years with Python 2.x. Of course you can improve a language, but you should take a look on the impact of your decisions.

There's a great example of a language's revision having a really bad impact: the R6RS Scheme standard. The change was motivated by the usual critique of Scheme being an academic non-practical language... well, the people behind R6RS seem not to realize that Scheme was meant to be like that and that the non-academic practical Lisp dialect is Common Lisp (which was initially created by almost the same people that created Scheme). So, R6RS added a lot of new Common Lisp-ish features that people hated. The new features are useful indeed, e.g. modules, standarization of common non-standard extensions, but people fell that those changes were a radical shift in the language's philosophy. The main consequence: very few Scheme implementations support R6RS (approved back in 2007) and those that do, use R5RS by default. MIT/GNU Scheme (the "original" Scheme implementation) goes as far as using a R4RS/R5RS mix. Now some people are discussing in splitting Scheme into a "Common Lisp-ish R7RS" and a "Scheme-ish Scheme"...

I don't think Python 3.0 will have such a bad impact, but the fact that distros are still using Python 2.6 for stability reasons will surely make its adoption slower than initially thought. But, considering that a lot of people still write K&R-style C or C89 instead of C99 or pre-standard C++, total adoption may never happen.

---

### Post by maximinus_uk on 2011-01-12
I've used 2.x for the last 7 or so years, I know it like the back of my hand hand; The very features that would make me turn to 3.x (more functional style things built into the language, a better lambda() ) are, according to Guido, not going to appear in the near future.

So, is there any really good reason for me to change? Nope, and I'm sure a lot of other people feel the same way.

---

### Post by Cheesehead on 2011-01-12
And yet some of us have already converted all our scripts to 3.x. I didn't see much point developing in and maintaining 2.x - much of that version-specific work would be wasted when upgrade became necessary anyway. 

I loved working in 2.x, and I love working in 3.x too. If you think of it as a classic new-technology adoption curve, then I was an early-adopter and five years from now only a few late-adopters will be left. We're in the middle of the changeover.

A long changeover period doesn't mean some kind of failure - I think it shows a healthy community. More 3.x training materials are appearing, more 2.x modules are being upgraded to 3.x, more 3.x questions are appearing in forums. It's slow, but then many of the authors and maintainers and trainers are volunteers and hobbyists - slow is okay as long as the work is solid. And the work so far has been really good.

---

### Post by ssam on 2011-01-12
might be worth comparing to perl6. which is going very slowly.

or C++0x which has taken a long time and huge effort to minimise compatibility issues [http://www.codeguru.com/cpp/misc/article.php/c18357/An-Interview-with-C-Creator-Bjarne-Stroustrup.htm](http://www.codeguru.com/cpp/misc/article.php/c18357/An-Interview-with-C-Creator-Bjarne-Stroustrup.htm)

---

### Post by worksofcraft on 2011-01-13
> **ssam said:**
> might be worth comparing to perl6. which is going very slowly.

or C++0x which has taken a long time and huge effort to minimise compatibility issues [http://www.codeguru.com/cpp/misc/article.php/c18357/An-Interview-with-C-Creator-Bjarne-Stroustrup.htm](http://www.codeguru.com/cpp/misc/article.php/c18357/An-Interview-with-C-Creator-Bjarne-Stroustrup.htm)

IMO it is compatability issues in Python that are a problem:

While I can compile **ALL** my old C++ code both with or without the -std=c++0x switch, I can get **NOT ANY** of my old Python programs to work with the new versions of Python... I converted them, then last time I tried still had the problem that packages I use (like gst) had not been converted :(

---

### Post by donsy on 2011-01-13
> **nvteighen said:**
> 
I don't think Python 3.0 will have such a bad impact, but the fact that distros are still using Python 2.6 for stability reasons will surely make its adoption slower than initially thought. But, considering that a lot of people still write K&R-style C or C89 instead of C99 or pre-standard C++, total adoption may never happen.

Look for 2.7.x to be around for a long, long time; maybe even forever. IMHO programming languages, should use the same approach that mathematics uses in embedding simpler numbers into supersets as isomorphisms. For example the set of positive integers "a" are embedded into the set of positive rational numbers of the form "a/1" with addition [a/1 + b/1], and multiplication [(a/1)(b/1)] preserved.

---

### Post by cgroza on 2011-01-13
I will change to Python3.x when wxPython and all my favorite libraries will be ported and functional.
Right now wxPython has no port to 3.x and I really need because I am developing an application right now.

---

### Post by nvteighen on 2011-01-14
> **donsy said:**
> Look for 2.7.x to be around for a long, long time; maybe even forever. IMHO programming languages, should use the same approach that mathematics uses in embedding simpler numbers into supersets as isomorphisms. For example the set of positive integers "a" are embedded into the set of positive rational numbers of the form "a/1" with addition [a/1 + b/1], and multiplication [(a/1)(b/1)] preserved.

You've put a nice mathematical description there of what I informally refered to as adding stuff but not touching what was already available.

Of course, and that's what C or C++ have been doing. This doesn't mean I endorse all features these languages added, but the method seems to be right. Obviously, you may need to touch already available features, but only to correct some unexpected behaivor that could affect normal usage of the said feature, similar as when in maths you have to correct hypotheses that aren't good enough. 

If you don't want that, instead of tweaking an already established and used programming language, I guess it's better to take advantage of the "open source" nature of these languages and create new different languages based on the original. That's what the Lisp community has been doing systematically since 1958.

---

### Post by slavik on 2011-01-14
Perl6 is a complete redesign of Perl. Perl6 has a spec, Perl5 has an interpreter.

---

### Post by lugalzagesi on 2011-02-05
Hello,
  I am completely new to Ubuntu 10.4.  I am trying to install google appengine but not having much luck.  i got Python 2.7.1 to install but cannot get google app_engine to install.  I unzipped the files and tried to run the dev_appserver.py as it said in README but it said command dev_appserver.py not found

---

### Post by memilanuk on 2011-02-05
Probably best to start your own thread on this topic rather than hijacking this one; better odds of getting someone to help you.

---

### Post by llanitedave on 2011-02-06
I'm still new to Python, and I made the decision to start clean learning Python 3.1.  I'm starting to internalize a few things, and though I still can't say I'm comfortable with it, I'm making progress.

At the same time, it is kind of frustrating that some cool-looking tools aren't available yet:  I'd hoped to make a GUI in wxPython rather than TKinter (and I really can't seem to grok the documentation of PyQT4, for some reason).

Would those of you who have a handle on both the 2.7 and 3.1 versions have an opinion about whether it's easier to learn 3.1 and then step back to 2.7, or should one internalize them the other way around?  Does it make a difference?

I want to be ready when the tools do get ported over.

---

### Post by wmcbrine on 2011-02-06
Python is still Python. Moving from 2.x to 3.x (or from 3.x to 2.x) is *not* like learning a new language. It's just that all your code breaks. :-/

---

