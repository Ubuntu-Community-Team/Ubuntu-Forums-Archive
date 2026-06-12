---
title: "Can someone give some detailed Jython instructions ?"
date: 2011-02-01
forum: Programming Talk
---

### Post by beligor on 2011-02-01
I want to call a python script from jython, get the returned values and then pass them to a java method. The first part works easily, my problem is in importing the java class that contains the method I want to call. I have   from projectname.src import ClassName but that will give
 ImportError: No module named projectname.src
I also tried importing from projectname and got the same. What is the path I should set ? (the project's workspace is the same as the folder in which the Jython script is). 
And also, how should I initialize the java class ? 
Thanks

---

