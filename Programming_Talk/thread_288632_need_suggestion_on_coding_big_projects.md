---
title: "need suggestion on coding big projects"
date: 2006-10-30
forum: Programming Talk
---

### Post by pranith on 2006-10-30
hi,
   I am a computer science student. Recently I am facing lots of problems completing big coding projects. I mean I am good at programming, developing algorithms but when it comes to doing single member project which is over 3000 lines, lot of directories many classes hell lot of dependencies  etc... I am failing to complete them in time I dont know how to handle this problem ... could u give any suggestions how to handle big coding projects....
thanks in anticipation
pranith

---

### Post by ghostdog74 on 2006-10-30
you can give Python a shot for the choosing of programming language. Its good for big projects.

---

### Post by Xkutzy on 2006-10-30
Sorry, but there is no magic bullet for this one. As coding projects get larger, they get more complex and harder to do. This is where good programming practice comes to your aid. As projects get bigger, you will have to spend more time on your design. Don't just jump in and start coding. Break the job down into smaller components. Code these and then most important test each component works as designed. If your design is right then hopefully these will be reusable in other projects saving you time later. Object oriented languages often help here but code re-use is possible for any language. Document your code thoroughly, it makes it easier to test and debug and to re-use it in later later projects. Use good descriptive variable names. It makes the code much easier to read and understand.

These approaches have helped me over the years. Good luck!

---

### Post by pranith on 2006-10-30
Thanks Xkutzy i will surely try that

---

### Post by Tomosaur on 2006-10-30
Don't reinvent the wheel. There are lots of sites which provide code for common (and sometimes not-so-common) functions, it may be worth your while doing a Google search.

As Xkutzy said: plan. Design your project and decide what NEEDS to be done and what is DESIRABLE. There's a big difference. Get all of the absolutely necessary stuff out of the way before you go adding bells and whistles, because you'll get caught up on a particular part which doesn't REALLY need to be so fancy. Analyse one bit of the requirements at a time. Break them up into individual operations, then code those and stitch them together.

You may want to take a look at [ASML](http://research.microsoft.com/foundations/AsmL/). At the moment it looks like the only available compilers are direct from Microsoft, but it really is a useful language. It is quite different from 'ordinary' languages, but also shares a lot of things. The biggest difference is that it works via 'steps'. Variables are not altered until the end of each step, meaning you are forced to think very secifically about how methods and such are implemented. The benefits for me weren't immediately obvious, but now I do tend to think a lot more about the design stage. I reccommend you look into it (but if you're having trouble with time-management, perhaps not :P)

---

### Post by nimrod_abing on 2006-10-30
You may also find it useful to use an SCM or version control software. Choose from either CVS, SVN, Monotone, Darcs, Aegis, GnuArch or BazaarNG. An SCM not only allows you to keep track of changes to your source code (and go back to old versions if necessary) but, configured properly, it also helps you ensure that your changes do not cause your builds to break. Coupled with test-driven design and development an SCM becomes a powerful QA tool.

My personal preference is darcs. It allows me to move changes between Windows, Linux, or Unix hosted repositories without any problems. It also has a smarter way of handling merges and conflicts especially between out-of-band/asynchronous modifications. GnuArch or Bazaar is good too especially when performing so-called "star merges", useful when working with large teams of developers. But since you're the only developer working on your project, I guess CVS or SVN should also work nicely for you.

---

### Post by pranith on 2006-10-31
thanks Tomosaur,nimrod_abing

---

