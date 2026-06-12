---
title: "What is the easiest way for a web developer to make apps?"
date: 2006-07-28
forum: Programming Talk
---

### Post by OneSeventeen on 2006-07-28
I want to start learning how to program standalone applications, and I am very familiar with PHP 5, Javascript, and things like that.

I don't mind sticking with non-compiled stuff, such as XUL, but most of the tutorials out there don't work with current versions of Mozilla/XULRunner.

I also wouldn't mind learning how to use the mono project, or python, etc.  I just want to be able to write standalone apps that look good.

I'm going to be working on a lot of stuff that could easily be done on the web, but I don't want users to have to configure a web-server.  You know, like project management stuff.

Any tips on where to start?  I will be developing in Ubuntu, but hopefully have the end product work on any GNU/Linux system.  (I want to do a lot for education systems and things like that, so I don't mind singling out linux.  If they can afford Windows/Apple, then they might as well go all out and buy expensive software to do other tasks as well.)

---

### Post by Paerez on 2006-07-28
Just saw this on digg today:
[http://www.aptana.com/](http://www.aptana.com/)
Eclipse plugin for web development. So you could also throw a php plugin in the mix with eclipse.

---

### Post by ifokkema on 2006-07-28
Well, if you know PHP already, you could go for PHP-GTK ([gtk.php.net]("http://gtk.php.net")). I've got a simple game working in a few hours after browsing the PHP-GTK manual (on the website).

But distribution is different because there's no offical .deb in the Ubuntu repositories. It's easy to make one yourself, but still.
If you want portability, I'd suggest Python-GTK. You'll have to learn a new language, but it's used by many other apps within Ubuntu.

---

### Post by OneSeventeen on 2006-07-28
I've been hearing more and more about python GTK lately, so I'll look into it and see how well I pick it up.

Any great IDE's for PythonGTK?

I just went through a couple of tutorials on making PyGTK apps with Glade, and that's cool for the interface, but how about the coding itself?  gedit is nice, but for a beginner like me I like code hints so I spend more time learning and less time correcting spelling errors :D

Thanks for the tip though, it looks pretty strong and easy(ish) to use!

(I keep wanting to close off my classes though... this whole spacing dictating the structure thing is throwing me off!)

---

### Post by Paerez on 2006-07-28
I'm sorry I misread your original post, I thought you wanted to make web apps on linux.

In that case, ignore my first suggestion. PyGTK seems really cool, but Java may also be worth it in case your client changes their mind, then you can just port the code right over.

The down side being I am sure pygtk is much faster and easier. I just got into python, I want to play with pygtk too!

---

### Post by Note360 on 2006-07-28
Python well first of all take a step back from python and learn the basics ok, then in a day or two come back to PyGTK. Oh and dont use a IDE. Code corrections will kill you you think they help but it is like the teacher proofreading all your work in school helps at first hurts in the long run. Sit down with gEdit or Scribes (simple python program easy to install) and that gives you a list of words you already used.

Scribes = [http://scribes.sourceforge.net/](http://scribes.sourceforge.net/)

---

### Post by Note360 on 2006-07-28
One correction Scribes is a editor for everything (almost). I meant it is made in python, sorry for the confusion.

---

### Post by ifokkema on 2006-07-28
> **OneSeventeen said:**
> (I keep wanting to close off my classes though... this whole spacing dictating the structure thing is throwing me off!)
LOL, I'm so used to using braces too...

I'm currently messing around with PHP-GTK to get more familiar with GTK and signals/callbacks and all that. I assume the Py-GTK API is different in function names and such, but if I ever want to create something a little more 'distributable' I'm going to dive into Py-GTK, too.

---

### Post by Paerez on 2006-07-28
scribes looks fantastic! Is it suitable for editing all kinds of files, like xorg.conf and fstab and C/C++, etc? or is it mainly python?

I always wondered why when I start typing a function, normal editors wouldn't figure it out and give me a template. This looks great! There goes my weekend!

---

### Post by OneSeventeen on 2006-07-30
> **Note360 said:**
> Oh and dont use a IDE. Code corrections will kill you you think they help but it is like the teacher proofreading all your work in school helps at first hurts in the long run.
...
I would normally agree except for the fact that the way I learn is by seeing what is available.  In PHP this is simple because PHP.net has just about the easiest to use manual that I've ever seen.  Since I'm not the type of person to choose the function I *think* does what I want it to, when I see a list and am unsure of what they do, I'll look up each one to see which I need.  In the end, I've learned 2 or 3 functions for each function I use, rather than just searching for the specific one I need.

I will still definitely look into Scribes though.

Here's a quick question, how would you find out how to carry out a specific task in python?

Let's say you want to open a file and read it line by line using python, what is your first step in finding the appropriate function/method of doing this?

---

### Post by Paerez on 2006-07-30
The first thing I do is search for a tutorial, then search inside the tutorial for the answer. The reason for this is that tutorials always (hopefully) have the most simple or basic way of doing common things.

So for python, I go to the [official tutorial]("http://docs.python.org/tut/"), and find the [file reading and writing section]("http://docs.python.org/tut/node9.html#SECTION009200000000000000000"), and do things that way.

If that doesn't work, then I combine both searches and search google for "python tutorial file read write". Then you get many examples of many ways of doing something, and I comb over all of them to find the simplest way.

I like the simple ways, because it is easy to understand and it is probably the way the creator meant it to be done.

---

### Post by Van_Gogh on 2006-07-30
You could also check out the doc-string of the function/class/method you want to use. e.g. opening a file is done by the function open. So if you try

```
print open.__doc__
```
and you'll get some info about how to use files.

This can also be done with methods, e.g
```
a = open('somefile', 'r')
print a.readline.__doc__
```
It's very useful, I think.

---

### Post by Paerez on 2006-07-30
ohh that is cool.

This thread inspired me to make a pygtk ipod and neuros video conversion tool... I got the command running but no gui yet.

Scribes is cool but the whole "completing your () and ""s" annoys me because sometimes I decide to wrap a statement in () after I wrote it. So its like:

a+b
then I go:
a+b+c
then I try to encapsulate a and b, but when I type ( is does:
()a+b+c
then I have to delete the extra ).

---

### Post by adamkane on 2006-07-30
Give an example of a web app that you would like to see.

When I think of web apps, I think of a LAMP CMS. All you need to learn is PHP and MySQL.

The difference between Javascript and PHP is client-side versus server-side, and the main benefit of server-side is that you have access to a database, if you like.

Yes, I know PHP is limited. Ruby, Perl or Python is the way to go, unless you want to jump into the proprietary world of Java.

If you're interested in web animation, then you will be working with Flash or Java.

---

### Post by ifokkema on 2006-07-31
> **adamkane said:**
> Yes, I know PHP is limited. Ruby, Perl or Python is the way to go, unless you want to jump into the proprietary world of Java.
Just out of curiosity, which limitations are you referring to, compared to the other languages?

---

### Post by adamkane on 2006-07-31
I like PHP. It gave all the great LAMP CMS like osCommerce and Moodle. I was as sad as you to learn this.

What I don't like about PHP
[http://www.bitstorm.org/edwin/en/php/](http://www.bitstorm.org/edwin/en/php/)

Experiences of Using PHP in Large Websites
[http://www.ukuug.org/events/linux2002/papers/html/php/index.html](http://www.ukuug.org/events/linux2002/papers/html/php/index.html)

I’m sorry, but PHP sucks
[http://maurus.net/work/php-sucks/](http://maurus.net/work/php-sucks/)

"PHP in contrast to Perl"
[http://tnx.nl/php](http://tnx.nl/php)

I hate PHP
[http://keithdevens.com/weblog/archive/2003/Aug/13/HATE-PHP](http://keithdevens.com/weblog/archive/2003/Aug/13/HATE-PHP)

PHP Annoyances
[http://lumphammer.net/articles/phpannoyances/](http://lumphammer.net/articles/phpannoyances/)

---

### Post by OneSeventeen on 2006-07-31
I guess I haven't had the same experiences with PHP that others have had... I'm runing PHP5 on an old linux server I set up which replaces some tools written in ASP and Coldfusion on newer servers.   The PHP scripts have not had a single problem, whereas the ASP and Coldfusion will throw random server errors at non-regular intervals.

But, then again, most of the arguments were against the migration away from PHP 4, or were based solely on PHP 4.  I do agree that the recursion methods are bad, and there are a few other issues with PHP that make it not as good as it could be, but then again, I simply use PHP 5 and use the features available.  For web scripting I haven't found the need for recursion, and if I did, I'd simply write the recursive function in some other language, such as C++, and load it up as a PHP module, or have PHP execute a perl script to do the recursion.

But, that's neither here nor there, the whole point is I'm trying to get away from web applications, and towards stand-alone-apps.  I only mentioned that I'm a web-developer so my point of view would be known.

I would rather stay away from proprietary-land, hence no Java.  I'm not worried about employers switching since I'm in a LAPP shop (PostgreSQL instead of MySQL), and I want to make stand-alone apps for open-source elementary education tools.  If they want it coded in a different language, they are welcome to read the code and convert it themselves :D

Anyway, I'll give scribus a look-over and start going through the python tutorial and see what I can come up with.  

Thanks again for all the tips, and if anyone knows how to make differently-shaped windows with alpha transparency instead of the standard gnome interface, please let me know!

---

### Post by LordHunter317 on 2006-07-31
> **OneSeventeen said:**
>  In PHP this is simple because PHP.net has just about the easiest to use manual that I've ever seen.That's probably because it's one of the most simplistic and incomplete manuals ever seen too. 

> I do agree that the recursion methods are bad, They're not bad.   They're a really good thing to have, and all programmers should have a thorough understanding of recusion.

[quote=adamkane]Yes, I know PHP is limited. Ruby, Perl or Python is the way to go, unless you want to jump into the proprietary world of Java.[/quote]It's no less proprietary than  any other language.  Not being open source != being proprietary, despite what people want to believe.  Sun does not have sole control over Java anymore, nor would they want it.

---

### Post by ifokkema on 2006-07-31
> **adamkane said:**
> I like PHP. It gave all the great LAMP CMS like osCommerce and Moodle. I was as sad as you to learn this.
Thanks for the links. I googled up some more and also read some pro-php rants (even if it were just to make me feel a little better). There are some good points there, but with some authors I don't agree to the weight of the problem. Where I see a minor issue, they see a reason to burn PHP down to the ground. Either way, good reading, thanks.

---

### Post by LordHunter317 on 2006-07-31
There is no such thing as a minor issue with PHP.  The language is so poorly designed and implemented that it is simply impossible for any issue to really be minor.

---

### Post by Steveire on 2006-07-31
> 
a+b
then I go:
a+b+c
then I try to encapsulate a and b, but when I type ( is does:
()a+b+c
then I have to delete the extra ).

Select the a+b+c (either with the mouse, or if you're already at the 'c' end, just press ctrl+shift+left), then type your bracket, and the other one will be on the other end. That works in Kate at least.

Check out diveintopython.org. It also comes with ubuntu, so actually you already have it. You will be making apps with it in no time. I recommend boa constructor as an IDE.

---

### Post by Paerez on 2006-07-31
thanks I will check that out.

Anyone have any opinions on pydev for eclipse?
[http://pydev.sourceforge.net/](http://pydev.sourceforge.net/)

I love eclipse.

---

### Post by OneSeventeen on 2006-07-31
I haven't tried any of the eclipse tools yet... not with success anyway.  (it doesn't seem as noob friendly as other IDE's)

I just installed boa-constructor, and I must say wxWindows looks like a smarter option than pyGTK, since my finished project won't require isntalling wxWindows or pyGTK on the end user's machine... at least that's what I think I'm reading on the wxWindows page...

If I'm wrong, please let me know.

Anyway, I'll be looking for a tutorial somewhere to see how to get started on this, either way, python looks pretty interesting so far.

I'm going to go ahead and say I'd rather not see any more pro/anti PHP comments, since I'm just looking for a method of developing windowed apps, and the only reason PHP was mentioned was to describe previous programming experience.

---

### Post by Paerez on 2006-07-31
At least for pyGTK, there is no extra installation required for a default ubuntu system in order to run a pyGTK program.

---

### Post by OneSeventeen on 2006-08-03
Well, I'm going back to give pyGTK another try.

My first project will be a text editor (similar to the Boa Constructor tutorial) then as I learn python I want to add some FTP capabilities, so I can log onto my FTP server, download a file, work on it locally, and if I want, hit a key-command or button that uploads the file to the appropriate location.

Shouldn't be too hard once I learn a bit more about python.

Thanks again for the help guys.  I'll probably start a new thread once I get into the pyGTK app I want to make.

---

### Post by adamkane on 2006-08-04
If you program in Java, you'll likely have to make use of proprietary code. Very often you will write something, and not even know that you're using proprietary code.

There are fun and interesting ways to use Java in an opensource way, but you'll be missing out on the large Java vendor community.

---

### Post by OneSeventeen on 2006-08-04
That's why I like the idea of sticking with python.  I also wouldn't mind learning XUL, so I can just require Firefox... but then I'd have to update my code when new versions of firefox comes out...

bah, so many options!!

I'm going to push through with pyGTK for a while, and see how I like it, and my next big task will be XUL, but only after I find a good tutorial that works with the current version of firefox.

---

### Post by OneSeventeen on 2006-08-04
Oh, and one more thing, I installed SPE (Stani's Python Editor) and it is kind of weak, in that it brings up code-hints for objects like file, but if I create a new object, like f = file("somefile.txt") then if I hit f. there are no code hints, because it doesn't associate the file object with "f"...

But oh well, it is still a good color-coder, and helps me to not mispell my variables.

I also find it weird that when I save a file, it automatically changes the permissions for me... which is nice, since I don't *really* need my python apps to be executable...  :p  (I'm sure it is a setting I'm missing, but it is kind of a weird default)

---

