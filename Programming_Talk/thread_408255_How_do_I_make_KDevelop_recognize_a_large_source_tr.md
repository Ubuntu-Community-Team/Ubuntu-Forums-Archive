---
title: "How do I make KDevelop recognize a large source tree?"
date: 2007-04-13
forum: Programming Talk
---

### Post by TwoBit on 2007-04-13
I have a large source code tree that comes from a Windows project and I want to get it running on Linux with KDevelop. There are many source files in many directories, but not every .cpp file in any given directory can be compiled (i.e. can't just compile *.cpp). I want to have a single KDevelop project which references all source code and headers. I can't find how to do this, though I figure it must be possible because pretty much every IDE on every other platform supports this.

Surely there must be a way to do this, as KDevelop seems to be a well-regarded IDE.

Thanks.

---

### Post by IronAvatar on 2007-04-13
I've been trying the same thing as you; using an existing code base that had been written under windows and needs to stay in it's own folder outside of my kDevelop project.  I tried looking on the kDevelop web site, and got as far as the documentation explaining the use of sub-projects.

But the documentation is very poor, and from what I can tell, you still have to copy your sources over to your kDevelop project source folder; which is just a big no -o for me.  Luckily, I'm not really needing to write KDE apps at the moment, so I'm just using Code::Blocks which is much more flexable.

I would reccomened using Code::Blocks over kDeveloper, but I've tried getting the basic KDE "hello world" app to build in Code::Blocks only to run into some issues regarding compiler defines etc.

Perhaps the (extremely messy) sollution is to use Code::Blocks to build libraries of your existing source, and just link to them in kDevelop and use custom include paths?

---

