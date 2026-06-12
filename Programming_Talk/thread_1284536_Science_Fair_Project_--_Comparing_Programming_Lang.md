---
title: "Science Fair Project -- Comparing Programming Language"
date: 2009-10-06
forum: Programming Talk
---

### Post by dellwood on 2009-10-06
Hi,

For better or for worse, I have decided to compete in my High School's Science Fair.  While brainstorming, the idea came to me to attempt to answer one of the first questions newbie programmers seem to always ask.  What is the best programming language?  

Now, obviously when such questions are asked on this board and ones similar to it, the response is always something along the lines of "Well, that depends what you want to do," and I realize this, so I guess the better question to ask is "What is the best all around programming language?"  The basic project that formulated in my mind is taking about six well known and well used programming languages, probably three low level and three high level, and with a tasked with a list of problems to solve, write programs to complete those tasks, monitoring many variables, such as time to write program, compile time (if the language uses a compiler), run time, etc.  Now, from this many questions crop up:

1) Which languages should be used?  -- I was thinking along the lines of C/C++, along with another low level language, and then for the high level ones Perl, Python, and Ruby.  The problems here are:

 -are C and C++ too similar to be tested side-by-side?  Also, is the level of          abstraction too far between the two to test them on the same level?  What should the third low-level language be, and if you agree C and C++ are two similar, than which one should be used and what should take the other ones place? I've always considered ruby/python somewhat on the same level of abstraction, but like C++, is Perl also too low to be put in the same level of abstraction as Ruby and Python? If so, what should replace Perl?

2) What is the best method to setup a controlled environment? -- I was thinking along the lines of virtual machines, but is that a good/bad idea? Also:
-does the amount of space on the hard drive matter between tests?  For instance, if I test C first then it will be run with whatever else is on the computer, but all tests from that point onward will be run with everything else plus what the compiler generates.  Will this matter?  How much do things like power, (if I run it from a laptop), CPU speed, etc. matter? If they change throughout the tests, is there a way to regulate such variables to stay within a range?  Should all tests be run in the same Virtual machine or separate ones?  (This area probably concerns me the most, so if there's anything else you think could add more control to the test environment, feel free to say so).

3) How do I verify the "correctness"  of the programs I write?  -- I live in a University town, so emailing the professors would not be a problem, but they may not know all the languages used.    Should I only ask people to proof the programs who have certain qualifications (BA, MA, or PhD in computer science, for example)?  Should I have multiple programs for each task in each language, and if so, should I write them all or should I ask multiple people to write them?  How would I go about choosing who to ask to write programs?  The same ways as who should proof them?

Ah, science is making my head hurt :D.  I probably could come up with more questions if I tried, but this seems more than enough for now.  All answers, suggestions, and comments are greatly appreciated and I want to thank any who take the time to do so in advance.  And if something is not clear, or you need anymore information from me, feel free to ask.

Thanks Again!

-Josh

---

### Post by Can+~ on 2009-10-06
> **dellwood said:**
> Hi,
Now, obviously when such questions are asked on this board and ones similar to it, the response is always something along the lines of "Well, that depends what you want to do," and I realize this, so I guess the better question to ask is **"What is the best all around programming language?"**  The basic project that formulated in my mind is taking about six well known and well used programming languages, probably three low level and three high level, and with a tasked with a list of problems to solve, **write programs to complete those tasks, monitoring many variables, such as time to write program, compile time (if the language uses a compiler), run time, etc.**  Now, from this many questions crop up:

Your question if flawed (and therefore, your Hypothesis will be too). That question is pretty much the first one, adding "all around" doesn't make it all that different from the original one.

Let me give you some questions:
-In what scenario it would be wiser to use X over Y?
-What criteria is used to select a language?

Plus, that testing method will only yield performance results, nothing about the most important things about languages, the syntax, the thing that is actually what humans understand when they use a certain language.

I think the most interesting aspect of a programming language is not on the code <-> execution part, but on the human <-> code one. Recently, I posted (well, got reposted) some food for the mind on the [Lambdagrok froum]("http://lambdagrok.wikidot.com/forum/t-183572/measuring-syntax-complexity") regarding the Backus-Naur Form as a tool to measure complexity on a programming language.

---

