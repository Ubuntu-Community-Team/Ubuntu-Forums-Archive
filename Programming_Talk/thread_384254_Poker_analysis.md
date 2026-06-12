---
title: "Poker analysis"
date: 2007-03-14
forum: Programming Talk
---

### Post by mediax on 2007-03-14
I play poker on Empire and receive tournament histories, which are basically lists of cards dealt, players' actions, etc.  I'm looking to summarise these to review and improve my game.

First of all, I wondered if anyone had done anything similar?  (Well, you never know . . .)

I'm coming to this project with a background of Basic, Pascal and VBA, but as I'm a fairly recent convert to Ubuntu, this seems like an ideal opportunity to learn a new language.  Perl looks like a good bet, but I'd appreciate any suggestions.  I know that Python is very popular, but I'm not sure if I fancy it (yet!)

---

### Post by loell on 2007-03-14
maybe you can look at "Machine learning" or data mining.

---

### Post by pmasiar on 2007-03-14
Perl was rather popular scripting language once, but with appearance of Python and Ruby, it is not "duck tape" it once was. It is very good for old gurus to write short throw-away scripts using it's embedded regex engine, but it has lots of quirks and tricks which are hard to remember if you use Perl only occasionally, and Perl code in harder to maintain unless very strict code standards are maintained. Also, OOP seems not very OO., and development of next version, Perl 6 seems stalled (and even if implemented, it feels over-complicated: I do not know any other language with so many operators it need "periodic table of operators" and uses Unicode characters to some of them. So i would advice agains starting new project with Perl, unless you are old Perl hacker and/or it is throw-away first quick pilot prototype.

Python and Ruby are fighting for scripting niche once owned by Perl. My money are on Python, because it is simpler, cleaner-looking, easy to learn, easy to read, and has strong following outside web app scripting (Ruby is used mostly for Rails web apps). Also, Python is older (more mature, more libraries) and has strong supporter - Google. Ruby is the latest fad (many java people flocked to it) and is by design closer to Perl quirks.

Python is easier to learn than any other mainstream language: using Python shell, you can create objects and try them from commandline - no need to create stub programs to test small snippets like you have to do in other languages.

I have little wiki with links for Python learners: [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart)

See also sticky for this forum for many links to many languages.

Either Python or Ruby will be good bet for sophisticated text parsing. Many people get distracted by significant whitespace in Python and go Ruby way, but Python approach (aligned proparly = valid syntax)  is preferable for team code sharing - no fights about placing  {} brackets.

---

### Post by lnostdal on 2007-03-14
I'd use [Common Lisp]("http://ubuntuforums.org/showpost.php?p=2224105&postcount=21") with the [cl-ppcre]("http://weitz.de/cl-ppcre/") library for this. 

But both Common Lisp, Python and Ruby are perfectly suitable and valid choices for this IMHO.

The most likely non-suitable choices for this is any non-interactive language. C and C++ comes to mind first.

---

### Post by mediax on 2007-03-14
Your comments have been very helpful - thanks.  I have to confess that I wasn't aware of the current status of Perl.

Python and Ruby are the other two programs I've been thinking about learning, so perhaps it's time to bite the bullet and go for one of them after all.

I do like the look of Ruby, but Python seems to be pretty much a "Swiss Army knife" language, so I'd probably get better long-term use out of it.

Hmm, looks like it might be Python after all . . .

---

