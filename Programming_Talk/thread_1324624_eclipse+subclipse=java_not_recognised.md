---
title: "eclipse+subclipse=java not recognised?"
date: 2009-11-12
forum: Programming Talk
---

### Post by apmcd47 on 2009-11-12
Here is my problem: I've started using Java from within ([www.yoxos.com](www.yoxos.com) - and click through the flying car) Eclipse on a new (to me) project using a subversion repository. I've installed Subclipse from the yoxos repository and I can attach to the SVN repostory and checkout packages. However I cannot for the life of me figure out how to tell Eclipse that this is a java package and it should compile and run/debug my programs.

I've looked at several web-based Eclipse/Subclipse tutorials and none of them seem to move beyond "check out your project and that's it". Well, unless I'm missing something that isn't it! I've followed the instructions to use the wizard when checking out and have been rewarded with a file-tree list (in the java view) with an empty package folder and my source files under the trunk folder. What should I do next?

Or is it a case that you can only use Eclipse with SVN repositories created with Eclipse?

Andrew

---

### Post by apmcd47 on 2009-11-13
This is the page that gave the best advice so far, but not good enough for me: ([http://www.bedework.org/trac/bedework/wiki/DevDocs/EclipseIDE](http://www.bedework.org/trac/bedework/wiki/DevDocs/EclipseIDE))

> **Checkout project from SVN, overwriting quickstart files** 

- In eclipse, Right-click on the SVN project in the repository exploring perspective and choose “checkout…” Choose “checkout as a project configured using the New Project Wizard”. Click Finish. Choose Java > Java Project in the tree view. Click Next. For project name use “bedework-3.4.1”. Choose “create project from existing source” radio button. Browse to “F:/bedework-3.4.1/bedework” (create the directory if it doesn’t exist). Click Finish. 

I find it hard to believe that it should be so difficult to do such a simple thing as check out a project, edit/test/debug the project and then commit it again!

Andrew

---

