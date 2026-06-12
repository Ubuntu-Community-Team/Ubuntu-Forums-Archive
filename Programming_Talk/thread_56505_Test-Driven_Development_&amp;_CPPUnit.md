---
title: "Test-Driven Development &amp; CPPUnit"
date: 2005-08-12
forum: Programming Talk
---

### Post by spacemonkey on 2005-08-12
I recently installed the cppunit libraries from synaptic to do some unit testing in C++.  I'm interested in doing some test driven development (writing the test before you write the implementation, and using the test as a design for the implementation, more to it than that, but that's the basics).  I know that the xUnit libraries for whatever language interface with several different IDEs.  Most of these IDEs I've read about are for windows.  Does anyone know if there are any IDEs for C++ that can interface with cppunit in the ubuntu repositories?

Also, what are your thoughts on Test-Driven Development?  Has anyone used it for large scale development, and if so, how did it go?

---

### Post by newbie2 on 2005-08-17
"CTPs are releases of code that Microsoft typically makes available in between full-fledged beta builds.
CTPs are typically not supported directly by Microsoft, but are aimed at developers and customers who want to be on the bleeding edge."
[http://www.eweek.com/article2/0,1895,1848934,00.asp](http://www.eweek.com/article2/0,1895,1848934,00.asp)

---

### Post by LordHunter317 on 2005-08-17
Eclipse might be able to if you install the CDT.  Don't quote me on it, though.  You're likely to have to build your own scaffolding around it.

As far as test-driven development is concerned, I'm not a fan.  It doesn't solve the fundamental problem: *you don't know what you want to design*.  Usually, going from a correct design to implementation is fairly easy.  But if you don't know what you want to design, you'll simply write test cases and code that passes them, but ultimately, you'll have to rewrite the code anyway, because the code doesn't do what you want.

IOW, test-driven development only helps you verify your code matches some fixed design (encapsulated in the tests).  It does nothing, nor can it, to ensure those tests actually match up with what you want to/need to actually create.  Nor do I think it makes it any eaiser to be sure of what you create is actually what you want.

That being said, automated testing frameworks have their purposes.  Automated regression testing to verify current functionality isn't broken is useful.  

Also, sometimes when you do have a good design, the eaisest way to code to the design is to write the tests first, and write code that passes all the tests.  But you still have to make sure those tests actually really verify the requirements, and that's the hard part.  It's always been the hard part.  TDD doesn't make it any eaiser.

---

### Post by spacemonkey on 2005-08-17
But the tests that you write before the code are the design of the code.  That's the whole point.  You write the test that shows what your code does, and then you write the code to do it.  The key to it is to use unit tests.  Write tests that verify only small parts of code.  I handful of related methods, one class, or something like that.  If you keep your tests small, then they will act as the design for the implementation of the code, then you won't run into the problem of code that satisfies the tests but doesn't do what you want it to.  And also, if you are running into that problem with unit tests, then you are probably writing bad tests.

Newbie2, I've got no clue what you're talking about.....

I'll have to look at Eclipse and see what I can do.

---

### Post by LordHunter317 on 2005-08-18
[QUOTE=spacemonkey]But the tests that you write before the code are the design of the code.[/quote]Yes, I understand that.

**But that doesn't assure you that your design meets your *requirements***.  If the requirments say: create an grape, and you go and write tests and code to those tests that create an apple, your application is still **wrong**.  


Your software must meet your design which must meet your requirements.  TDD only helps software meet designs.  It does not help design meet requirements.  And in my experience, it's the requirements -> design part that falls apart, not translating the design into actual code.

> You write the test that shows what your code does, and then you write the code to do it.And if you don't actually know what your code is really supposed to do?  Then you'll end up writing tests and therefore code that is meaningless.

> The key to it is to use unit tests.  Write tests that verify only small parts of code.That's not always useful, or gives you useful information.  I can think of plently of applications where I could write code that would not only pass it's unit tests at a small enough scope, but also meet the requirements, yet be actually useless in the context of the real application.

> If you keep your tests small, then they will act as the design for the implementation of the code, then you won't run into the problem of code that satisfies the tests but doesn't do what you want it to.No, you just avoid the problem of code that doesn't meet your design.  It doesn't save you if your **design** is wrong to begin with, which is my whole point.

---

### Post by thumper on 2005-08-22
[QUOTE=spacemonkey]But the tests that you write before the code are the design of the code.  [/QUOTE]
Well... no.  The tests test the interface to your code, not the design of your code.

You could have something that matches the tests but the design of the underlying code is crap.  Have you created something good?

I don't have any problem with TDD but don't make the mistake of assuming that the tests replace design.

---

