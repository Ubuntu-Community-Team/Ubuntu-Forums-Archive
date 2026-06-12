---
title: "Introduction to open source programming"
date: 2007-05-29
forum: Programming Talk
---

### Post by durus on 2007-05-29
Hi I am pretty new to linux and open source, i have been trying linux some times but never sticked to it. My main rezone to use linux is that i want to learn how to program "real" applications that someone may use in the future.

I do know how to program c/c++, php, and some python, and i want  to learn little about how open source projects works, can you send me a link to a c++ project that is not to big, and tell me how the cvn works. I mean how to use it and how people that aren't in the team contributes with bug fixes and things like that.

For me it's important that it's some basic c++ project so that there isn't to much to do before i understands the basics of how this things works. I as a person do have difficulties to take the first step in learning things and do usually need help at the beginning but then when i now the basics the rest usually do come automatically.

I do know that this is proboly some basic questions that you think that i should know if i really want to make applications, I am therefore glad i you can send me some links to tutorials about this basic things if you think that i have to read them before 

Thanks

---

### Post by ankursethi on 2007-05-29
CVS tutorials : [http://www.google.co.in/search?q=cvs+tutorial&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.in/search?q=cvs+tutorial&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
SVN tutorials : [http://www.google.co.in/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=pay&q=svn+tutorial&btnG=Search&meta=](http://www.google.co.in/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=pay&q=svn+tutorial&btnG=Search&meta=)

Both are version control systems, and both are widely used by FOSS projects. I think you should see what your project of choice uses and learn that.

I have no idea about how people not in the team contribute patches, but I think they use "diff" and "patch" to do their work. Use Google to find out more. Also learn "make" to manage large projects.

There are ample projects on Freshmeat.net and SourceForge.net. Take your pick. or start your own.

---

### Post by Blender on 2007-05-29
You will have to learn GNU Autotools, too:
[http://sourceware.org/autobook/]("http://sourceware.org/autobook/")

In addition to what ankursethi said, probably the best way to learn SVN is to read the SVN book:
[http://svnbook.red-bean.com/]("http://svnbook.red-bean.com/")

---

### Post by cferthorney on 2007-05-29
> **Blender said:**
> You will have to learn GNU Autotools, too:
[http://sourceware.org/autobook/]("http://sourceware.org/autobook/")

In addition to what ankursethi said, probably the best way to learn SVN is to read the SVN book:
[http://svnbook.red-bean.com/]("http://svnbook.red-bean.com/")

Thanks for the GNU Auto tools link - really helpful :-)  With regards the SVN/CVS debate - you need to learn both.  KDE for instance uses Subversion now, Bugzilla uses CVS.  Projects big and small use a mixture.  There is no one standard sadly.  So much to learn so little time...

---

### Post by harun on 2007-05-29
I found this walk through of autotools to be really helpful while I was learning:

[http://www.st-andrews.ac.uk/~iam/docs/tutorial.html#SEC7](http://www.st-andrews.ac.uk/~iam/docs/tutorial.html#SEC7)

---

### Post by durus on 2007-06-02
Thanks for all links, i haven't time to check them all but i have reed about SVN. I made a google code project were i tried some commands, it's really great. I have only programmed apps for my self, but i can't count how many times i have made changes that i wanted to undo but couldn't before.
Now i will start read about GNU autotools. What do you think about CVS, do need to learn it or is it enough to learn about SVN, as i understood it, SVN is much better then CVS and people starting new projects will use SVN. 

Is there more things that you think that i should  read about if i want to do c++ projects ?
Do you also know any free SVN server that is private, so that other people can't get access to the source code ? I would like to start use SVN for my school projects and as we do get grades I do not want other people to able to copy the codes that i have to hand in to our teacher.

---

### Post by Blender on 2007-06-02
> **durus said:**
> Thanks for all links, i haven't time to check them all but i have reed about SVN. I made a google code project were i tried some commands, it's really great. I have only programmed apps for my self, but i can't count how many times i have made changes that i wanted to undo but couldn't before.
Now i will start read about GNU autotools. What do you think about CVS, do need to learn it or is it enough to learn about SVN, as i understood it, SVN is much better then CVS and people starting new projects will use SVN. 

Is there more things that you think that i should  read about if i want to do c++ projects ?
Do you also know any free SVN server that is private, so that other people can't get access to the source code ? I would like to start use SVN for my school projects and as we do get grades I do not want other people to able to copy the codes that i have to hand in to our teacher.

Regarding CVS, as far as you don't use it on a daily basis, you only need very basic knowledge (checkout, update, commit).

There are other (simpler) build systems, e.g. CMake and SCons, besides Autotools.

If you're the only user of your school projects, then you can use SVN on your local computer, without running a server.
Consult the SVN book (basically, you access the repo with a **file://** URL).

---

