---
title: "perl | python | php"
date: 2009-11-22
forum: Programming Talk
---

### Post by mo.reina on 2009-11-22
what are the major differences and similarities between these 3 scripting languages?

i understand that all 3 are used for developing web applications, and that php is the most popular one for this task.

do programmers only use one of the 3 when developing web apps, or use a combination?

how about for client side applications?

---

### Post by scragar on 2009-11-22
Perl is pretty much linux only, it's very efficient for regular expressions(pattern matching), it's got some really nice shorthand, but perl is a harder language to learn, it's hacky in many ways, and pretty much every new major version(so from 3.* to 4.0 or 4.* to 5.0) changes the syntax of some things, meaning that you need to rewrite from time to time if you want to keep up to date.

Python isn't used online like the other two are, perl and PHP are loaded as modules by apache, Python can completely replace apache, this makes it more efficient and allows you much greater control, Python is also very easy to learn and enforces good layout of your code. Python is also rather good for client side work. Python only achieved popularity late compared to the other two, but is very popular right now, it's hard to judge how long it will remain popular, but python is already backed by google, so it looks good.

PHP is very popular for web based work, it runs on windows, linux, mac and pretty much anything you can think of, because nothing is specific to a single platform you know that as long as your modules are installed you can run any code anywhere. PHP is slowly moving towards a far more Object Oriented syntax, where prior to version 4 there were no objects at all, in PHP6(dev) objects are used for most things by default, although backwards compatibility is maintained.

---

### Post by ssam on 2009-11-22
python has been around longer than PHP (1991 vs 1995), though is less established as a web programming language. none of them are going away anytime soon. python is pre-installed on most Linux and MacOS X.

PHP is not used much outside programming websites, whereas python is used for some applications (lots of ubuntu's tools are written in python).

you might also want to look at ruby.

if you want to program websites have a look at some web application frameworks such as django.

---

### Post by nvteighen on 2009-11-22
It's all about their fundamental principles. 

**Perl** was initially born as general programming language with its strength in text processing. It's aim was to superseed tools like sed, awk and grep, which are just scripting text-processing languages. But, ironically, Perl turned out more into some sort of "high-level C". Its usage in web development comes from it's great support for string manipulation; an HTML file is essentially a text file, so Perl is a logical choice to handle it.

**Python** was born as a general programming language with no particular strength. The idea was to create a language that could make higher-level programming much simpler and replace the misusage of low-level languages in that area. Its usage in web development comes from the high-level side... web development is not systems programming, so Python had easily developed libraries for this stuff... The issue is that the "connection" is not because Python provides useful functionality for that directly (like in Perl's case, where the language-task connection is rather obvious) but because it can be used to easily create frameworks for that. In some way, it's an indirect cause.

**PHP** was created exclusively for web development, so that's why it's used... Kinda obvious. The issue is that that design decision makes it a rather useless language for anything that's outside the mere modification of HTML files. You can use it for CGI scripting, of course... and people use it, but its limitations end up driving coders to write bad code... or switch to Perl or even Java if needed.

---

### Post by Martin Witte on 2009-11-22
> **scragar said:**
> Perl is pretty much linux only

See [ports]("http://perldoc.perl.org/perlport.html#Supported-Platforms") for all platforms perl has been ported to, although perl is rooted in Unix - and is mostly tailored to Unices - including Linux

---

### Post by ghostdog74 on 2009-11-22
> **nvteighen said:**
> The issue is that that design decision makes it a rather useless language for anything that's outside the mere modification of HTML files. 
not true. you can use it for system administration (and others) too, not just for web development

---

### Post by nvteighen on 2009-11-22
> **ghostdog74 said:**
> not true. you can use it for system administration (and others) too, not just for web development

I don't say you can't, but haven't ever seen that PHP usage.

---

### Post by Reiger on 2009-11-22
PHP is a general purpose programming language these days with plenty of libraries to go by. PHP is actually used for quite a bit of sysadmin type tasks. The plethora of phpmyadmin type suites speaks for themselves.

---

### Post by A_Fiachra on 2009-11-22
IMHO, PHP has all the ugliness of Perl with none of the power -- it was created for people who couldn't learn Perl to do CGI programming.  To be fair, I haven't looked at it in years, in no small part because it's advocates are like Red Sox fans.

Perl's ugliness is accepted because you can do basically anything in Perl -- it's the Swiss Army Chainsaw of unix utilities (and consequently most modern OS's).  Writing large systems in Perl takes great care because the language is so flexible, people tend to be brain dead and abuse it.

Python is designed with the idea that most code spends more time being read and fiddled with by programmers than actual machines (in terms of wall clock time, that is generally true) so it embraces a level of elegance that neither Perl nor PHP can touch.  Python is not as weakly typed as most scripting languages -- in fact it is much more like Java in that respect -- most things are first class objects and operator overloading is a breeze (compared to Java which is utterly braindead when it comes to operator overloading).  It embraces serious OO and some aspects of functional programming (yes, functions can be first class object too) in a way that language lawyers love.

Naturally, the question isn't what language is best, that's a moronic question.  The question is "which language is best for task X given that my experience and skill as a developer is Y?"

So, what's the task, how skilled are you and what's your level of experience?

---

### Post by Can+~ on 2009-11-22
PHP is widely used for web programming, but I usually never recommend it. Why? Because it encourages bad style programming.

[list]
[*]Mixing layout elements with logic is so easy to do, that pretty much anyone that used PHP has used it. It encourages this kind of programming, but it's a bad practice.
[*]Duplicated functionality seems to be PHP's game. Every single function has either a shortcut, an alias, older versions of the function, duplicated statements, multiple ways to use statements. Now that they added methods to strings, there's also the str functions and the string methods. Python already had this trouble, and moved everything outside to the string module and kept.
[*]Cluttered namespace. Aside from having duplicated functions, the fact that variables are $variablized, it seems that PHP devs pretty much decided that the whole namespace should be entirely devoted to all the functions available in the manual, I hope their new OOP-ness adds namespacing and modules.
[/list]

And if you're on PHP's boat, it's worth to check out the available frameworks, like CakePHP.

---

### Post by slavik on 2009-11-22
Time for some corrections. :)

Perl - was supposed to be a better awk, but wound up being general purpose and a swiss army knife with a space shuttle and a surgery room built in. CPAN is big. Big as in, there are probably 2-3 modules for whatever you need to do.
As to the major version argument above ... 4.x hasn't been used in ages.
Currently suffers from having 1 reference implemenation which you have to mimic if you want to write it on top of something else. Perl6 defines spec tests which you have to pass in order to be accepted as a valid Perl6 interpreter/compiler

Python - was a scripting language for a little known OS ... OS died but Python was decent. Currently suffers from the same issue as Perl. The main implementation (the C version). Has GIL, thus no thread concurrency.

PHP - Perl for the web. Very easy to use to get a DB connection, get data, generate output and done. Suffers from cluttered global namespace (as mentioned) as well as a naming misconvention (CamelCase versus underscores).

All 3 have modules for apache. PHP is the most popular for web dev because it is the simple to get up and running with. Perl is most popular with Unix admins because it was around way back when and is very maluable. Python is the up and comming language as newbies to computers/Linux learn it.

All 3 languages can be used interchangeably. But for any given project, I would advise you to split it into pieces and define clear interfaces for each piece. It would also make sense to use only 1 language for any single project, makes everyone's life easier.

---

### Post by mo.reina on 2009-11-22
thanks for the great replies!  

outside of web development, what are the strengths of each language?  i've read reviews saying that PERL becomes cumbersome and almost impossible to debug when writing applications that exceed a few hundred lines.  has anyone found this to be true?

---

### Post by myrtle1908 on 2009-11-22
> **mo.reina said:**
> i've read reviews saying that PERL becomes cumbersome and almost impossible to debug when writing applications that exceed a few hundred lines.  has anyone found this to be true?

This is garbage.  You will often hear things like this from developers who have close to zero exposure with a language thus do not understand its idiosyncrasies, much less how to *use* it.  Any language is difficult to debug if you don't know what you are doing.

---

### Post by Reiger on 2009-11-22
Perl can be as ugly as you want it to be. Whether or not code is maintainable depends very much on whether:
(a) You write simple & efficient solutions instead of clumsy, long winded and cumbersome ones. This generally means you must be somewhat experienced with a language before you will realize the difference between what is maintainable and what is a hairy mess; since some of the &#8216;clever tricks&#8217; will wind up a nightmare to understand later on and quite unnecessary from the P.O.V. of someone with more experience in the language since there was of course feature xyz that rewrites this weirdness in 5 neat lines of pure elegance.
(b) You write your program with the intention to be maintained. I.e. you take the necessary precautions such as documentation & comments of what the heck you are doing.
(c) You stick to idiomatic code which anyone familiar with the language will immediately recognize. E.g.: in an imperative language you generally use a for loop and not a recursion for simple linear data structures.

---

### Post by ghostdog74 on 2009-11-22
> **mo.reina said:**
> thanks for the great replies!  

outside of web development
outside of web development, the 3 P's, PHP, Perl and Python can do almost the same kind of system administrative tasks and others, because they have abundance of libraries and modules developed by their communities. what is really left for you to decide, is whether the code you write in them appeals to YOU, aesthetically, as well as how easy for you to use your tools. so why don't choose 1 and start to learn it already? Perl is it? then go to perldoc.org and start learning. whatever we say here doesn't really matter, because after all, there are always biases to what one likes (or dislikes). What's most important is, you start to use them, and decide for yourself what's best for you. This will always be the ultimate solution to questions of such nature

---

### Post by Aayu on 2009-11-23
Python is clean, simple to read, powerful and has a beautiful syntax (I'm learning 3.0), has good documentation, is popular outside web development (Pygame anyone)
 
Perl CAN be clean, providing it's in small quantities, is good for web based development and scripts, has a HUGE CPAN archive, but in large programs, Perl can look like a right mess (can't read my own code), outside of web development however, Perl isn't really that popular imo (everyone just wants it for CGI stuff)
 
PHP is a broken mess, stick with PHP3 ;)

---

### Post by Hellkeepa on 2009-12-12
HELLo!

First I'd like to debunk a couple of myths:
[list][*]Python requires a beautiful syntax/it's impossible to write hard-to-understand Python code.
Oh, so very wrong. While it is true that it is harder to write *really* obfuscated code with Python, it is still very easy to make a mess out of it. Especially if you have a lot of blocks within it, or not; Just add an arbitrary number of indentations at random locations, and the poor bloke that is supposed to read it will never know what belongs to a block or not.
[*]PHP encourages bad coding styles.
While it is true that the naming convention of some of the functions could be made more consistent, PHP does not in any way encourage bad coding style. What it does, is to leave the coding style (almost) entirely up to the programmer. Since PHP is such a popular language, and a lot of newbies are using it, the visibility of badly written code is a natural consequence of this.
Same as with any other language, including Python and Perl.[/list]
That said; What language you decide to use is one you have to decide for yourself. PHP is, as noted mostly used on web-based projects. It has a very Perl and (simple) C-like syntax, and if you use either of these you should be quite familiar with PHP within a short time. (In fact, I prefer to write my PHP code in a C-type manner, using a "main()" function and all.
Python is used in a bit more general manner, and easier to make into a compiled executable than PHP. Syntax is quite different, though, and whether or not you find it more "beautiful" is a completely personal preference.
Perl is, as noted, a very powerful and compact language. Mainly used for *nix administration, and text manipulation. The only important thing for Perl is speed, readability and aesthetics are secondary. Makes for a very quick and powerful language, but not the easiest to learn and use at times.

Addendum: For those who are bashing PHP, calling it broken, ugly or whatever, and then turning around stating that you haven't looked at it in years, or don't really know anything about it; You're not doing yourself, nor anyone else, a favour by posting such uninformed and inaccurate claims. I realize you found a tool that suits you very well, but I don't understand this need to bash other languages to defend *your* choice.
This does not only apply to those bashing PHP, but everyone bashing any other language than their personal favourite.

Namespaces, more OOP, and general cleanup is coming in PHP 6. PHP5 has come a long way already, especially when compared to early PHP 4 or (heaven forbid) PHP 3.

Happy codin'!

---

### Post by wmcbrine on 2009-12-12
> **Hellkeepa said:**
> Just add an arbitrary number of indentations at random locations [in Python], and the poor bloke that is supposed to read it will never know what belongs to a block or not.If you added arbitrary indentation, the program wouldn't even run. So no, that's not an issue.

In real life, people (as opposed to parsers) already use indentation to tell where the blocks are, in almost every language, regardless of whether the language has block delimiters.

---

### Post by Can+~ on 2009-12-12
> **Hellkeepa said:**
> Just add an arbitrary number of indentations at random locations, and the poor bloke that is supposed to read it will never know what belongs to a block or not.

It's like saying "Just add an arbitrary set of {} and it will never know what belongs to a block or not".

I agree with you, python can be obfuscated, unless a language specifies really strict rules, people will find a way to make it horrible. I've seen guys coming from C that do pretty much C on python, and using variable names like "aa", "ab", "ac"...

> **Hellkeepa said:**
> PHP does not in any way encourage bad coding style. What it does, is to leave the **coding style (almost) entirely up to the programmer**. Since PHP is such a popular language, and a lot of newbies are using it, the visibility of badly written code is a natural consequence of this.

And that's exactly the reason why I said (and many others), that the OP should start away from PHP. Putting the responsibility on the programmer when you're just starting, is like your dad hands you the keys of his car when you don't even know how to drive.

> **Hellkeepa said:**
> It has a very Perl and (simple) C-like syntax, and if you use either of these you should be quite familiar with PHP within a short time.

I would say, that's one of the big things that put me off PHP. Not the C-like syntax (using {} for blocks), but the fact that PHP seems to be targeted at the C programmer, many times dropping some of the consistency of the language in favor of having functions like "stripos".

In fact, it seems that they wrote the language in different moods everyday, someday they decided to add the str functions, in the "str<action>" format. Later they decided to use_underscores. Other functions are 1337ly named with something2other, because numbers and words are awesome, classy. And now that they're entering the OO world, they now want to move things to camelCase, and for some reason adding the double-underscore Python-like __constructor (although, python defines it as [FONT="Courier New"]__init__(self)[/FONT]).

Python isn't perfect either, they used to have messy names for the modules, but they've been fixing that. And it seems that, for an older language than PHP (PHP:1995, Python:1991) (I just discovered this, actually), it somehow manages to keep in good shape most of the time, or cover its tracks (for example, threading module wrapped the thread module).

> **Hellkeepa said:**
> Perl is, as noted, a very **powerful** and compact language. Mainly used for *nix administration, and text manipulation. The only important thing for Perl is speed, readability and aesthetics are secondary. Makes for a very quick and **powerful** language, but not the easiest to learn and use at times.

I love how people tout around the "powerful" word. What does it mean, exactly? Do you mean as lines written vs instructions? Size of the standard library? Expressiveness?

In the business point of view, "powerful" would be to have most of the job already done (read: availability of already-made libraries or frameworks).

> **Hellkeepa said:**
> Addendum: For those who are bashing PHP, calling it broken, ugly or whatever, and then turning around stating that you haven't looked at it in years, or don't really know anything about it;

I've been using it since PHP 4.1.0. I created a little site for my university on 5.2.0, and other projects, and I still think it's messy, and it's quite difficult to work in a group with it, seems like is more targeted for the lone coder rather than a group of people.

I hope PHP 6.x normalizes the whole library and fix the seemingly weird decisions of the language. I also used PHP in my newbie days, although I didn't develop any kind of affection for it back then.

---

### Post by scragar on 2009-12-12
> **Can+~ said:**
> I've been using it since PHP 4.1.0. I created a little site for my university on 5.2.0, and other projects, and I still think it's messy, and it's quite difficult to work in a group with it, seems like is more targeted for the lone coder rather than a group of people.
PHP is actually quite easy to use in a group as long as you follow the basic rules of working in a group first, if you like to skip steps then you're going to shoot yourself in the foot no matter what language you use, blaming the language for the approach is like blaming the nail when you smack your thumb with a hammer.

---

