---
title: "Restarting Python script"
date: 2009-06-14
forum: Programming Talk
---

### Post by Nevon on 2009-06-14
I'm part of a group developing a FOSS, cross-platform, point-and-click adventure game in Python, using SDL through Pygame. 

I'm currently looking to hack together a sort of pause menu that allows you to quit or start a new game. Quitting isn't very hard, but starting a new game has proved harder than I first thought it would be. All you would need to do is restart the program. But so far I haven't really found a very good way to do this. Any ideas?

If you're interested in the project, you can check out [my blog](http://www.blastfromthepast.se/blabbermouth/), or have a look at [the source code](http://github.com/kallepersson/subterranean/tree/) itself.

---

### Post by Tony Flury on 2009-06-16
If you have built your application as a set of classes - then restarting the Application is simply a case of deleting the Application object and recreating it.

if you have your engine and your gui as seperate classes then this should restart the game = without restarting the gui.

---

### Post by Nevon on 2009-06-17
> **Tony Flury said:**
> If you have built your application as a set of classes - then restarting the Application is simply a case of deleting the Application object and recreating it.

if you have your engine and your gui as seperate classes then this should restart the game = without restarting the gui.

Wow! Why didn't I think of that? :oops:

---

