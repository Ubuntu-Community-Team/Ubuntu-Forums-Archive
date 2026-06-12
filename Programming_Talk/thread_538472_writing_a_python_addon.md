---
title: "writing a python addon"
date: 2007-08-30
forum: Programming Talk
---

### Post by aquavitae on 2007-08-30
I'm sure this is really simple, but I can't find anything on google about it.  I'm writing an app in python which I intend to compile to binary.  However, I want to use python scripting within it (rather like blender does).  Obviously, within a script I will need something like "import MyApp" to get access to the functions and classes in my app.  My question is, will it work using just "import MyApp" once I've compiled myapp, or do I need to do anything special to make it available.  Also, what would be the best way to run a script from MyApp - should I use exec?  And do I need to install python on the target machine or will it be embedded in my app?

---

### Post by nanotube on 2007-08-30
> **aquavitae said:**
> I'm sure this is really simple, but I can't find anything on google about it.  I'm writing an app in python which I intend to compile to binary.  However, I want to use python scripting within it (rather like blender does).  Obviously, within a script I will need something like "import MyApp" to get access to the functions and classes in my app.  My question is, will it work using just "import MyApp" once I've compiled myapp, or do I need to do anything special to make it available.  Also, what would be the best way to run a script from MyApp - should I use exec?  And do I need to install python on the target machine or will it be embedded in my app?

about your last question: if you are compiling to binary with py2exe, e.g., then a python interpreter will be included, so you don't need to install python to be able to run the scripts from withit MyApp.

---

### Post by aquavitae on 2007-08-31
Thanks.  That implies, then, that the classes in my app will be available throught the "built in" interpreter.  I think...

---

