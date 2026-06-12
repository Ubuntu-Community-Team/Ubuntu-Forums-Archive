---
title: "Should I start python by learning python 2 or python 3?"
date: 2010-03-14
forum: Programming Talk
---

### Post by superarthur on 2010-03-14
Sorry to ask another stupid question.
If I start learning python, should I start with python 2 or python 3? (Since they are incompatible with each other)
If python 2 is good enough, they don't have to make python 3. So I presume python 3 is better. However, most python codes are written in python 2, and python 2 is installed in ubuntu by default.
If I learn python 3, then it would not be compatible with what most people use, and it would be confusing to have 2 versions of python in my computer.
If I learn python 2, it may fade out slowly, and I'll have to learn python 3 all over again.

What should I do?

---

### Post by durand on 2010-03-14
Python 2 and 3 aren't that different really. I'd suggest learning python 2 as most of the libraries you might use are still written in python 2. If you don't intend to use many libraries however, python 3 would be fine. It's not very difficult to use python 3 once you've learnt python 2.

---

### Post by km0r3 on 2010-03-14
> **durand said:**
> Python 2 and 3 aren't that different really. I'd suggest learning python 2 as most of the libraries you might use are still written in python 2. If you don't intend to use many libraries however, python 3 would be fine. It's not very difficult to use python 3 once you've learnt python 2.

+1

Libraries are a good argument. **A lot of good** 3rd party Python applications/libraries haven't yet been ported to Python 3k. *They will*, but most Python programmers are still using Python 2.x.

*I think,* if you can write Python 2.x programs you will be able to write Python 3k programs.

---

### Post by Cracauer on 2010-03-14
They have small but very nasty differences, and when given a 2.x Python program there is no automatic way to determine whether it is compatible with Python 3.x. There is a serious possibility that the whole Python 3.x effort is dropped in favor of further 2.8 development because the uncertainty might be considered worse than dropping what little language improvements Python 3.x brings.

I would advise against using Python 3 for now. The language isn't that hot either way. What you want is libraries. You can't easily tell which libraries you can use in Python 3.

You will curse Python more than enough for version incompatibilities even with 2.x versions.

---

### Post by wmcbrine on 2010-03-14
I'm still waiting for certain libraries to be ported to 3 before I can port my own stuff... I have a feeling I may end up doing it myself.

My advice to the OP is to not try to [learn C](http://ubuntuforums.org/showthread.php?t=1427382) and Python simultaneously. :)

---

### Post by wmcbrine on 2010-03-14
> **Cracauer said:**
> There is a serious possibility that the whole Python 3.x effort is droppedWhere do you get this idea?

> *You will curse Python more than enough for version incompatibilities even with 2.x versions.*Oh, please. My only complaint is all the people still using old versions (like 2.4 in CentOS), which keeps me from taking advantage of nice new features in code I distribute. But even that is minor.

---

### Post by Cracauer on 2010-03-14
> **wmcbrine said:**
> Where do you get this idea?


That's what the development team says when you confront them with that 3.x doesn't have enough improvements to warrant incompatibilities that are undetectable before run time.

 > **wmcbrine said:**
> 
Oh, please. My only complaint is all the people still using old versions (like 2.4 in CentOS), which keeps me from taking advantage of nice new features in code I distribute. But even that is minor.

Yeah, that's why we have a by-weekly meeting about how to merge towards one version and no progress.

The lack of any compile time interface checking (with type checking) makes version incompatibilities bad, because you only know when you run.

---

### Post by wmcbrine on 2010-03-15
> **Cracauer said:**
> That's what the development team saysDo you have a citation for this?

As for that compile-time checking... clearly you want some other language. But that doesn't make Python deficient.

---

### Post by superarthur on 2010-03-15
> **wmcbrine said:**
> 
My advice to the OP is to not try to [learn C](http://ubuntuforums.org/showthread.php?t=1427382) and Python simultaneously. :)

Why not? :P
I learned Java and Perl almost simultaneously.

---

### Post by raydeen on 2010-03-15
If you work in 2.6 you'll have the benefit of having a foot in both worlds as 2.6 is a bridge between 2.x and 3.x. I tend to work in 2.6 and 3.1. The differences are minimal at the newbie stage. Learn both and you can't go wrong. :)

---

### Post by wmcbrine on 2010-03-15
> **superarthur said:**
> Why not? :P
I learned Java and Perl almost simultaneously.Focus, man, focus.

---

### Post by Cracauer on 2010-03-15
> **wmcbrine said:**
> Do you have a citation for this?


I don't recall whether that was a public conversation. Why don't you poll them for it?

> **wmcbrine said:**
> 
As for that compile-time checking... clearly you want some other language. But that doesn't make Python deficient.

The point here is that the situation with inter-version incompatibilities is much worse in Python than it is in other scripting languages.  Both Ruby and Perl design new versions to be more friendly towards running old code unchanged, or at least to be able to deal with it smoother. The Python 3 situation with the contents of strings being a version problem is about worst case for any kind of automatic or even human scanning for upgrade problems.

If you want to use Python to learn a new language today, Python 3 is clearly not the way to go.

---

### Post by wmcbrine on 2010-03-15
> **Cracauer said:**
> I don't recall whether that was a public conversation. Why don't you poll them for it?In other words, no, you don't have a citation. I gotta say, it's a pretty sensational claim to post without a citation. Not that I think you're being dishonest, but I doubt that you understood correctly.

> *The point here is that the situation with inter-version incompatibilities is much worse in Python than it is in other scripting languages.*I've never had a problem moving code forward through the 2.x series. 2 to 3 is an issue, yes. But so what? 2.x is still available. And the changes in 3.x are a clear win.

> *If you want to use Python to learn a new language today, Python 3 is clearly not the way to go.*Yes, 2.x is still more practical for most purposes. And I have to admit, the transition is going more slowly than I'd hoped.

---

### Post by Cracauer on 2010-03-15
> **wmcbrine said:**
> In other words, no, you don't have a citation. I gotta say, it's a pretty sensational claim to post without a citation. Not that I think you're being dishonest, but I doubt that you understood correctly.


I just re-checked to see what the newest status is, and that seems it is 3.x or death.  Looks like my info was out of date. Fine.

> **wmcbrine said:**
> 
I've never had a problem moving code forward through the 2.x series. 2 to 3 is an issue, yes. But so what? 2.x is still available. And the changes in 3.x are a clear win.


I don't think so. I don't use any form of unicode or international characters, much less requiring them in the default strings. There would have been ways to deal with this without making a mess out of old users of binary data in strings - after Python forced them to do so in the first place (there was no good place to hold binary  chunks).

The problem with 2.x to 2.y compatibility is not so much that things *are* incompatible. The problem is that you just don't know and have no easy way of telling.  That is why you have meetings with lots of people in a company all "requiring" a specific version of Python.  They know which version does work for them and they can't easily tell which others would.  So they have a version they "require". Kinda.

> **wmcbrine said:**
> 
Yes, 2.x is still more practical for most purposes. And I have to admit, the transition is going more slowly than I'd hoped.

Python 3.x does not only introduce incompatibilities, it chose to ignore a whole bunch of things that would have been important to some people, starting from the C interface.  Only a small minority of people actually benefit from what made it into 3.x.

Given the situation as it is it would have been better to break more stuff but get more people excited about 3.x.

This is an entirely predictable situation, I think.

Python is not a commercial system that can just stop selling the old version and force users to upgrade.

---

### Post by soltanis on 2010-03-15
Nothing particularly exciting about Python 3.

The dealbreaker for me was the fact that most systems that do ship with Python nowadays (OS X, Linux) go with Python 2.4 or 2.6, not 3. So I write with 2.6 compatibility in mind. That and the fact that most libraries are still only compatible with the 2.x branch.

---

