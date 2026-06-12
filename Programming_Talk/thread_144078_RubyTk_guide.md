---
title: "Ruby/Tk guide"
date: 2006-03-13
forum: Programming Talk
---

### Post by zkissane on 2006-03-13
Is there a good guide for Tk programming in Ruby, either in print or on the intarweb?  I found the online version of _Programming Ruby: The Pragmatic Programmers' Guide_ at [http://www.rubycentral.com/book/index.html](http://www.rubycentral.com/book/index.html) but the Tk chapter was kind of underwhelming.  And, of course, I've Googled the subject but there's a low signal to noise ratio.  Most of the "tutorials" are one page "Here's a dialog with buttons!  Have fun!" type things.

Also, does anybody have the 2nd edition of _Programming Ruby_?  Is it worth buying despite the fact that the first edition is freely available?

---

### Post by celloandy on 2006-03-14
I'm not aware of any specific guide, but out of curiosity, why Tk?  I know some people (especially Tcl people) still use it, but feature-wise, it's lacking in a lot of pretty important areas (antialiased text, internationalization, etc.), if I'm not mistaken, and there are several other toolkits that are much better-supported, these days.  Gtk+, the GUI toolkit that makes Gnome (and, hence, Ubuntu) tick, is very well-supported, with actively maintained bindings that are easy to install using apt.  Their webpage is [http://ruby-gnome2.sourceforge.jp/](http://ruby-gnome2.sourceforge.jp/), and I see that they have tutorials linked from their front page for Gtk, Gstreamer, and other interesting libraries.  I've done almost no Ruby programming, so I can't really assess how good either the bindings or the tutorials are, but I hear good things, and Tk is just so ugly...

Anyway, I know I didn't directly answer your question, and for that, I'm sorry.  Best of luck in finding a Tk guide if that's really what you want.

Andrew

---

### Post by Jessehk on 2006-03-14
> 
Also, does anybody have the 2nd edition of Programming Ruby? Is it worth buying despite the fact that the first edition is freely available?


Also interested in an answer, here.

---

### Post by zkissane on 2006-03-14
[QUOTE=celloandy]I'm not aware of any specific guide, but out of curiosity, why Tk?  I know some people (especially Tcl people) still use it, but feature-wise, it's lacking in a lot of pretty important areas (antialiased text, internationalization, etc.), if I'm not mistaken, and there are several other toolkits that are much better-supported, these days.  Gtk+, the GUI toolkit that makes Gnome (and, hence, Ubuntu) tick, is very well-supported, with actively maintained bindings that are easy to install using apt.  Their webpage is [http://ruby-gnome2.sourceforge.jp/](http://ruby-gnome2.sourceforge.jp/), and I see that they have tutorials linked from their front page for Gtk, Gstreamer, and other interesting libraries.  I've done almost no Ruby programming, so I can't really assess how good either the bindings or the tutorials are, but I hear good things, and Tk is just so ugly...

Anyway, I know I didn't directly answer your question, and for that, I'm sorry.  Best of luck in finding a Tk guide if that's really what you want.

Andrew[/QUOTE]

Honestly, I just picked Tk because that's what the online Ruby book used.  I'll look into Gtk.  Outside of MS, Java and wxWidgets, my awareness of GUI toolkits is limited.

---

### Post by roarskater on 2006-07-19
hey to adress the question "Also, does anybody have the 2nd edition of Programming Ruby? Is it worth buying despite the fact that the first edition is freely available?", i have the 2nd edition actually and in the begining of the book it tells u what is new with it such as:
in the first half of the book, they added six new chapters, getting started is a more complete introduction to getting up-and-running with ruby, the chapter on threads was extended, the chapter on web programming has alternative templating systems and a section on SOAP. the language reference chapter has been significantly extended, the built in classes and modules portion of the book has more than 250 changes, and then theres also a section on the standard library, which has grown a lot since ruby 1.6.
I think for the most part thats what it says changed to summarize it.. u dont really NEED to buy it from what i can tell, but I personnaly like to have a paper book sitting infront of me rather than clicking back and forth while im trying to program, especially when learning something new. so its really your choice.

and to adress the TK guide, the closest thing to an actual guide i actually found was probably [http://members.chello.nl/~k.vangelder/ruby/learntk/hello.html](http://members.chello.nl/~k.vangelder/ruby/learntk/hello.html)

its not great, but that + pragmatic programmers guide and some of the links off of that site may give u atleast a little bit of TK.. i think theres actually a fairly big TK library link off of that site too.

---

