---
title: "What to learn next?"
date: 2011-05-02
forum: Programming Talk
---

### Post by cgroza on 2011-05-02
Hello, I want to master another language, a scripting one. I am already comfortable with Python, proefficient  in C++ and Java.

I read some Ruby tutorials and now I am having a difficulties choosing between Perl and Ruby.
Which one should I choose? I've heard that Ruby is very similar to Perl and given the popularity in TIOBE I am a little more for Ruby.

What do you say?

---

### Post by shawnhcorey on 2011-05-02
Sorry but Perl and Ruby are very different.  Ruby is object-oriented and Perl is procedural, though Perl can do object-oriented through [Moose]("http://search.cpan.org/~doy/Moose-2.0002/lib/Moose.pm") and [Mouse]("http://search.cpan.org/~gfuji/Mouse-0.92/lib/Mouse.pm").  And, of course, Perl has [CPAN, the Comprehensive Perl Archive Network]("http://www.cpan.org/"), a vast collection of modules and objects for Perl.

There are also web-frameworks for both.  Ruby on Rails and LAMP (Linux-Apache-MySQL-(Perl|Python|PHP)).  Perl also has [Catalyst]("http://search.cpan.org/~bobtfish/Catalyst-Runtime-5.80032/lib/Catalyst.pm"), [Mason]("http://search.cpan.org/~jswartz/Mason-2.07/lib/Mason.pm"), [Template::Toolkit]("http://search.cpan.org/~abw/Template-Toolkit-2.22/lib/Template/Toolkit.pod"), and [CGI::Application]("http://search.cpan.org/~markstos/CGI-Application-4.31/lib/CGI/Application.pm"), just to name a few.

If you're into genetics, there's [BioPerl]("http://search.cpan.org/~cjfields/BioPerl-1.6.900/BioPerl.pm").

---

### Post by brpylko on 2011-05-02
I recommend Ruby, just because I like it better. ;)

---

### Post by cgroza on 2011-05-02
> **shawnhcorey said:**
> Sorry but Perl and Ruby are very different.  Ruby is object-oriented and Perl is procedural, though Perl can do object-oriented through [Moose]("http://search.cpan.org/%7Edoy/Moose-2.0002/lib/Moose.pm") and [Mouse]("http://search.cpan.org/%7Egfuji/Mouse-0.92/lib/Mouse.pm").  And, of course, Perl has [CPAN, the Comprehensive Perl Archive Network]("http://www.cpan.org/"), a vast collection of modules and objects for Perl.

There are also web-frameworks for both.  Ruby on Rails and LAMP (Linux-Apache-MySQL-(Perl|Python|PHP)).  Perl also has [Catalyst]("http://search.cpan.org/%7Ebobtfish/Catalyst-Runtime-5.80032/lib/Catalyst.pm"), [Mason]("http://search.cpan.org/%7Ejswartz/Mason-2.07/lib/Mason.pm"), [Template::Toolkit]("http://search.cpan.org/%7Eabw/Template-Toolkit-2.22/lib/Template/Toolkit.pod"), and [CGI::Application]("http://search.cpan.org/%7Emarkstos/CGI-Application-4.31/lib/CGI/Application.pm"), just to name a few.

If you're into genetics, there's [BioPerl]("http://search.cpan.org/%7Ecjfields/BioPerl-1.6.900/BioPerl.pm").
Well I want to study bioinformatics and I heard that they use perl a lot. What do you suggest as a text processing language?

---

### Post by brpylko on 2011-05-02
Ruby was made to process text, seriously, that was its purpose.

---

### Post by cgroza on 2011-05-02
Hmm, I might go with ruby now since I can handle it's syntax and I will learn perl later.

---

### Post by shawnhcorey on 2011-05-02
> **cgroza said:**
> What do you suggest as a text processing language?

Perl.  Perl was first designed as a text-processing language but it has expanded to become much more.  Perl's regular expressions are built-in and are the most advanced.  They are so advanced, that other languages borrow Perl's regex engine rather than create their own.  It's one of the nice things about FLOSS.

---

### Post by Simian Man on 2011-05-03
I would learn a functional language, preferably Haskell because it forces you to do things the functional way.  Ruby and Perl are decent languages, but are so similar to Python that you won't really learn anything new.  If you ever need them, you can pick them up in a few days.  Learning functional programming is something that will make you a better programmer in every language you use, especially Python which has very good functional features.

---

### Post by cgroza on 2011-05-03
> **Simian Man said:**
> I would learn a functional language, preferably Haskell because it forces you to do things the functional way.  Ruby and Perl are decent languages, but are so similar to Python that you won't really learn anything new.  If you ever need them, you can pick them up in a few days.  Learning functional programming is something that will make you a better programmer in every language you use, especially Python which has very good functional features.
Hmm, I will take a look at Haskel, sounds interesting. Thank you.

---

### Post by myrtle1908 on 2011-05-03
> **cgroza said:**
> What do you suggest as a text processing language?

Perl eats text for breakfast.  It's a no brainer.

---

### Post by cgroza on 2011-05-03
I looked at Haskell and it really does not offer what I want. I have decided to go with perl after discovering the regular expressions, all I need is a quick hacky scripting language.

---

### Post by cgroza on 2011-05-03
> **myrtle1908 said:**
> Perl eats text for breakfast.  It's a no brainer.
Just discovered that. I think that's why it was invented, data extraction.

---

### Post by Simian Man on 2011-05-03
> **cgroza said:**
> I looked at Haskell and it really does not offer what I want. I have decided to go with perl after discovering the regular expressions, all I need is a quick hacky scripting language.

Sorry, I missed that you were looking for text processing specifically.  I though you just wanted to add something new to your toolbox.

---

### Post by shawnhcorey on 2011-05-03
> **cgroza said:**
> I looked at Haskell and it really does not offer what I want. I have decided to go with perl after discovering the regular expressions, all I need is a quick hacky scripting language.

I'm going give this advice because if you don't follow it, you'll get complaints.  (It seems to drive some Perl mongers crazy.)  The name of the language is Perl.  The name of the program that executes Perl code is perl.  One is uppercase; the other, lowercase.  And there's no such thing as PERL.

If you want to learn Perl's regular expressions, see:
[LIST]
[*][perldoc perlretut]("http://perldoc.perl.org/perlretut.html")
[*][perldoc perlre]("http://perldoc.perl.org/perlre.html")
[/LIST]

---

### Post by cgroza on 2011-05-03
> **Simian Man said:**
> Sorry, I missed that you were looking for text processing specifically.  I though you just wanted to add something new to your toolbox.
I really like their concept, one day I might dig around it.

---

### Post by cgroza on 2011-05-03
> **shawnhcorey said:**
> I'm going give this advice because if you don't follow it, you'll get complaints.  (It seems to drive some Perl mongers crazy.)  The name of the language is Perl.  The name of the program that executes Perl code is perl.  One is uppercase; the other, lowercase.  And there's no such thing as PERL.

If you want to learn Perl's regular expressions, see:
[LIST]
[*][perldoc perlretut]("http://perldoc.perl.org/perlretut.html")
[*][perldoc perlre]("http://perldoc.perl.org/perlre.html")
[/LIST]

Sorry, I am just used to write python lower case. It seems I do the same thing to Perl... :)

---

### Post by rg4w on 2011-05-04
Lisp.  Almost devoid of practical use in most applications, but it's so mind-expanding everyone keeps recommending it as a must-do for earnest learners.

---

### Post by cgroza on 2011-05-04
> **rg4w said:**
> Lisp.  Almost devoid of practical use in most applications, but it's so mind-expanding everyone keeps recommending it as a must-do for earnest learners.
Way too many brackets. Thanks for suggestion anyway.

---

### Post by simeon87 on 2011-05-04
> **cgroza said:**
> Way too many brackets. Thanks for suggestion anyway.

Although Lisp's syntax is indeed rich in brackets, that shouldn't be a reason to reject it. Its concepts have influenced many languages, including the recently introduced Clojure. It features many contructs of functional programming and it blurs the distinction between data and code.

It may not be your current focus in learning a new language but, like Haskell, it's certainly worth learning.

---

### Post by cgroza on 2011-05-04
> **simeon87 said:**
> Although Lisp's syntax is indeed rich in brackets, that shouldn't be a reason to reject it. Its concepts have influenced many languages, including the recently introduced Clojure. It features many contructs of functional programming and it blurs the distinction between data and code.

It may not be your current focus in learning a new language but, like Haskell, it's certainly worth learning.
I did not reject it, simply left it for another day.

---

### Post by krazyd on 2011-05-05
> **shawnhcorey said:**
> Sorry but Perl and Ruby are very different.  Ruby is object-oriented and Perl is procedural, though Perl can do object-oriented through [Moose]("http://search.cpan.org/~doy/Moose-2.0002/lib/Moose.pm") and [Mouse]("http://search.cpan.org/~gfuji/Mouse-0.92/lib/Mouse.pm").  And, of course, Perl has [CPAN, the Comprehensive Perl Archive Network]("http://www.cpan.org/"), a vast collection of modules and objects for Perl.

I believe ruby has more modules now.
[http://www.modulecounts.com/](http://www.modulecounts.com/)

@O.P. I would recommend ruby over perl, purely for the nicer (my opinion) syntax. Check out BioRuby:
[http://bioruby.open-bio.org/](http://bioruby.open-bio.org/)

---

### Post by cgroza on 2011-05-05
> **krazyd said:**
> I believe ruby has more modules now.
[http://www.modulecounts.com/](http://www.modulecounts.com/)

@O.P. I would recommend ruby over perl, purely for the nicer (my opinion) syntax. Check out BioRuby:
[http://bioruby.open-bio.org/](http://bioruby.open-bio.org/)

I kind of like the Perl syntax. I will learn Perl and then go to dig Ruby deeper(I am familiar with it's syntax, the ruby blocks are awesome.)

Right now I am discovering regex with Perl (noticed that both languages use almost the same syntax for that).

Great languages. Thank you for your tip.

Bioruby? The languages are equal to me, now it is even harder to decide!:D:D

---

### Post by slavik on 2011-05-05
Are you proficient in data structures and analysis of algorithms?

---

### Post by cgroza on 2011-05-05
> **slavik said:**
> Are you proficient in data structures and analysis of algorithms?
Not yet, I am only 15.

---

### Post by slavik on 2011-05-05
Go learn that.

You say you are comfortable with Python, then:
- implement a list
- implement a queue
- implement a stack
what are the differences between the above 3?

- can you implement a circular list?
- implement a binary tree and use it to sort a bunch of numbers.

Here's a real interesting problem:
write your own regex engine

My largest problem with Python and it being the BASIC of the current years is that people like cgroza are produced (no offense meant). Just because you know how to type in a programming language to make a computer do something, does not mean you understand computer science at large.

---

### Post by cgroza on 2011-05-05
> **slavik said:**
> Go learn that.

You say you are comfortable with Python, then:
- implement a list
- implement a queue
- implement a stack
what are the differences between the above 3?

- can you implement a circular list?
- implement a binary tree and use it to sort a bunch of numbers.

Here's a real interesting problem:
write your own regex engine

My largest problem with Python and it being the BASIC of the current years is that people like cgroza are produced (no offense meant). Just because you know how to type in a programming language to make a computer do something, does not mean you understand computer science at large.
I might try to do those. I already implemented an iterator (bidirectional) and I should give myself another challenge.

---

### Post by andrewgail on 2011-05-06
I think, You can start with Ruby programming language.  The Ruby on Rails framework allows developers to create powerful, dynamic web applications quickly and easily. A language simple to adapt is not necessarily simple to program, as abounding a apprentice can attest.

---

### Post by cgroza on 2011-05-06
> **andrewgail said:**
> I think, You can start with Ruby programming language.  The Ruby on Rails framework allows developers to create powerful, dynamic web applications quickly and easily. A language simple to adapt is not necessarily simple to program, as abounding a apprentice can attest.
I am not really interested in web programming, had a few tries, it did not "stick".
Thank you.

---

