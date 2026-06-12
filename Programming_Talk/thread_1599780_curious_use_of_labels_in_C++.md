---
title: "curious use of labels in C++"
date: 2010-10-18
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-18
No doubt most of us know of using labels with dreaded goto statement and inside classes we label parts as private:/protected:/public: but learning QT atm I see the following:
[php]
class CannonField : public QWidget {
public:
... usual bunch of methods

// but what use is a public label here ?
public slots:
     void setAngle(int angle);
     void setForce(int force);

// and another label here?
signals:
     void angleChanged(int newAngle);
     void forceChanged(int newForce);

 protected:
... then back on familiar terrain
[/php]

if I take out it won't compile :confused:

---

### Post by GeneralZod on 2010-10-18
Those aren't labels: those are some of the "extensions" to C++ that Qt uses for its [signals and slots](http://doc.trolltech.com/4.7/signalsandslots.html) system - they are processed automatically by Qt's [moc](http://doc.trolltech.com/4.7/moc.html) tool into "normal" C++ prior to compilation.

Think of them as artificial syntactic sugar :)

Edit:

Oh, and I may as well nip this in the bud - it's "Qt", not "QT" ;)

---

### Post by worksofcraft on 2010-10-18
> **GeneralZod said:**
> Those aren't labels: those are some of the "extensions" to C++ that Qt uses for its [signals and slots](http://doc.trolltech.com/4.7/signalsandslots.html) system - they are processed automatically by Qt's [moc](http://doc.trolltech.com/4.7/moc.html) tool into "normal" C++ prior to compilation.

Think of them as artificial syntactic sugar :)

Edit:

Oh, and I may as well nip this in the bud - it's "Qt", not "QT" ;)

Ah... OK that makes more sense now, TYVM :)
I don't particularly like proprietary language extension pre- processors like this, but I suppose it's better than having to learn a whole new language like C# or Vala and it makes me wonder what is so beneficial about the esoteric extensions that it couldn't have been solved with regular language features :shock:

---

### Post by GeneralZod on 2010-10-18
Vala basically *is* a "proprietary language extension pre-processor" ;)

Qt's signals and slots (as well as it's QProperties) provide run-time introspection of an objects capabilities, allowing you to greatly reduce the coupling between objects - you can connect objects together that literally have no knowledge of each other at all - something that's awkward to pull off in a statically-typed language like C++.

---

### Post by nvteighen on 2010-10-18
> **worksofcraft said:**
> Ah... OK that makes more sense now, TYVM :)
I don't particularly like proprietary language extension pre- processors like this, but I suppose it's better than having to learn a whole new language like C# or Vala and it makes me wonder what is so beneficial about the esoteric extensions that it couldn't have been solved with regular language features :shock:

When using Qt, always keep in mind that it was designed when there was no C++ standard yet... and that it had to keep several features because of backwards compatibility.

---

### Post by worksofcraft on 2010-10-19
> **nvteighen said:**
> When using Qt, always keep in mind that it was designed when there was no C++ standard yet... and that it had to keep several features because of backwards compatibility.

Hummm... yes well I'm not that happy with QT now that I've had a chance to experiment.

What I'm actually working towards is a fully functional bidirectional language terminal emulator. That is one that can handle a mixture of left to right and right to left languages.

Like Gtk, Qt has all the official algorithms built in. So to test it oout, I hacked an Arabic text into [QT tutorial #8]("http://doc.trolltech.com/4.3/tutorial-t8.html") and once I changed "tr" to "trUtf8" it seemed to work... up to the point when I moved the slider. Suddently numbers displayed were hopped from the left side to the right side of the text and back again depending on their magnitude :shock:

ANyway I planned to prune out the irrelevant bits and just display some bidirectional text. I started simply copying all the .h and .cpp files into one single source file that was perfectly legitimate by C++ standards (with exception of afore mentioned QT extensions) and I get stacks of inexplicable linker messages like:
```

cannonmain.cpp:(.text+0x72): undefined reference to `vtable for LCDRange'

```

Then I notice QT doesn't use gettext for internationalization and has it's own localization hard coded for the set of languages that it supports.

That trUtf8 call that was necessary to display my utf-8 characters also implied it was going to try and translate it all and in my terminal emulator application that is really NOT what I want: I'm displaying what the user is typing as well as the output from any commands that run, and those will be using their own l10n facilities where applicable :confused:

So as far as I'm concerned QT is simply too clever for it's own good :P I need something dumber... like perhaps I take it back to the original X11 interface :popcorn:

---

### Post by spjackson on 2010-10-19
> **worksofcraft said:**
> Hummm... yes well I'm not that happy with QT now that I've had a chance to experiment.

After a short spell using Qt any problems you have encountered will naturally by down to defects in Qt.
> 
What I'm actually working towards is a fully functional bidirectional language terminal emulator. That is one that can handle a mixture of left to right and right to left languages.

Like Gtk, Qt has all the official algorithms built in. So to test it oout, I hacked an Arabic text into [QT tutorial #8]("http://doc.trolltech.com/4.3/tutorial-t8.html") and once I changed "tr" to "trUtf8" it seemed to work... up to the point when I moved the slider. Suddently numbers displayed were hopped from the left side to the right side of the text and back again depending on their magnitude :shock:
If you have found a demonstrable, repeatable bug in Qt, then why don't you report it? Did you report any of the Gtk faults you found to the Gtk project?
> 
ANyway I planned to prune out the irrelevant bits and just display some bidirectional text. I started simply copying all the .h and .cpp files into one single source file that was perfectly legitimate by C++ standards (with exception of afore mentioned QT extensions) and I get stacks of inexplicable linker messages like:
```

cannonmain.cpp:(.text+0x72): undefined reference to `vtable for LCDRange'

```Yes, moc is defective: it fails when users ignore the instructions.
> 
Then I notice QT doesn't use gettext for internationalization and has it's own localization hard coded for the set of languages that it supports.
Naturally, Qt does not use gettext because gettext is GPL. The GPL is not compatible with Nokia's (and formerly Trolltech's) licensing policy.
> 
That trUtf8 call that was necessary to display my utf-8 characters also implied it was going to try and translate it all and in my terminal emulator application that is really NOT what I want: I'm displaying what the user is typing as well as the output from any commands that run, and those will be using their own l10n facilities where applicable :confused:
The tr() and trUtf8() calls do indeed try to translate whatever you pass them. If you don't want the translation, then fromUtf8() might be what you are looking for. The functions should perhaps have been called trStandsForTranslate() and trStandsForTranslateUtf8().
> 
So as far as I'm concerned QT is simply too clever for it's own good :P I need something dumber... like perhaps I take it back to the original X11 interface :popcorn:I look forward to the list of defects you find in X11.

Now I have no particular axe to grind in defending Qt - I am merely a user and I do have my own criticisms. However, I note that the problems you have had in your project have all been the fault of Gtk, C++ and now Qt. I do wonder whether you are possibly being a little unfair.

If you direct your concerns to the qt-interest mailing list, expressed rationally and calmly, I would be surprised if Thiago Maciera did not do his best to address them. You might also be interested to read some of Josh Grauman's (fairly recent) postings on his Hebrew project. However, you seem to have already dismissed Qt as not fit for purpose, so perhaps there's not much point in that.

---

### Post by dwhitney67 on 2010-10-19
> **worksofcraft said:**
> 
ANyway I planned to prune out the irrelevant bits and just display some bidirectional text. I started simply copying all the .h and .cpp files into one single source file that was perfectly legitimate by C++ standards (with exception of afore mentioned QT extensions) and I get stacks of inexplicable linker messages like:
```

cannonmain.cpp:(.text+0x72): undefined reference to `vtable for LCDRange'

```


The error above tells me that you did not implement one or more virtual methods in the LCDRange class.  This is not a Qt problem... this is a programmer problem.

---

### Post by worksofcraft on 2010-10-19
> **spjackson said:**
> After a short spell using Qt any problems you have encountered will naturally by down to defects in Qt.
If you have found a demonstrable, repeatable bug in Qt, then why don't you report it? Did you report any of the Gtk faults you found to the Gtk project?
Yes, moc is defective: it fails when users ignore the instructions.
Naturally, Qt does not use gettext because gettext is GPL. The GPL is not compatible with Nokia's (and formerly Trolltech's) licensing policy.
The tr() and trUtf8() calls do indeed try to translate whatever you pass them. If you don't want the translation, then fromUtf8() might be what you are looking for. The functions should perhaps have been called trStandsForTranslate() and trStandsForTranslateUtf8().
I look forward to the list of defects you find in X11.

Now I have no particular axe to grind in defending Qt - I am merely a user and I do have my own criticisms. However, I note that the problems you have had in your project have all been the fault of Gtk, C++ and now Qt. I do wonder whether you are possibly being a little unfair.

If you direct your concerns to the qt-interest mailing list, expressed rationally and calmly, I would be surprised if Thiago Maciera did not do his best to address them. You might also be interested to read some of Josh Grauman's (fairly recent) postings on his Hebrew project. However, you seem to have already dismissed Qt as not fit for purpose, so perhaps there's not much point in that.

:confused: I haven't dismissed anything.

I could spend all day every day for years reading all the opinions and research done by other people and no doubt different publications promote different perspectives. Without actually experiencing the problems first hand I probably won't even understand what they are talking about.

It is question of taking an objective look at the issues of programming with these different packages. Based on what I like and what I dislike I make a rational choice which I hope will prevent me from bashing my head against a dead-end brick wall further down the line.

Personally I greatly favor the principle of KISS: "Keep it simply stupid" and on that basis I don't like the moc system nor do I find it appealing that localization logic in QT seems to be hard coded into the package.

I had a good look at the code for gnome-terminal and the vte widget. From what I have seen I would not enjoy working on that code.

Motivation for developing something new is usually based on dissatisfaction with what is already available. If it were not for that, then you would probably still be programming in Cobol.

---

### Post by worksofcraft on 2010-10-19
> **dwhitney67 said:**
> The error above tells me that you did not implement one or more virtual methods in the LCDRange class.  This is not a Qt problem... this is a programmer problem.

Yeah that's what I thought too at first, but eventually I worked out that it's because I **have to** put all QOBJECT's in separate .h files so that the moc generated source files can include them. Strangely it doesn't complain at compile time but just gives above linker error.

Note: Regarding posting bug reports, Here are [images of R2L problems]("http://ubuntuforums.org/showthread.php?p=9994641#post9994641") with a simple string and number. It is debatable whether these are even bugs. Doing proper testing and identifying repeatability of such issues in any of these packages is a major project in it's own right and not one I  set out to be working on atm. A quick google tells us there are plenty of people who do actually know how their language needs to be displayed who have been posting such bug reports for many years.

---

### Post by scourge on 2010-10-19
> **worksofcraft said:**
> Yeah that's what I thought too at first, but eventually I worked out that it's because I **have to** put all QOBJECT's in separate .h files so that the moc generated source files can include them.

You don't have to do that. You can also put "#include "foo.moc" at the end of foo.cpp (the source file containing QObject-based class declarations).

---

### Post by dwhitney67 on 2010-10-19
I personally do not like Qt either, but apparently many people do like it.  Whatever!

As for displaying Western text, whether it be numbers, letters, or words, into Arabic or any other language, I'll leave that exercise to you, for I have no interest in such.

In my "world" (ie professional domain), one must speak and write in English.

---

### Post by worksofcraft on 2010-10-19
> **spjackson said:**
> 
I look forward to the list of defects you find in X11.


Meh... can't sleep... so I'm not one to keep people in suspense, but I haven't had any chance to experiment so I'll just have to make it all up as I go...

Now evidently X11's violation of the KISS rule is in it's concept of a "network". It was conceived back in the days of ancient time-sharing systems that centralized all processing power in one place to drive a bunch of dumb terminals.

These days processing power on a network is distributed and modern display capabilities go just a tad further than what VT100 compatible box drawing characters you need to specify in your terminfo database.

Thus to seriously leverage capabilities of contemporary advanced graphics engines one would need to be able to have control of things like 3-D vector rendering and all sorts of other stuff that I know absolutely nothing about (yet).

I have heard rumors of a company who realized that, and they created something called "direct-X" but surprisingly it has nothing to do with the X  windowing system ... although it does make for some truly awesome graphics I suspect :D

p.s. Oh I just had another insight: Many international character sets don't fit well in fixed width fonts and so having predefined terminal widths is probably going to cause some headaches, but overall I'm only aiming to emulate a dumb terminal so X11 will probably be the right tool for the job :)

Now I just read the first paragraph of the 466 page Xlib programmers manual and I see that to X a "display" is a set of multiple screens with **one keyboard** and one mouse, but I was thinking of somone who while working in one window is using **two** keyboards: Like one for typing Arabic and the other for English... anyway I better not jump to conclusions as I still have 465½ pages to go :shock:

---

### Post by worseisworser on 2010-10-19
> **worksofcraft said:**
> Meh... can't sleep... so I'm not one to keep people in suspense, but I haven't had any chance to experiment so I'll just have to make it all up as I go...

Now evidently X11's violation of the KISS rule is in it's concept of a "network". It was conceived back in the days of ancient time-sharing systems that centralized all processing power in one place to drive a bunch of dumb terminals.

These days processing power on a network is distributed and modern display capabilities go just a tad further than what VT100 compatible box drawing characters you need to specify in your terminfo database.

Thus to seriously leverage capabilities of contemporary advanced graphics engines one would need to be able to have control of things like 3-D vector rendering and all sorts of other stuff that I know absolutely nothing about (yet).

I have heard rumors of a company who realized that, and they created something called "direct-X" but surprisingly it has nothing to do with the X  windowing system ... although it does make for some truly awesome graphics I suspect :D

p.s. Oh I just had another insight: Many international character sets don't fit well in fixed width fonts and so having predefined terminal widths is probably going to cause some headaches, but overall I'm only aiming to emulate a dumb terminal so X11 will probably be the right tool for the job :)

Now I just read the first paragraph of the 466 page Xlib programmers manual and I see that to X a "display" is a set of multiple screens with **one keyboard** and one mouse, but I was thinking of somone who while working in one window is using **two** keyboards: Like one for typing Arabic and the other for English... anyway I better not jump to conclusions as I still have 465½ pages to go :shock:

I once ate an entire bag of popcorn; including the bag.

---

### Post by Simian Man on 2010-10-19
> **worksofcraft said:**
> ...

Wowzers. I'm speachless.

---

### Post by worksofcraft on 2010-10-22
> **Simian Man said:**
> Wowzers. I'm speachless.

Me too.

The simple task of plotting Unicode glyphs in both directions on a screen has lead me to a much better understanding of the whole gnome text rendering stack. Right down to the fundamental Xlib protocol that is being superseded by XCB, we find FreeType making way for OpenType and something called HarfBuzz replacing parts of Pango and Cairo libraries that QT and Gtk+ are based on...

All this progress is not driven by a bunch of "malcontents" but by people who take an objective look at the real issues. There are no mythical target locales, because the real trend of internationalization and Unicode is to have ALL languages ALL the time and to do that developers have to be willing to learn and reassess the internals and concepts of all that low level code that drives our high level abstractions.

---

