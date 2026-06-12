---
title: "Executing .py files"
date: 2009-07-24
forum: Programming Talk
---

### Post by Dullstar on 2009-07-24
Help.  I'm trying to learn to program in Python, but I am having trouble getting .py files to execute once I finish them.

btw, C or any similar languages are NOT acceptable solutions.  I have tried them before, but couldn't get so far as completing the Hello World tutorial due to their confusing syntax.

---

### Post by Dullstar on 2009-07-24
I forgot to mention, I am running Ubuntu 9.04 for this.

---

### Post by OutOfReach on 2009-07-24
You can try this from the command line:
```

python my_file.py

```


Or, you can add the shebang line:
```

#!/usr/bin/env python

```
at the very top of your code, and make the file executable:
```

chmod +x my_file.py

```
so you can just do:
```

./my_file.py

```

---

### Post by Dullstar on 2009-07-24
Hold on, please.  I'm going to apply the changes that I think you say I need to do to the file, if that doesn't work I'll post the source code and see if someone can fix it.

---

### Post by Dullstar on 2009-07-24
This is the source code.
```
#!/usr/bin/env python
chmod +x calc.py

# Python Calculator

true=1
print "Welcome to the Calculator"
print "-------------------"
print
pi = 3.141592653
print "We support the use of pi."
print 
print "In a future version we hope to make the program loop to the beginning of code after completion."
print "The string for pi is simply... pi."
#pick operation



repeating=true
running=true

while(repeating):
    while(running):
        print "Please select operation."
        print
        print "Fractions don't work."
        print
        print "Equation (sorry, no variables) - 1"
        print "Area - 2"
        print "Powers - 3"

        # usrimput

        oper = input(">>> ")

        if oper == 1:

            print "Please enter the equation (remember, no variables)"
            prob = input (">>> ")
            answer = prob
            print answer
            print
            print
            print

        if oper == 2:
            print "Please select a shape."
            print "Recangle - 1"
            print "Circle - 2"
            print "Triangle - 3"
            print
            print "Squares, rhombuses, and paralellograms can be done through the rectangle."
            shape = input (">>> ")

            if shape == 1:
                print "You have chosen a rectangle."
                print "The formula is length*width."
                print "What is the length?"
                length = input (">>> ")
                print "What is the width?"
                width = input (">>> ")
                area = length*width
                print area
                print
                print
                print

            if shape == 2:
                print "You have chosen a circle."
                print "Formula is Radius*Radius*Pi"
                print "This calculator uses 3.141592653 for pi."
                print "Do you have the radius (1) or the diameter (2)?"
                circle = input ("Radius (1) or Diameter (2)>>> ")

                if circle == 2:
                    print "What is the diameter of the circle?"
                    print "Formula is diameter/2.0"
                    diameter = input (">>> ")
                    radius = diameter/2.0
                    print "Radius is", radius
                    area = radius*radius*pi
                    print area
                    print
                    print
                    print
        
                if circle == 1:
                    print "What is the radius?"
                    radius = input (">>> ")
                    area = radius*radius*pi
                    print area
                    print
                    print
                    print

                if circle > 2:
                    print "INVALID INPUT"
                    print
                    print
                    print

                if circle < 1:
                    print "INVADLID INPUT"
                    print
                    print
                    print

            if shape == 3:
                print "You have chosen a triangle."
                print "Formula is base*height*0.5"
                print "What is the base?"
                base = input (">>> ")
                print "What is the height?"
                height = input (">>> ")
                area = base*height*0.5
                print area
                print
                print
                print

            if shape > 3:
                print "INVALID INPUT"
                print
                print
                print

            if shape < 1:
                print "INVALID INPUT"
                print
                print
                print

        if oper == 3:
            print "What number to what power?"
            print "Please enter number."
            number = input (">>> ")
            print "Please enter power."
            power = input (">>> ")
            answer = number**power
            print answer
            print
            print
            print
            
        if oper > 3:
            print "INVALID INPUT"
            print
            print
            print

        if oper < 1:
            print "INVALID INPUT"
            print
            print
            print


    
repeating=true
running=true

```

Now that I look at it, there is some text I never got around to updating.  Just printed stuff though, shouldn't have any input on the code.

Can you help me figure out what the problem is?  It won't execute at all.

---

### Post by OutOfReach on 2009-07-24
Ok the #!/usr/bin/env python is in the right place, but I meant inserting the command
```

chmod +x my_file.py

```
into the command line, not into the file, sorry about the confusion.
EDIT: Make sure to do the above command in the correct directory, for example if the file is on your desktop, you would do:
```

cd ~/Desktop/

```
then the first command.

---

### Post by Dullstar on 2009-07-24
Thanks.

Is there a way I can make it executable just like any other program though?
After all, I'm going to be making a game with this language.

---

### Post by Dullstar on 2009-07-24
It's working in the terminal now.  Is there a way I can get it to run by navigating to the file itself and double clicking on it?

---

### Post by OutOfReach on 2009-07-24
> **Dullstar said:**
> It's working in the terminal now.  Is there a way I can get it to run by navigating to the file itself and double clicking on it?
Hmm...I'm not quite sure but since you have made it executable (with the chmod command), try double clicking on it, it should come up with a prompt with some options, and one of those options __should__ be something like "Run in Terminal", try clicking on that.

---

### Post by Dullstar on 2009-07-24
I'll see if that works.

---

### Post by Dullstar on 2009-07-24
It's working!  Thanks, OutOfReach.  I'm going to make a few polishes to the code, then upload it to my website.  I'll be sure to credit you for helping me solve the problems that popped up!

---

### Post by OutOfReach on 2009-07-24
> **Dullstar said:**
> It's working!  Thanks, OutOfReach.  I'm going to make a few polishes to the code, then upload it to my website.  I'll be sure to credit you for helping me solve the problems that popped up!
Glad to help :)

---

