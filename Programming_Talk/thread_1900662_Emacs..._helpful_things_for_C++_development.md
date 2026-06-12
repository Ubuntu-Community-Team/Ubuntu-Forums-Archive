---
title: "Emacs... helpful things for C++ development"
date: 2011-12-26
forum: Programming Talk
---

### Post by kerryhall on 2011-12-26
I was wondering if emacs supports a few helpful things that other IDEs support.

First of all, I was wondering if it was possible to search for a variable name, and see where in the current source tree a variable with that name is declared.

Secondly, I was wondering if it would be possible to have a small subwindow that shows a list of classes, showing member variables and such, the same way that dev-c++ does?

Third, how about a popup window showing the kind of arguments a function expects, while typing out a function name, in the same way dev-c++ does? 

Finally, how about member function autocompletion? So if I have a point class, with a member function print(), and I have 
point mypoint; 

Then when I start typing 
mypoint.print();

By the time I get to mypoint. I would like to have a dropdown box showing the possible functions, maybe some info about the functions like return type and what arguments they take, and tab autocompletion.

Are those things possible and implemented in emacs?

Thanks!!

---

### Post by JDShu on 2011-12-27
I recommend cscope for navigating and reading code.

---

### Post by matthew.ball on 2011-12-28
> **kerryhall said:**
> I was wondering if emacs supports a few helpful things that other IDEs support.

First of all, I was wondering if it was possible to search for a variable name, and see where in the current source tree a variable with that name is declared.

Secondly, I was wondering if it would be possible to have a small subwindow that shows a list of classes, showing member variables and such, the same way that dev-c++ does?

Third, how about a popup window showing the kind of arguments a function expects, while typing out a function name, in the same way dev-c++ does? 

Finally, how about member function autocompletion? So if I have a point class, with a member function print(), and I have 
point mypoint; 

Then when I start typing 
mypoint.print();

By the time I get to mypoint. I would like to have a dropdown box showing the possible functions, maybe some info about the functions like return type and what arguments they take, and tab autocompletion.

Are those things possible and implemented in emacs?

Thanks!!
Hey, hopefully I can be of *some* help here - though, I don't actually have experience *using* this extension, so I can't help in setting it up.

But anyway, there is an emacs project called [CEDET]("http://cedet.sourceforge.net/") (Collection of Emacs Development Environment Tools) which achieves what I believe you are asking for, a screenshot can be found [here]("http://cedet.sourceforge.net/img-gen/ecb.png").

Now, how you go about setting up this beast, I am not quite sure. Some suggestions can (hopefully) be found [here]("http://www.emacswiki.org/emacs/CollectionOfEmacsDevelopmentEnvironmentTools") and [here]("http://alexott.net/en/writings/emacs-devenv/EmacsCedet.html"). In advance, I apologise if they are no help (I have heard that CEDET is *very* difficult to get working entirely).

Now, from my own experience, while I can't quite offer answers for everything you asked about, I can explain what has worked for me. [This]("http://www.youtube.com/watch?v=rGVVnDxwJYE") video demonstrates, and explains, how to set up an auto-complete feature for emacs (I do not remember if it says how to make the tab key work "properly" with this [i.e. indent or auto-complete depending on context] - if it doesn't, post so here and I'll give you the code which makes the tab key behave as it should).

---

