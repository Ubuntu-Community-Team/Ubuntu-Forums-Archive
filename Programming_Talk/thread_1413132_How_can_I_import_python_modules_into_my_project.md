---
title: "How can I import python modules into my project"
date: 2010-02-22
forum: Programming Talk
---

### Post by hoboy on 2010-02-22
How do I import python modules into my project ?
in java I can do this by adding the jar files that api is in in the project path.

For example.
They are some modules in MySQL-python-1.2.3c1.tar.gz that I want to use in my project, how can I do this ?

---

### Post by hoboy on 2010-02-22
Problem solved.

---

### Post by Imaginary-r4e- on 2010-02-22
How about sharing how you solved the problem so that others who have the same problem can take use of this thread?

---

### Post by nvteighen on 2010-02-22
Well, because it actually is that trivial that you should know it from any Python tutorial or minimum experience working with it.

To import a Python module you use the **import** statement, knowing that it will search Python's system-wide modules and the directory where the importing code resides... There are ways to change this behaivor, but usually you either use a module that's available in the distribution repositories (you could have gotten python-mysqldb simply from APT) or you place it inside your project's folder... and redistribute it if the module's license allows you to.

That's all of it...

---

### Post by hoboy on 2010-02-22
> **nvteighen said:**
> Well, because it actually is that trivial that I can't think why he even asked the question.

To import a Python module you use the **import** statement, knowing that it will search Python's system-wide modules and the directory where the importing code resides... There are ways to change this behaivor, but usually you either use a module that's available in the distribution repositories (you could have gotten python-mysqldb simply from APT) or you place it inside your project's folder... and redistribute it if the module's license allows you to.

That's all of it...

Well import was the wrong word, I didn't know that there was something called PYTHONPATH, this was the source cause of my miseries.
the modules I want to have access to in my code should be visible to PYTHONPATH.

---

