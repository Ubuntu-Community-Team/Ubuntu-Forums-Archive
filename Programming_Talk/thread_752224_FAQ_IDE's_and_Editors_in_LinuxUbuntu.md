---
title: "FAQ: IDE's and Editors in Linux/Ubuntu"
date: 2008-04-11
forum: Programming Talk
---

### Post by LaRoza on 2008-04-11
**See these links first:**
[list]
[*] [Wikipedia article on IDE's]("http://en.wikipedia.org/wiki/Integrated_development_environment")
[*] [Comparison of IDE's]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments")
[*] [Ubuntu Programming Tools]("http://ubuntuprogramming.wikidot.com/Tools")
[/list]

This thread is dedicated to helping you decide which IDE or editor to use. In the end, you can only decide for yourself, so try out the options.

There are many options for Linux, and none of them are "better" by definition. Use whatever you want.

[The Ubuntu Programming Wiki]("http://ubuntuprogramming.wikidot.com/Tools") has entries on various tools. Not all are there obviously. 

If you are used to Visual Studio in Microsoft Windows, you are likely wondering what is available for Linux. The answer is: anything you want. The free world and languages aren't tied to a single Application. Use what catches your fancy.

Most are in the repositories, so install through Synaptic or your preferred method. If they are not in the Ubuntu repositories, googling for them will get you their homepage usually. (The wikipedia links also will lead you to them)

This thread is four years old about this subject: [What's your Favorite IDE?]("http://ubuntuforums.org/showthread.php?t=6762")

**If you post a thread about which IDE to use, or which editor is better, it will be moved to Recurring Discussions or closed**

---

### Post by Gen2ly on 2008-04-11
good lists LaRoza, thanks!

---

### Post by Wybiral on 2008-04-17
Now if only we could develop as much as we bicker about which IDE is better... :)

---

### Post by Can+~ on 2008-04-17
I've been using [editra](http://editra.org/) 2 months already, and I can say, it's quite good.

When you type in python:
[PHP]mylibrary.<shows lists of content inside module>[/PHP]

---

### Post by LaRoza on 2008-04-17
> **Can+~ said:**
> I've been using [editra](http://editra.org/) 2 months already, and I can say, it's quite good.

When you type in python:
[PHP]mylibrary.<shows lists of content inside module>[/PHP]

Perhaps you could add it to the wiki?

---

### Post by Can+~ on 2008-04-17
> **LaRoza said:**
> Perhaps you could add it to the wiki?

Added: [Editra at wikidot](http://ubuntuprogramming.wikidot.com/editra)

---

### Post by Tuna-Fish on 2008-04-18
How exactly do you turn the completion on? I tried editra, but it doesn't seem to complete anything.

I'm using newest svn, the sourcefile was recognized to be python, and settings/autocompletion is on.

---

### Post by Can+~ on 2008-04-18
> **Tuna-Fish said:**
> How exactly do you turn the completion on? I tried editra, but it doesn't seem to complete anything.

I'm using newest svn, the sourcefile was recognized to be python, and settings/autocompletion is on.

It's actually lame, it does not complete as you type, but when you write

[PHP]import package

package.<list pops>

variable or function or class.<list pops>[/PHP]

the list is summoned, if you do Ctrl+K you can see the builtins. And make sure the Lexer is set to python.

It's no the kind of auto completition, as you type, but it's better than anything :(.

---

### Post by Harry_Iyer on 2008-12-18
> **wybiral said:**
> 
now if only we could develop as much as we bicker about which ide is better... :)


true. True.

_

---

### Post by olejorgen on 2008-12-18
Those who like IDEs might want to check out [http://trolltech.com/developer/qt-creator/qt-creator](http://trolltech.com/developer/qt-creator/qt-creator) (Haven't tried it myself)

---

### Post by shankhs on 2009-09-28
[This]("http://ubuntuforums.org/showthread.php?t=752224") thread by LaRoza is not working.Its pointing to:
[http://ubuntuprogramming.wikidot.com/Tools](http://ubuntuprogramming.wikidot.com/Tools)

where it says 
```

The page tools you want to access does not exist.

```
Can anybody please post any alternative link to ubuntu programming tools beside whats mentioned here.

---

### Post by nelsonspbr on 2009-10-10
QtCreator just rocks, one of the best (if not THE best) IDE I ever used... if your planning to use C++ with Qt or only C++, it is the best choice.

---

### Post by cjminton on 2010-01-27
> **LaRoza said:**
> **See these links first:**
[LIST]
[*] [Wikipedia article on IDE's]("http://en.wikipedia.org/wiki/Integrated_development_environment")
[*] [Comparison of IDE's]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments")
[*] [Ubuntu Programming Tools]("http://ubuntuprogramming.wikidot.com/Tools")
[/LIST]

This thread is dedicated to helping you decide which IDE or editor to use. In the end, you can only decide for yourself, so try out the options.

There are many options for Linux, and none of them are "better" by definition. Use whatever you want.

[The Ubuntu Programming Wiki]("http://ubuntuprogramming.wikidot.com/Tools") has entries on various tools. Not all are there obviously. 

If you are used to Visual Studio in Microsoft Windows, you are likely wondering what is available for Linux. The answer is: anything you want. The free world and languages aren't tied to a single Application. Use what catches your fancy.

Most are in the repositories, so install through Synaptic or your preferred method. If they are not in the Ubuntu repositories, googling for them will get you their homepage usually. (The wikipedia links also will lead you to them)

This thread is four years old about this subject: [What's your Favorite IDE?]("http://ubuntuforums.org/showthread.php?t=6762")

**If you post a thread about which IDE to use, or which editor is better, it will be moved to Recurring Discussions or closed**

3rd link from the top - Ubuntu Programming Tools brings you to a page that no longer exists.

---

### Post by nardis_Miles1 on 2010-01-28
Preamble:
I'm trying to find the right Forum and thread for a question about fonts in xemacs. I ended up here because xemacs can be used as an integrated development environment. If there is a better forum/thread, I would appreciate some guidance.

Question:
On upgrading to Karmic, and losing xorg.conf, the appearance of fonts in xemacs has degraded substantially. I had this experience several years ago and was able to fix it by ordering my FontPath carefully in *xorg.conf*. Is there a similar capacity in the absence of and active *xorg.conf* in */etc/X11*?

---

### Post by puzzler995 on 2010-03-10
eclipse is pretty good, expecially since it is in the repos ;)

---

### Post by Zanthir on 2010-10-16
I hesitate to use Mono because I feel like it is just a Microsoft product wannabe, lagging a few years behind. This is likely true just for it's support for the Microsoft library compatibility, and I know Mono is more than that.

I'm trying to convince my friend we should be doing our amatuer game programming in something compatible with Linux, but he still wants to use C#/.NET/XNA/DirectX with Visual Studio. 

I don't really see a compatible alternative in Linux. I think C++/Qt/(3d game library?)/OpenGL is as close as it comes. I guess Mono also has something close too. 

Anyone know of a good game library comparable to XNA? I'm posting this here because I'm guessing it will correlate with QtCreator, MonoDevelop, or some other IDE.

---

