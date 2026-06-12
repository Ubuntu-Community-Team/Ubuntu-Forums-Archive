---
title: "Questions about going from C# and WinForms to other languages/GUIs"
date: 2011-06-28
forum: Programming Talk
---

### Post by Zeikcied on 2011-06-28
Couldn't come up with a shorter subject line to convey what it is I want to ask.

I know C#.NET, though I wouldn't consider myself an advanced programmer.  Maybe intermediate.  I've been wanting to branch out into C++ and/or Java, but I'm lost as to where to find tutorials or references.  Some pages I've seen on C++ teach the basics at the start, which leaves me kind of bored.  It doesn't help that I have motivation and attention span issues...

I've also looked into JavaScript and HTML5.  See, I have a game I wrote in C# for a class in 2005.  It uses WinForms and GDI+.  It's still in an early stage, as I haven't worked on it much since that class.  I switched to Linux in 2006, so that's been the main issue.  MonoDevelop doesn't seem to have a WinForms designer, so it limits me on how much I can alter the game.

I also use KDE, and there doesn't seem to be an optimal Qt binding for Mono.  Not that I would know how to use that.  I have no idea where to start learning GTK or QT or any of the other graphics libraries.  WinForms is all I know.  I don't know what the differences are.

I guess, in the end, the only reason I'm even considering C++ is because of the lack of good Qt support in Mono.  If I could somehow manage to port my C# game to Qt without having to change languages, then I'd be happy.  But I don't know how to port from WinForms to Qt, and I don't know if any of the bindings are up to par.

I would still like to learn Java and JavaScript/HTML5.  I started going through the W3Schools JavaScript tutorial, and it seems to be okay.  I get most of the concepts.  The only sticking point is how to take a two-dimensional array and figure out how to implement that in JavaScript without having a giant mess.

Sorry for my rambling, nonsensical post.  I hope someone can make sense of it and help me out.

---

### Post by doas777 on 2011-06-28
I'd head toward java for now, as your UIs cross all the boundraries you mention. for games you are going to want to look at opengl, but games are out of my element, so I can't speak authoritatively on that.

in terms of java, my advice, is to download eclipse, and just start trying to write a java program. google is the best book there is, if all you have are syntax questions. if you are decent with C# (or even VB) learning java on your own won;t be too hard. once you can code, picking up a new langague usually isn't too hard, especially when they are as closely related as .net and java.

IMO, javascript is an ugly langague, and I've never found satisfactory tools for working with it. I'm one of those .net devs you hear about being dismayed that MS is heading toward HTML5, since its the latest greatest buzz platform. Lately I've made it a career goal to learn me some android. time to get some mobile under my belt.

---

### Post by directhex on 2011-06-29
There's a Qt binding for Mono, but it's largely undocumented - you would need to feel your way through it. [libqyoto-cil-dev](apt:libqyoto-cil-dev) is likely the right thing to install.

---

### Post by Zeikcied on 2011-06-29
> **doas777 said:**
> I'd head toward java for now, as your UIs cross all the boundraries you mention. for games you are going to want to look at opengl, but games are out of my element, so I can't speak authoritatively on that.

The game I have is a simple 2D, turn-based game wrote in GDI+.  I may be wrong, but I don't think OpenGL would be necessary.  Some of my favorite games in the Kgames package (KNetWalk, Klickety, and KPatience) have smooth and simple graphics without using OpenGL.  So I'm pretty sure I'll be fine without it.

Thanks for the other advice, though.  I guess I will look more into Java than C++.

The only reason I'm looking into Javascript and HTML5 is because I thought it might be neat to have a web-based version of my game.  Even though it's just a clone of a PopCap game (Mummy Maze if you're wondering) I thought it would be fun to try.  Like I said, I'm not sure how to get around the lack of multi-dimensional arrays, but I guess I'll come up with something.  Even if I have to use an array of arrays (which I just think would be needlessly large, being an array of 25 arrays each with 25 entries).

And I know about Qyoto, but the lack of documentation really makes me afraid to try it.  I'm holding out hope that there will be some documentation eventually.  As someone who has never used Qt, going into a Qt binding without any documentation doesn't sound like a good idea.

Anyway, one reason I've wanted to learn C++ is because a lot of open source programs seem to use it.  But I don't think I'd ever have anything to contribute, so other than being able to understand the code, there doesn't seem to be much reason for me to actually try. *shrug*

---

