---
title: "Testing"
date: 2007-03-27
forum: Programming Talk
---

### Post by docetes on 2007-03-27
is there a name for "test as you go along" software testing?

Cheers,
Dave

---

### Post by Tomosaur on 2007-03-27
Well, some call it 'clean room', or 'white room' development. I think it was first tried out seriously at IBM, but don't quote me on that. It's based on the principle that if you are sure to iron out bugs and other problems right through development, then you won't have any at the end. However, it can bring its own problems - ie - it CAN slow development time, and depending on the software, it can drive your testing budget through the roof. However, it can also cut your development time AND testing time, It all depends on the project really. You need to find the right balance between development and testing, for example - writing a tiny chunk of code and testing it may be possible, but bugs may in that chunk may not manifest themselves in any case until further down the line. In large projects this can be pretty problematic - you may not even know whether other developers are following the 'clean room' approach, or indeed whether their code is working at all. Some would argue that it is still better to run through extensive testing at the end of development, when you have all of the code together.

---

### Post by lnostdal on 2007-03-27
Yes, it's called bottom-up programming .. [http://www.paulgraham.com/progbot.html](http://www.paulgraham.com/progbot.html) .. and it is a great way to develop.

You add small pices that you test at once (as you go along) instead of building top-down where you imagine you have the fundament (bottom) that would enable you to test the current parts "some time in the future".

While Lisp isn't a requirement for this (it is very suitable though), the language must IMHO at least be interactive and/or have a [REPL]("http://en.wikipedia.org/wiki/REPL").

---

### Post by pmasiar on 2007-03-27
> **docetes said:**
> is there a name for "test as you go along" software testing?

This kind of question is made for Wikipedia: start with  [http://en.wikipedia.org/wiki/Software_testing](http://en.wikipedia.org/wiki/Software_testing)

You may look for [http://en.wikipedia.org/wiki/Regression_testing](http://en.wikipedia.org/wiki/Regression_testing) ?

Another, even better source of information about software development is the "Original Wiki" - wiki by Ward Cunningham, the guy who invented the concept, "Portland Pattern Repository's Wiki". All pages with "testing" in title: [http://c2.com/cgi/wiki?search=testing](http://c2.com/cgi/wiki?search=testing). Check "continuous testing": [http://c2.com/cgi/wiki?ContinuousTesting](http://c2.com/cgi/wiki?ContinuousTesting) and [http://c2.com/cgi/wiki?ContinuousIntegrationRelentlessTesting](http://c2.com/cgi/wiki?ContinuousIntegrationRelentlessTesting)

---

### Post by rickardg on 2007-03-27
> **docetes said:**
> is there a name for "test as you go along" software testing?


Perhaps the term you are looking for is [test-driven development]("http://en.wikipedia.org/wiki/Test_driven_development").

---

### Post by pmasiar on 2007-03-27
> **rickardg said:**
> Perhaps the term you are looking for is [test-driven development]("http://en.wikipedia.org/wiki/Test_driven_development").

nah, test-driven is: "write tests first". TDD is a next step, higher level,  *above* continuous testing. IMHO.

---

### Post by rickardg on 2007-03-27
> **pmasiar said:**
> nah, test-driven is: "write tests first". TDD is a next step, higher level,  *above* continuous testing. IMHO.

I'm not saying you are wrong (this time either :-)), but since "test as you go along" isn't very specific and TDD seems to be quite talked about these days I thought perhaps that was what the OP was thinking of.

---

### Post by pmasiar on 2007-03-27
> **rickardg said:**
> I'm not saying you are wrong ....

I agree with you. I even tried TDD (test first) once, and liked it :-) OP has couple links to follow and study, we are done here.

My [ESP module](http://en.wikipedia.org/wiki/Extra-sensory_perception) is cloudy today and I cannot figure out what OP ment to ask -- it's screen switches between "not enough input info" and "42" :-) . I guess yours too. So let's wait what OP will say, if any.

---

