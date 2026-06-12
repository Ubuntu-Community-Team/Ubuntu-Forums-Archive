---
title: "Perl or PHP?"
date: 2005-04-20
forum: Programming Talk
---

### Post by drummer on 2005-04-20
Hi, I am currently starting my software design major work for school and want to create a blog tool. 

It'll have text entry, possibly with WYSIWYG formatting (a bit like the editor i'm writing in now; but with the formatting viewable in the text, not just the tags), an image gallery, an archive section and a profile page with various other information. Information will be stored in a database (MySQL?) and the whole thing will be web based web-based with editing done with the use of forms.

Would it be better to use PHP or Perl for this project? I originally looked at Perl as i was thinking of going a GUI as well, but the GUI idea is no longer and now PHP looks good as well. I've played a bit with PHP before but not really with database interaction and don't know which to choose.

Thanks for your help,
Owen

---

### Post by kperkins on 2005-04-20
Basically the question is--which language are you more comfortable in?
I've used both types of blog, and there's not much difference from the user end, really.
I like PHP better because I'm more comfortable with it, and think that the code looks cleaner, and PHP works very well with databases (better than Perl, as far as I'm concerned).
My 2 cents (which ain't worth much now-a-days). :razz:

---

### Post by jdonnell on 2005-04-20
I'd use php

---

### Post by drummer on 2005-04-20
thanks for the speedy replies.. php does look like the better choice, but any ideas of how to do the WYSIWYG thing, with the text formatting displayed updated in realtime as it is changed/applied? or if it is actually possible to do in php?

This type of WYSIWYG is used in the hotmail and gmail email composing things if you don't know what i'm talking about...

---

### Post by kperkins on 2005-04-20
The WYSIWYG editor that you're talking about is, obviously, possible in PHP, since this forum is written in PHP (as are most forums).  I know of a couple of blogs that are written with WYSIWYG editors for posting (it's not really WYSIWYG per se, but I do know what you're talking about)--WordPress is a good example of that.

---

### Post by hamiltjr on 2005-04-21
From my experience, PHP offers much more capability in and of itsself. With Perl, you either end up writing all of the scripts entirely by yourself, or searching for an already mand Perl Module to suit your needs. In my opinion, PHP is much nicer and put together. The only times I have had to revert to using Perl is when I was working on a webserver that didnt support PHP... so for me PHP is the only way to fly.
[B]
My vote: PHP[/B]
 :)

---

### Post by dataw0lf on 2005-04-21
I used to be a Perl advocate... then I met my trusty friends PHP and Python.  They completely replace any use I might've had for Perl, whatsoever.  Honestly, I don't see any reason for anyone, in any situation, to use Perl anymore ;).

---

### Post by sas on 2005-04-21
I'd use ASP.net and mono if there was the choice....

I'd go with php though...the db stuff isn't that hard to do iirc...

---

### Post by jdonnell on 2005-04-21
[QUOTE=sas]I'd use ASP.net and mono if there was the choice....
[/QUOTE]

With vbscript or c#?

Man, I do php, python, and .net at work. I'd never choose .net over php or python. What is it you like about .net?

---

### Post by sas on 2005-04-21
vb.net is all I know at the minute...I intent to start playing with C# sometime this week though...

The nice thing about asp.net /asp.mono (?) is the way it forces seperation of design and code, it's similarity to mono/.net desktop programming, object orientation, useful (though buggy) IDE - webmatrix, free forms validation..

It just seemed to work rather nicely, when I tried PHP a couple of years ago it just seemed kind of kludgy - though I've done a lot more programming since so maybe that'll help and I've never really used python aside from a couple of tutorials

---

### Post by jdonnell on 2005-04-22
You should check out ruby on rails, I think you may like it a lot. I agree about php. It doesn't give you any structure up front, but there are projects that provide forced structure for it. 
[Subway](http://subway.python-hosting.com/) for python is something you might want to look at as well.

---

### Post by sas on 2005-04-22
[QUOTE=jdonnell]You should check out ruby on rails, I think you may like it a lot. I agree about php. It doesn't give you any structure up front, but there are projects that provide forced structure for it. 
[Subway](http://subway.python-hosting.com/) for python is something you might want to look at as well.[/QUOTE]
 I've had ruby on rails bookmarked since it was annouced on /. and still never got around to checking it out...I've never checked out the forced structure php stuff, I guess I should write php "properly" anyway, but it's so easy to kludge it ;)

I've bookmarked subway, I've been meaning to look at python in more depth but just not got around to doing it..

---

### Post by drummer on 2005-04-23
[QUOTE=jdonnell]You should check out ruby on rails, I think you may like it a lot. I agree about php. It doesn't give you any structure up front, but there are projects that provide forced structure for it. 
[Subway](http://subway.python-hosting.com/) for python is something you might want to look at as well.[/QUOTE]
 in what way does php not give any structure upfront? and what's this 'forced structure'? sorry, i haven't really done any programming in php, python, ruby, etc.. only pascal  :? ... and scripting (html, css).
thanks for all your help and opinions though..  :)

---

### Post by jdonnell on 2005-04-23
[QUOTE=drummer]in what way does php not give any structure upfront? [/QUOTE]

I didn't explain it right. When doing web programming you usually want to do an MVC pattern that seperates your data modeling and business logic from the code that makes teh html. Ruby on rails forces you to do this where php doesn't. In php you either have to set this up yourself or use something like [http://www.mojavi.org/](http://www.mojavi.org/)

---

