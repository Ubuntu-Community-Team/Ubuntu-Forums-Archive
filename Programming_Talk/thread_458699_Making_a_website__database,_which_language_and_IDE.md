---
title: "Making a website / database, which language and IDE to use"
date: 2007-05-29
forum: Programming Talk
---

### Post by lord bacon on 2007-05-29
ok as the title says im attempting to make a website that is a front end to a database and allows searching etc. this may seem simple but i was wondering which programming language/languages to use and how i should go about it??.. i am at a complete loss. 

i was thinking of useing PHP and mySQL to do this... but i have no dea how, and wethere it is even possible...

i was also wanting to know what IDE/s I should use if any (was thinking eclipse).

thanks for the help in advance
Lord Bacon

---

### Post by pmasiar on 2007-05-29
Sure it is possible - many people make living doing that. But it is not obvious, you need to learn some tricks.

PHP is popular, because it allows you to mix logic and HTML on same page. But it allows create *very* messy code, hard to maintain.

Different approach, requiring little more discipline, is use [http://en.wikipedia.org/wiki/Model_view_controller](http://en.wikipedia.org/wiki/Model_view_controller) approach, "scripting" language (Python or Ruby) and templates. Result is much cleaner and easier to maintain. Ruby has popular framework Ruby on Rails (RoR), Python has Django and TurboGears. Some people use Java but it is much more work to make it in java.

Check wiki in my sig, especially [http://LearnPython.pbwiki.com/WebApplication](http://LearnPython.pbwiki.com/WebApplication)

---

### Post by AnRa on 2007-05-29
> **pmasiar said:**
> PHP is popular, because it allows you to mix logic and HTML on same page. But it allows create *very* messy code, hard to maintain.

Different approach, requiring little more discipline, is use [http://en.wikipedia.org/wiki/Model_view_controller](http://en.wikipedia.org/wiki/Model_view_controller) approach, "scripting" language (Python or Ruby) and templates. Result is much cleaner and easier to maintain. Ruby has popular framework Ruby on Rails (RoR), Python has Django and TurboGears. Some people use Java but it is much more work to make it in java.

You can also use the MVC approach with PHP using [CakePHP](http://cakephp.org/) or [CodeIgniter](http://codeigniter.com/). :)

---

### Post by ankursethi on 2007-05-30
Using Perl, Python or Ruby means a tiny bit of extra work, but gives much better results. I haven't had good experiences with PHP.

Eclipse would be an overkill for simple a web app. Use something like Quanta Plus or Bluefish, which are more web-designer friendly.

---

### Post by LaRoza on 2007-05-30
PHP is good, but as stated before, the code can be messy if not well thought out.

If you use objects and included files wisely, you can drastically reduce the code and make it much easier to maintain.

http//www.tizag.com 

has many tutorials for web based programming.

---

### Post by lord bacon on 2007-05-30
Thanks for all the ideas, hopefully this will help lead me in the right direction.. hopefully, i will look into Ruby as it does look interesting, and always wanted to have a look at it.

once i have got this started im sure that i will be back here for many many more questions, mainly security based, ( is there much security in Ruby). i am also at putting in userprofles and such (ie usernames and password) would Ruby or Python be better for this. 

Thanks again

---

### Post by barmazal on 2007-05-30
> **AnRa said:**
> You can also use the MVC approach with PHP using [CakePHP](http://cakephp.org/) or [CodeIgniter](http://codeigniter.com/). :)

he knows that, me and few other guys told him that for few times but he still finds it interesting to publicly declare his misunderstanding

Once again , framework can be MVC not a language. There are much more PHP MVC frameworks

I don't know what can be more mess than having not strict typed variables and perl  general looks but still.



Anyhow, [COLOR="DarkOrange"]lord bacon[/COLOR]

first you need to decide what language you want to learn, easiest imho would be using framework rather just coding everything yourself. framework is number of functions combined together in order to ease with certain tasks.

if you interested to learn Ruby then your web framework is Ruby on Rails
if you decide Python then frameworks would be Django, Turbo Gears or Zope
for PHP you have much more frameworks and come much more advanced ones, since it's the most popular language for web applications, it's easy to maintain, understand and it has proper application to code at.

for IDE, as everything it depends on language, i won't go Ruby since it only started to getting integrated into good IDE's so probably many errors would be found of course you can try Aptana, Eclipse or Easy Eclipse.

Python i have no idea, probably pyDev for Eclipse but i don't know how good is that

for PHP you have PDT for Eclipse and Easy Eclipse for dynamic languages which supposedly should support PHP, Python and Ruby at once.

so YES Eclipse or Easy Eclipse would be your choices, ignore all these applications like Bluefish and so on since those have no proper auto-complete and intellisense. Eclipse is bit heavier but it takes to write code much lesser time than typing every single thing your self and remembering what object was that

---

### Post by lord bacon on 2007-05-31
so i have installed eclipse.. which is fine.. but how do i go about installing pdt. i have tried to use the update manager but it says im missing XYZ files etc so it cant DO it... what do i do now.

havnt ever tried any of this stuff before so step by step info would be much appreciated..


Thanks,
Lord Bacon

---

### Post by pestilence on 2007-06-05
For IDE you could try Activestate's Komodo I believe it's one of the best IDE out there.

---

