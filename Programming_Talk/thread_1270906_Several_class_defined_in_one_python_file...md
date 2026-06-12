---
title: "Several class defined in one python file.."
date: 2009-09-20
forum: Programming Talk
---

### Post by hoboy on 2009-09-20
In java each class has its own file, like test.java.
In python is this the case ?
can I defined several class in one file ?
test.py can contains 2,3,4 deferent class ?
how to I acccess the method of these class ?

---

### Post by matmatmat on 2009-09-20
There can be any number of classes in a file.
To use another files callses do:
```

import file_name

```

---

### Post by The Cog on 2009-09-21
You can define any number of classesin one file. Imagine you have a file called myUtils.py with several utility classes in it. You instantiate those classes like this:
> import myUutils
fw = myUutils.FancyWidget()
fw.doSomethingNeat()

---

### Post by alzaf on 2009-09-21
Something worth considering is the use of packages. This isn't necessary for small programs that have a few classes but is useful when creating larger programs to group together similar types of classes for ease of reference. An example could be a program that has classes that are input-output, music and video based. 

To do this you would create folders in the place where you store your program and. To use the above example, you would have folders called:

io
music
video

You would store the files containing the classes in each folder, ie all the input-output based files would go in io folder, music based files would go into music folder and video based files would go in video folder. In each folder, a file named __init__.py needs to be inserted. This can be blank but can also be populated with data that will be global to package like the __init__ function that can be used in classes. 

To call the classes you should put the following code in your program (there is a files called class1.py in the io folder)

> 
import io.class1

x=io.class()
x.do_somthing()


---

### Post by hoboy on 2009-09-22
> **alzaf said:**
> Something worth considering is the use of packages. This isn't necessary for small programs that have a few classes but is useful when creating larger programs to group together similar types of classes for ease of reference. An example could be a program that has classes that are input-output, music and video based. 

To do this you would create folders in the place where you store your program and. To use the above example, you would have folders called:

io
music
video

You would store the files containing the classes in each folder, ie all the input-output based files would go in io folder, music based files would go into music folder and video based files would go in video folder. In each folder, a file named __init__.py needs to be inserted. This can be blank but can also be populated with data that will be global to package like the __init__ function that can be used in classes. 

To call the classes you should put the following code in your program (there is a files called class1.py in the io folder)

Thanks.. this answer my question.

---

### Post by nvteighen on 2009-09-22
But, sometimes a module could export more than one class... I think the one class per file seems to be a Javaism, which is not per se bad, but just sticking to a certain model that's needed for Java because how it works... and needlessly importing that idea into Python.

Python packages are great, but they may be overkill... If you happen to be writing a certain library whose classes are all very related in use, you may consider using a single file... or not. Sometimes the criterion seems to be how the application will be deployed and personal preference.

At the end, in the case of Python, modules, classes and packages behaive almost exactly the same...

---

