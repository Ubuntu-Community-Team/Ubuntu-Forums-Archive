---
title: "python script help D:"
date: 2010-05-04
forum: Programming Talk
---

### Post by makuab on 2010-05-04
# Area calculation program

print "Welcome to the Area calculation program"
print "---------------------------------------"
print

# Print out the menu:
print "Please select a shape:"
print "1  Rectangle"
print "2  Circle"
print "3  Square"

# Get the user's choice:
shape = input("> ")

# Calculate the area:
if shape == 1:
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")
    area = height*width
    print "The area is", area

elif shape == 2:
    radius = input("Please enter the radius: ")
    area = 3.14*(radius**2)
    print "The area is", area

elif shape == 3:
    length = input("Please enter the length of one side")
    area = length**2
    print "the area is", area

else:
    # If all else fails...
    


I get this error
  
File "yes.py", line 36
    
        ^
IndentationError: expected an indented block

---

### Post by makuab on 2010-05-04
double post sorry.

---

### Post by lisati on 2010-05-04
Moved to "programming talk"

Suggestion: when pasting code, put [noparse]```
 at the start, and 
```[/noparse] at the end. This will help preserve formatting, which not only aids readability, but can make a difference in some programming languages.

---

### Post by doas777 on 2010-05-04
well, first off, please post your code in a code block (the '#' button on the top of the reply frame), and make sure you keep your indents. for instance:
```

# Area calculation program

print "Welcome to the Area calculation program"
print "---------------------------------------"
print

# Print out the menu:
print "Please select a shape:"
print "1 Rectangle"
print "2 Circle"
print "3 Square"

# Get the user's choice:
shape = input("> ")

# Calculate the area:
if shape == 1:
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")
    area = height*width
    print "The area is", area

elif shape == 2:
    radius = input("Please enter the radius: ")
    area = 3.14*(radius**2)
    print "The area is", area

elif shape == 3:
    length = input("Please enter the length of one side")
    area = length**2
    print "the area is", area

else:
    print "exiting"


```

note the bottom line. you had 
```

else:
#comment. 

```

the code was breaking on the comment, becase every statement following a ':' is supposed to be indented. you didn't have a line there, but the interpreter checked for indent before checking to see if there was any code to run. 

hth

---

### Post by Nebelhom on 2010-05-04
Could you post it as code format please.

at the moment, you don't have any indentation which is the way python distinguishes between code blocks.

for example after each if statement, the next line has to be indented (typically by four spaces in relation to the above if statement).

example from your code:

```
# Calculate the area:

if shape == 1:
    # four space indentation
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")   
    area = height*width
    print "The area is", area
```

does that answer it?

---

