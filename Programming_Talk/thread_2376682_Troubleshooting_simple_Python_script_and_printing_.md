---
title: "Troubleshooting simple Python script and printing class objects"
date: 2017-11-04
forum: Programming Talk
---

### Post by Drone4four on 2017-11-04
I’m learning to read, create, use and manipulate Python classes.

For practice I have begun to create a class tracking user input for a US PassPort application.  In my script I have documented each code segment for readability.  Here it is:

```
#!/usr/bin/env python3

# MIT License
# By Drone4four / Angeles4four and Daniel08 on GitHub

# The purpose of this script is to collect personal US citizen passport information

# General initilization of libraries which I may use down the road:
import random
import os

# Create a new object type called, PassPort:
class PassPort(object):

    # Initilization of special method, right?
    def __init__(self, first_name, middle_name, last_name, gender, YOB, iQ):

        # Universal class object attribute:
        species = 'homo-sapien'

        # Regular class objects:
        self.first_name = first_name
        self.middle_name = middle_name
        self.last_name = last_name
        self.gender = gender
        self.YOB = YOB # (Year of birth)
        self.iQ = iQ # (Inteligence Quotient)

    # Comparing the iQ variable among the entire citizenry:
    def iQcomparison():
        average = int(100)
        genius = int(75)
        if self.iQ < average:
            print(str("The citizen is less smart than average."))
        elif self.iQ > average:
            print(str("The citizen is smarter than average."))
        elif self.iQ <= genius:
            print(str("The citizen is among smartest of Americans."))

# Instance of PassPort:
citizen256032 = PassPort(first_name='Jon', middle_name='Ross', last_name='Dobbs', gender='male', YOB=int(1947), iQ=int(44))

# Prints specific instance to CLI (second format ), right?
print("The citizen's first name is {}. \n The citizen's middle name is {}. \n The citizen's last name is {}. \n The species of the citizen is {}.  \n The gender of the citizen is {}. \n The citizen was born in the year {}. \n And finally, the citizen has an iQ of {}." format(citizen256032.first_name, citizen256032.middle_name, citizen256032.last_name, citizen256032.species, citizen256032.gender, str(citizen256032.YOB), str(citizen256032.iQ)))

# and this iQ, as compared to other citizens, he there is a flippin {iQcomparison()}.")

# Prints specific instance to CLI (first format), right?
# print("The citizen's first name is" + citizen256032.first_name + ".  The citizen's middle name is" + citizen256032.middle_name + ".  The citizen's last name is " + citizen256032.last_name + "The citizen was born in the year " + str(citizen256032.YOB) + ".  And finally, " str(citizen256032.iQ) + ".")

'''
====== TO DO =======
* Prompt user for all his/her citizen information instead of feeding it in the script
* Rename file
* Have print statement print all the information into a flowing plain english sentence
'''

```

In my shell, it throws this output:
```
$ python3 main.py                
  File "main.py", line 44
    print("The citizen's first name is {}. \n The citizen's middle name is {}. \n The citizen's last name is {}. \n The species of the citizen is {}.  \n The gender of the citizen is {}. \n The citizen was born in the year {}. \n And finally, the citizen has an iQ of {}." format(citizen256032.first_name, citizen256032.middle_name, citizen256032.last_name, citizen256032.species, citizen256032.gender, str(citizen256032.YOB), str(citizen256032.iQ)))
        ^
SyntaxError: invalid syntax
$
```

I'm not sure what this shell output is trying to say.  I’ve tried swapping out the str() for int() when referring to the last two class variables. I’ve also tried running the script with neither str() nor int().  Still throws an error. Any one here have an idea as to what is wrong with my program?

[Here is my code on GitHub](https://github.com/Angeles4four/PassPort/blob/master/main.py). I am accepting pull requests.

Thanks for your attention.

---

### Post by kostkon on 2017-11-04
Looks like you were getting a syntax error because you missed a dot before format():
```
print("The citizen's first name is {}. \n The citizen's middle name is {}. \n The citizen's last name is {}. \n The species of the citizen is {}.  \n The gender of the citizen is {}. \n The citizen was born in the year {}. \n And finally, the citizen has an iQ of {}.".format(citizen256032.first_name, citizen256032.middle_name, citizen256032.last_name, citizen256032.species, citizen256032.gender, str(citizen256032.YOB), str(citizen256032.iQ)))
```

Also, you need to move your species declaration outside of __init__():
```
class PassPort(object):

    species = 'homo-sapien'
```

Hope that helps.

---

### Post by Drone4four on 2017-11-05
Thank you, **@kostkon**.  This helps.

---

