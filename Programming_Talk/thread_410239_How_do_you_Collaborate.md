---
title: "How do you Collaborate?"
date: 2007-04-15
forum: Programming Talk
---

### Post by Bicx on 2007-04-15
I'm about to finish my first software design class (not so much programming, more layout, diagrams, and planning), and the biggest problem I've had as leader of my group (other than laziness of various team members) is forming a system where we can easily collaborate on a project. Right now, we're just sending new copies of our project over e-mail, but this is a poor solution. If someone doesn't answer their e-mail or send me a new copy of the source code, I don't know whether to pick up the slack in one area or start developing another section.

So my question to all you experienced software developers is this: How can I efficiently bring my team together to collaborate on a software project in a streamlined manner? What tools might I need?

Any advice would be gladly accepted.

---

### Post by spin2cool on 2007-04-15
1) assign responsibilities.  Don't jump all over, looking for holes in the code.  Modularize the code, and assign each person a section.  You handle the db calls, I'll work on the GUI, etc.  

2) In order to do this well, you'll need a really good set of specifications.  If your code will be calling someone else's functions, you should have a plan ahead of time that tells you exactly what you'll be passing to them, and exactly what you expect to get back.

3) get some versioning software - CVS, SVN, Perforce, whatever.  This will allow members of the group to check in and out files from a central location, rather than having multiple copies floating around via email.

---

### Post by shawnhcorey on 2007-04-15
4) Create module interface documents that spell out in detail what information is being transfered. When everyone knows exactly what their code has to do to be integrated with the others, things will go a lot smoother.

---

### Post by pmasiar on 2007-04-15
Free opensource TRAC [http://trac.edgewall.org/](http://trac.edgewall.org/) is great tool integrating subversion repository, code viewer (colorizing changes in source), bug tracker, and wiki for documentation.

Wiki is great way to distribute documentation, and TRAC has special markup linking to bugs and changesets (so in 1 click you can go from wiki docs to committed source code with hightligted changes). SVN = subversion allows also branches and file renames - don't use CVS if you can have SVN for same price :-)

---

