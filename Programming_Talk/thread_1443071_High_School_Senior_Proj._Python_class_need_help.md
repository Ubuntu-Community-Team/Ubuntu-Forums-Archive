---
title: "High School Senior Proj. Python class need help"
date: 2010-03-30
forum: Programming Talk
---

### Post by Eremis on 2010-03-30
Hi everybody, 

I am learning Python for my senior project. (My topic is "Open Source vs Proprietary Software in Schools")... I know java, so programming is not a new thing for me.

I am working on a program that will help my teacher with the monthly food drive. So basically I have 2 classes: The GUI class where I use wxPython called "MannaHelper.py" and a class that represents each school class that turns in food "schoolClass".

Now for my problem:

When i import and use my schoolClass inside my MannaHelper class I get the following error:

```

Traceback (most recent call last):
  File "C:\Users\******\Documents\NetBeansProjects\MannaHelper\src\test.py", line 3, in <module>
    c1 = schoolClass('Java 1a -- Mr. Wilson', 20)
TypeError: 'module' object is not callable

```

I will include the two files below, but instead of the whole gui, i will show u a tester file where i create a new "schoolClass", and the same error occurs.

I will greatly appreciate your help! Thanks! 


schoolClass.py ---------------------->

```

#!/usr/bin/env python

#   By: ****** *****            An application that organizes the annual manna food drive
#
#   schoolClass.py              3 March, 2010

class schoolClass:

    # Constructor -----------------------------
    def __init__(self, className, numStudents):

        self.className = className
        self.numStudents = numStudents

        self.firstReturn = 0
        self.secondReturn = 0
        self.thirdReturn = 0
        self.fourthReturn = 0
        self.fifthReturn = 0
    # -----------------------------------------



    # Functions -------------------------------
    def getRatio(self):

        totalPounds = (self.firstReturn + self.secondReturn +
        self.thirdReturn + self.fourthReturn + self.fifthReturn)

        if totalPounds == 0:
            ratio = 0
        else:
            ratio = totalPounds / self.numStudents

        return ratio

    def __str__(self):

        returnStr = ""
        numLine1 = 40 - len(self.className)

        returnStr += ('' + str(self.className) + (' ' * numLine1) + str(self.numStudents) +
        (' ' * 10) + str(self.getRatio()) +' lb/student')

        return returnStr
    # ------------------------------------------


# Tester ---------------------------------------
if __name__ == '__main__':
    
    # Everything works here, I get an error only when I import...
    class1 = schoolClass("Java 1A -- Mr. Wilson", 20)
    class2 = schoolClass("French I -- Ms. Castevens", 14)
    class3 = schoolClass("Algebra II -- Ms. Kuster", 21)
    class4 = schoolClass("English -- Ms. Love", 29)

    class1.firstReturn = 6.2
    class1.secondReturn = 4
    class1.thirdReturn = 3.6

    print class1
    print
    print class2
    print
    print class3
    print
    print class4


```


test.py ------------------------->

```

import schoolClass

c1 = schoolClass('Java 1a -- Mr. Wilson', 20)

print c1


```



P.S.

Does anybody know a good way to convert my project into a single .exe? (school uses windows)... I tried py2exe, but failed because I cant get it to work with wx.Python....

Thanks!

---

### Post by Bachstelze on 2010-03-30
Hi,

the error message says: "module object is not callable". Indeed, when you do

```
import schoolClass
```

Python binds the [font=monospace]schoolClass[/font] variable to a module object (the module contained in schoolClass.py). In order to access members of this module, like your schoolClass class, you must use the normal dot notation (object.member), which gives:

```
c1 = schoolClass.schoolClass('Java 1a -- Mr. Wilson', 20)
```

---

### Post by Eremis on 2010-03-30
Thank you so much! 

It fixed it...

Also do you know a way how I can distribute this app to a windows user without making him/her install python on their machine?

---

### Post by Bachstelze on 2010-03-30
> **Eremis said:**
> 
Also do you know a way how I can distribute this app to a windows user without making him/her install python on their machine?

Nope, sorry. py2exe is the only one I know of, and apparently it doesn't work for you...

---

### Post by Eremis on 2010-03-30
ok, thanks

---

### Post by lavinog on 2010-03-30
You could try what this person did:
[http://ubuntuforums.org/showpost.php?p=5473160&postcount=7](http://ubuntuforums.org/showpost.php?p=5473160&postcount=7)

---

### Post by Eremis on 2010-03-31
Hum... this sounds interesting, but do you know what files are not necessary in python?
(So I dont delete the ones i need)

---

