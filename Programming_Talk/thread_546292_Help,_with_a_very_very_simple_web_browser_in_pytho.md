---
title: "Help, with a very very simple web browser in python"
date: 2007-09-08
forum: Programming Talk
---

### Post by Yuzem on 2007-09-08
I know very little about python, but what I want to do is really simple:
A gtk window able to play a flash video. (no menus, no toolbar, nothing more)
For example this address:
[http://www.youtube.com/v/n-yMH8XzhlU](http://www.youtube.com/v/n-yMH8XzhlU)

The best option that I have found was to embed mozilla into a gtk application.

I followed this tutorial:
[http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html](http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html)

But it give me the following error:
```
Traceback (most recent call last):
  File "/home/azd/Desktop/flash", line 6, in <module>
    import gtkmoz
ImportError: No module named gtkmoz
```

I don't know how to install that. I want it to have dependencies that can be installed from the repositories. (I plan to make a deb)

Any ideas? 
Thanks in advance.

---

### Post by tenmillionmilesaway on 2007-09-08
I dont know anything about python but have you considered making your application in xul ([http://en.wikipedia.org/wiki/XUL](http://en.wikipedia.org/wiki/XUL)) ie use mozilla directly rather than embed it in another language.  I only say this as I have used it before and it is dead easy to make a simple browser using this approach.  Also while im not sure about the python bindings, the Java bindings for Mozilla are very buggy.

---

### Post by CptPicard on 2007-09-08
A flash player is not a web browser. A web browser is not always a flash player.

You do not in general need a simple web browser, you just need a flash playing component... of course if you can't manage that, on the KDE side you might consider embedding Konqueror's KPart, if that has flash enabled.

Are you sure there is no such thing as an app that specializes in just running the flash? I mean, if you are to run a browser, you'd have to probably parse and crop the HTML as well to get the kind of display you probably want.

---

### Post by Yuzem on 2007-09-09
> **tenmillionmilesaway said:**
> I dont know anything about python but have you considered making your application in xul ([http://en.wikipedia.org/wiki/XUL](http://en.wikipedia.org/wiki/XUL)) ie use mozilla directly rather than embed it in another language.  I only say this as I have used it before and it is dead easy to make a simple browser using this approach.  Also while im not sure about the python bindings, the Java bindings for Mozilla are very buggy.
I tried to write something in xul yesterday but it opens with firefox. (I am very newbie) :(

> **CptPicard said:**
> A flash player is not a web browser. A web browser is not always a flash player.

You do not in general need a simple web browser, you just need a flash playing component... of course if you can't manage that, on the KDE side you might consider embedding Konqueror's KPart, if that has flash enabled.

Are you sure there is no such thing as an app that specializes in just running the flash? I mean, if you are to run a browser, you'd have to probably parse and crop the HTML as well to get the kind of display you probably want.
I don't know any app for that.
I thought that it was a simple thing to do.
A screenshot of epiphany doing what I wanted to do:
[[IMG]http://img360.imageshack.us/img360/4616/avatarfactoryyoutubeax3.th.jpg[/IMG]](http://img360.imageshack.us/my.php?image=avatarfactoryyoutubeax3.jpg)

The thumbnails there are not videos but links to the videos:
[http://ubuntuforums.org/showthread.php?t=486359](http://ubuntuforums.org/showthread.php?t=486359)

---

