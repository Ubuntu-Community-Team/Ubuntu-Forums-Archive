---
title: "[Help] ADA-GPS aggregate project setup"
date: 2020-06-13
forum: Programming Talk
---

### Post by Lelorrain on 2020-06-13
I am trying to create an aggregate project definition to include all the test project that I have already created while learning ADA.but when I start GPS with the Learning.ADA.gpr project, I get the message:

```

Welcome to GPS 6.1.2016 (20160515) hosted on x86_64-linux-gnu)
the GNAT Programming Studio
(c) 2001-2015 AdaCore

[2020-06-13 19:36:35] /home/rene/Programming/Projects/Ada/learning_ada.gpr:2:28: warning: file "tests/test01.grp" not found
[2020-06-13 19:36:35] there are no non-aggregate projects[2020-06-13 19:36:35] /home/rene/Programming/Projects/Ada/learning_ada.gpr:2:28: warning: file "tests/test01.grp" not found

```

My aggregate specification is:

```

aggregate project learning_ada is
    for Project_Files use ("tests/test01.grp", "tests/test02.grp") ;
end Learning_Ada;

```

My directory structure is as follow:

```

  /Ada
    |----> /tests
    |        |----> /src
    |        |        |----> test01.adb
    |        |        |----> test02.adb
    |        |
    |        |----> /obj
    |        |----> /bin
    |        |
    |        |----->test01.gpr
    |        |----->test02.gpr
    |
    |----> learning_ada.gpr

```

---

### Post by TheFu on 2020-06-13
This is the first post that I've ever seen here about ada.  I'd suggest that other forums would likely be more fruitful in getting help.  When ada was very young, my employer at the time did encourage all the programmers in my group to learn it - we were going GN&C coding for spacecraft.  A few of the team did, but not me.

> warning: file "tests/test01.grp" not found
tells me that the CWD isn't Ada.  BTW, be very careful using leading / characters.  I suspect it is a problem with understanding the difference between a relative path and an absolute path.  By definition, all paths that begin with 1 or more / characters are absolute while any path that does not is relative to the CWD.

The output from **tree -F** is usually the format for showing directory strictures and files. If you only want to show directories, use **tree -dF**.  This places trailing / characters AFTER directories, not before to address the relative vs absolute path issue.

---

### Post by Lelorrain on 2020-06-13
The wpd for GPS is "~/Programming/Ada", that's the one shown on the Tree graph.

---

### Post by spjackson on 2020-06-14
Your tree structure mentions .gpr files. Your use statement refers to .grp files. gpr != grp.

---

### Post by TheFu on 2020-06-15
**wpd** probably should be **pwd** too?  With computers, details matter. With programming, details have to be perfect.

---

