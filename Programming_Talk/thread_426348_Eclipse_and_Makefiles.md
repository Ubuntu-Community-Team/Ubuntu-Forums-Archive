---
title: "Eclipse and Makefiles"
date: 2007-04-28
forum: Programming Talk
---

### Post by Daishim on 2007-04-28
I'm fairly new to the Eclipse IDE (using the CDT plugin for C and C++ development), and I'm having some trouble getting Eclipse to handle the generation of makefiles.  From what I understand by twiddling with it a little is that it can/should automatically generate makefiles based upon the source files you add to a project, however, I can't quite seem to get this to work out of the box.  If a place a makefile (hand written) in the project directory, Eclipse will use it to build the project just fine.  Is there something that I'm overlooking to get Eclipse to do this for me?

Can anyone point me in the right direction?

Thanks.

---

### Post by jespdj on 2007-04-28
When you create a new C or C++ project in Eclipse, you can choose to make a Managed Make or Standard Make project. Choose Managed Make Project if you want Eclipse to automatically generate makefiles for you. Then use things like File / New / Source File etc. to add source files to your project.

---

### Post by Daishim on 2007-04-28
Thanks a bunch.  When I saw it the first time I thought it said managed C++ instead of managed make C++.

---

### Post by alienjon on 2008-12-27
I know you aren't really asking this in your original question, but just to put it out there, in case you need to know later (as I just did) managed make projects mean the Eclipse will automatically creature/update your project's make files, but if you need those make files later, you can find them in the release directory for the current build.

For example, if you just built a Debug version of your program, its make file is in Debug/

(For some reason, Eclipse doesn't easily advertise this fact)

---

### Post by vishalag on 2009-05-19
Thanks a lot man...
Did not occur to me since last 6 hours. This needs to be advertised. It was not at all obvious. 
Again I will summarise the problem which occured which this post solved.

The problem was that eclipse was not able to generate the make file on its own. It would run the program very well given the makefile. So you might be stuck only thinking that what the hell is the problem that it does not generate a makefile.

---

