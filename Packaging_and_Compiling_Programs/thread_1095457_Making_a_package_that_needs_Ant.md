---
title: "Making a package that needs Ant"
date: 2009-03-13
forum: Packaging and Compiling Programs
---

### Post by WaffleCode on 2009-03-13
Hello there! I am a newcomer to development, and would like to help out the Ubuntu Project. I took on a request to package the game [TripleA]("http://triplea.sourceforge.net") (Awesome game, by the way -- I would definitely recommend that you try it out) for Ubuntu users. This is my first package, and as such I'm not very familiar with the packaging tools. 

[This]("https://wiki.ubuntu.com/PackagingGuide/Complete") guide seems like it would work, but unfortunately the TripleA source code uses Ant to compile, not Make. How do I package something using Ant?

---

### Post by Vadi on 2009-03-13
I believe you would edit *debian/rules* file to use ant instead of make.

And thanks for taking up packaging! ubuntu is desperately short on them.

---

