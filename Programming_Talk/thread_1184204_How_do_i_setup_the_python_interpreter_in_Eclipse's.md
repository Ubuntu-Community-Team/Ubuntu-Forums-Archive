---
title: "How do i setup the python interpreter in Eclipse's - pydev"
date: 2009-06-10
forum: Programming Talk
---

### Post by xZachtmx on 2009-06-10
Ok i got pydev installed but when i create a new pydev project it asks me to configure a python interpreter... when i press auto config... it gives me an error of some sort. so when i try to manually create one i named it but where is the interpreter located on ubuntu jaunty jackalope?

---

### Post by Ann.A on 2009-06-11
Go to windows > Preferences.  Find Pydev on the left hand side and select Interpreter - Python.  Click the New button on the right hand side and pick your python version, usually installed to /usr/bin/python<version #>  

It should load several python libraries and populate the PYTHONPATH.  Click OK then go to run configurations to set up a project to run python.

---

