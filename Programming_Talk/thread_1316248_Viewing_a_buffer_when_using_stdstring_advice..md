---
title: "Viewing a buffer when using std::string advice."
date: 2009-11-05
forum: Programming Talk
---

### Post by Swerve1000 on 2009-11-05
I have a task to do about the std::string datatype.

To do the task I need to use the KDevelop IDE and be able to find the size of the buffer being used when performing operations upon strings, but never having used KDevelop before, I'm at a complete loss.

Could anyone be so kind as to give me some direction as how to go about viewing a buffer which is in use? Can it's contents be viewed within a window of the IDE, or would I have to call functions to 'cout' details about the buffer being used?

I'm at a complete loss about this, so any info is really appreciated.

Many many thanks.

---

### Post by dwhitney67 on 2009-11-05
I'm not what KDevelop has to do with this?

If you need the size of an std::string, use the size() (or length()) method.

If you need to examine the size whilst debugging the application, you should be able to call that method as well.  If you want to examine the contents of the data within the string as you are debugging, then printing the _M_dataplus._M_p attribute should suffice.

Btw, you can also call the function data() to get the data stored within a string.

---

