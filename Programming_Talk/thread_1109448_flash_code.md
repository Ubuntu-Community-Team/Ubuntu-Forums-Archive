---
title: "flash code"
date: 2009-03-28
forum: Programming Talk
---

### Post by miggys on 2009-03-28
Okay, I really have no clue how one programs in flash.  Trying to google for it makes it seem like you have to have some (proprietary windows) program where you click buttons to make your flash application.  I have found swftools and they have a short tutorial thing:

[**_swfc manual_**]("http://www.swftools.org/swfc/swfc.html")

This is what I want to do.  Actually write code.  

So here are my questions:

1)  Is this code stuff specific to swfc or is it just that everybody else uses some program that shields the user from having to look at actual code?

2)  Are there any more tutorials/examples/lists of functions that you know of?  The tutorial I linked doesn't seem too exhaustive.

3)  If I have an .swf or .fla file is there a way to see the actual text code?  I think that fla is the source code that the proprietary adobe program would use, so maybe it's possible to see the actual text code with it.  Obviously, examining working code is a good way to learn.

Thanks!!

---

### Post by NathanB on 2009-03-28
It is called ActionScript.  Read about it here:

[http://en.wikipedia.org/wiki/ActionScript](http://en.wikipedia.org/wiki/ActionScript)

You can obtain a free "third party" compiler here:

[http://www.libming.org/WhatsIncluded](http://www.libming.org/WhatsIncluded)

This tool will allow you to examine a symbolic representation of the bytecode (it runs in a Virtual Machine just like Java and .NET does) of existing SWF files:

[http://flasm.sourceforge.net/](http://flasm.sourceforge.net/)

You should search the 'net for ActionScript tutorials and examples...

Hope that helps...

---

### Post by Can+~ on 2009-03-28
I used Actionscript from version 1 (even earlier).

The language is very object oriented (AS3), the best part, is that you don't need anything special to work with the in-movie objects, for instance:

```
_root.movieclip1._x = 200;
```

Is completely valid (_root being the top frame).

Functions are declared with the function statement. And well.. the documentation of Adobe is pretty good, take a look and you'll soon get a grip on the language. I suggest starting directly with AS3, as AS2 is a huge mess (every variable is global).

If you are just playing around with fla and swf, I suggest to stay away from Adobe Flash ($700!).

---

### Post by miggys on 2009-03-29
thanks for helping to clarify this a bit.  I am just "playing around" mostly with the goal of theming my mp3 player and potentially making small applications for said mp3 player :)

Thanks

---

### Post by delfick on 2009-03-30
this might help :[http://ubuntuforums.org/showthread.php?t=742981](http://ubuntuforums.org/showthread.php?t=742981) :)

---

