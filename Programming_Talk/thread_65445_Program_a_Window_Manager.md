---
title: "Program a Window Manager???"
date: 2005-09-14
forum: Programming Talk
---

### Post by slooksterpsv on 2005-09-14
How do you create a Window Manager for Linux? I would like to try and create my own. Does anyone have any links/tutorials/etc. that I could look at? If so that would be greatly appreciated.

---

### Post by -Rick- on 2005-09-14
I don't know any tuts or so...but I think it might be a good idea to studying src code of simple WM's (TWM? Ratpoison?)

---

### Post by jerome bettis on 2005-09-14
i don't think you understand how ambitious something like that is.  i'm sure all the window managers that exist have dozens of developers that have spent lots of hours over several months (even years) working on them. download the source for metacity (or any other one) and i think you'll be surprised by the amount and complexity of code.  it would take me a few days at the very least to look at the code and see what does what.

so unless either A) you're a beast and can write lots of working code quickly (probably not judging by your post - no offense meant) B) you've got lots of free time over the next few months C) you just want one that's *very* simple or D) you've got a crew of developers, i wouldn't bother.  

you're probably better off taking a look at one of the more flexible window managers such as fvwm, fluxbox etc and see if they already do what you want to program.  fvwm is amazingly customizable, if you want to do it, you probably can.  there's lots of hype about enlightenment 17 (useless eyecandy), maybe that's what you're looking for.
 
also you can use programs like wmctrl and devilspie to do things you normally can't with the window manager. 

hope that helps

---

### Post by slooksterpsv on 2005-09-14
[QUOTE=jerome bettis]i don't think you understand how ambitious something like that is.  i'm sure all the window managers that exist have dozens of developers that have spent lots of hours over several months (even years) working on them. download the source for metacity (or any other one) and i think you'll be surprised by the amount and complexity of code.  it would take me a few days at the very least to look at the code and see what does what.

so unless either A) you're a beast and can write lots of working code quickly (probably not judging by your post - no offense meant) B) you've got lots of free time over the next few months C) you just want one that's *very* simple or D) you've got a crew of developers, i wouldn't bother.  

you're probably better off taking a look at one of the more flexible window managers such as fvwm, fluxbox etc and see if they already do what you want to program.  fvwm is amazingly customizable, if you want to do it, you probably can.  there's lots of hype about enlightenment 17 (useless eyecandy), maybe that's what you're looking for.
 
also you can use programs like wmctrl and devilspie to do things you normally can't with the window manager. 

hope that helps[/QUOTE]
 I guess source is the only wayt to go. Thanks, I'll go find one, probably fvwm, and download it - or maybe fluxbox. Thanks

---

### Post by SilentCacophony on 2005-09-14
The great thing about open source is just that. You can look at, and use the source code.

I would try out some of the simple, stable wm's, and find one to build upon. That's how many of them start.

In any case, it never hurts to research [GNU](http://www.gnu.org/) and [OSI](http://www.opensource.org/index.php). And I can't forget the [FSF](http://www.fsf.org/).

---

### Post by LordHunter317 on 2005-09-14
[QUOTE=jerome bettis]i don't think you understand how ambitious something like that is.[/quote]Not really.  The X11R6 Programmer's Manual has a chapter dedicated to basic window managers, and even has complete code.  Of course, it's not even to TWM functionality, but the basics aren't terribly, terribly hard.

Modern WMs are bit harder, but it's not terribly difficult if you have competent coding skills and X11 library experience (and not through a toolkit).

If you don't have either, then yes, it could be quite a task.

---

### Post by jerome bettis on 2005-09-14
^ w3rd

then why does metacity suck so bad?? :-P

---

