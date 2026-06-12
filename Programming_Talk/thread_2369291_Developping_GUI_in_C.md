---
title: "Developping GUI in C"
date: 2017-08-21
forum: Programming Talk
---

### Post by bask185 on 2017-08-21
For my work I spent a lot of work in building a GUI app in Qt. Now I am doing the Exact same in C# using visual studio and I really do not like C#. However a while ago when I was working with my raspberry. I had a C program which I could compile using make and make-install. That program opened a window with a few buttons.

This got me thinking. Qt costs money for what we want and C# is an abbomination of a programming language. So the cheapest thing to do would be writing a program in whatever editor, compiling it with the gcc compiler and start selling. But I have 3 questions about this. The end goal is to sell machines with a working GUI application, a binary.

1. Do we have to deal with Licences? Can I just make a binary, copy it on a machine and sell that machine _legally_ _without releasing the source code_?  
2. The GUI has some advanced features such as a webbrowser which displays an HTML and a few certain graphical objects like a graph and such. Can this be realized with a plain C program?
3. What is a good website with information about this object?

---

### Post by TheFu on 2017-08-21
1. Yes, you **MUST** deal with licenses, especially if you are selling anything.
You will need to avoid the GPL license libraries/code. 
[http://www.zdnet.com/article/no-gpl-apps-for-apples-app-store/](http://www.zdnet.com/article/no-gpl-apps-for-apples-app-store/)
[https://mikrotik.com/downloadterms.html](https://mikrotik.com/downloadterms.html) - requiring a wire transfer of $45 to get something they should have available on their website, for $0, is slimy, IMHO.  Linking to the source of their files, but not their files isn't bad, but it doesn't show how everything is integrated either.

2. C can do anything. It just takes time to create the code.

3. [https://www.gnu.org/licenses/gpl-violation.en.html](https://www.gnu.org/licenses/gpl-violation.en.html) - google can find others "comparison of software licenses"

If you create software for sale, you'll need to learn and understand about licensing, copyright, and patents or risk all your work being used in ways you never intended.

---

