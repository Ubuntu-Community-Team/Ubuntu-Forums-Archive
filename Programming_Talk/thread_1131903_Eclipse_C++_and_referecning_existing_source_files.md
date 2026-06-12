---
title: "Eclipse C++ and referecning existing source files"
date: 2009-04-21
forum: Programming Talk
---

### Post by rabinnh on 2009-04-21
It's easy to import existing source files into an Eclipse project, but a much more common situation is to include files that are common to a number of projects.  For the life of me, I can't figure out how to include source files in my project without importing them and therefore making copies.

Can anyone help?

---

### Post by dwhitney67 on 2009-04-21
I use Eclipse at the office, and we have no such trouble.  Maybe you are not organizing your files on your file-system properly.

Common header files (and source code) should be in a separate project.  Another project can be setup to reference these.

---

### Post by rabinnh on 2009-04-21
Really?  So to include an existing arbitrary cpp and h file I have to create a whole new project and include it?

I may look for another tool.  We have a "common" area with many miscellaneous useful classes that we use in various combinations.  That's just too much of a pain for us.

And please don't ask about creating a library.  We have reasons for working the way we do.

Thanks for the reply.

---

