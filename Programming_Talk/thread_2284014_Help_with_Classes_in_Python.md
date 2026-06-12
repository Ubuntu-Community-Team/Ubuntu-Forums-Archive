---
title: "Help with Classes in Python"
date: 2015-06-26
forum: Programming Talk
---

### Post by branau on 2015-06-26
Hey guys, I'm having a hard time with this code here. First, I get some input from a user and store it in a variable:
```
def My_Class(object:
    my_input = input("My question here?")
    my_input = my_input.lower()

```

Next, based on what I get back from the user, I have a series of variables that change:
```

    if "foo" in my_input:
        variable1 = "1"
        variable2 = "2"
        variable3 = "__/__/__/__/__/__/__/__"
        template = '| {:^38} | {:^7} | {:^6} | {:^12} | {:^24} |'
    elif "bar" in my_input:
        variable1 = "3"
        variable2 = "4"
        variable3 = "__/__/__"
        template = '| {:^50} | {:^7} | {:^6} | {:^12} | {:^12} |'
    elif "abc" in my_input:
        variable1 = "5"
        variable2 = "6"
        variable3 = "__/__/__"
        template = '| {:^50} | {:^7} | {:^6} | {:^12} | {:^12} |'

```

Later on, within the same class, I have a couple of functions that call on these variables:
```

    def titles():
        print (template.format("Some", "Text", "Here", "And", "Here"), file = log)
        print("|", "-" * 99, "|", file = log)

    def print_my_list(my_list):
        for item in my_list:
            print (template.format(item, '_____', variable1, variable2, variable3), file = log)

```

When I try to run it, I get this error code:
```

Traceback (most recent call last):
  File "my_file.py", line 6, in <module>
    class My_Class(object):
  File "my_file.py", line 132, in My_Class
    titles()
  File "my_file.py", line 104, in titles
    print (template.format("Some", "Text", "Here", "And", "Here"), file = log)
NameError: name 'template' is not defined

```
If I remove the title() function and place its contents in-line with the rest of the class content, it runs just fine. However, I have to call on this a lot so I'd rather it be a function to reduce the amount of typing I have to do and to make the code look neater.
Any ideas on how I could fix this?

EDIT: Figured it out.

---

### Post by ajgreeny on 2015-06-26
"Figured it out" doesn't help anyone with the same query who happens to be searching for an answer to the same problem.

Tell us all please what the solution was.

---

### Post by branau on 2015-06-26
> **ajgreeny said:**
> "Figured it out" doesn't help anyone with the same query who happens to be searching for an answer to the same problem.

Tell us all please what the solution was.

Sorry about that. Here goes:

When I first wrote the program, it had classes but it wasn't really object-oriented. The classes were mostly for show and had no real use other than to organize my program. Once I started repeating the same things over and over, I tried to move them into functions so that I could clean up the code and reduce the amount of typing involved but that threw NameErrors all over the place. 

```
def My_Class(object):
    my_input = input("My question here?")
    my_input = my_input.lower()

```

First I moved this into a function, and had to add the "self" argument to each. That allowed me to call it and save the answer as a variable as so:
```
def My_Class(object:
    def my_question(self)
        self.my_input = input("My question here?")
        self.my_input = my_input.lower()
        return my_input

    answer = my_question()

```

Next, I had to move this into a function as well.

```

    def my_function(self, my_input):
        if "foo" in my_input:
            self.variable1 = "1"
            self.variable2 = "2"
            self.variable3 = "__/__/__/__/__/__/__/__"
            self.template = '| {:^38} | {:^7} | {:^6} | {:^12} | {:^24} |'
        elif "bar" in my_input:
            self.variable1 = "3"
            self.variable2 = "4"
            self.variable3 = "__/__/__"
            self.template = '| {:^50} | {:^7} | {:^6} | {:^12} | {:^12} |'
       elif "abc" in my_input:
            self.variable1 = "5"
            selfvariable2 = "6"
            self.variable3 = "__/__/__"
            self.template = '| {:^50} | {:^7} | {:^6} | {:^12} | {:^12} |'

```

The same had to be done with my titles() function:

```

    def titles(self):
        print (self.template.format("Some", "Text", "Here", "And", "Here"), file = log)
        print("|", "-" * 99, "|", file = log)

    def print_my_list(my_list):
        for item in my_list:
            print (self.template.format(item, '_____', self.variable1, self.variable2, self.variable3), file = log)

```

I also had never made an instance of my class, I was just running everything out of the class itself, so I did that.

```

class1 = My_Class()

```

Finally, I created an Engine class that would run all of the functions from my class:

```

def Engine(object):
    def start(My_Class):
        My_Class.answer = my_question()
        My_Class.titles(self)
        My_Class.my_function(answer)

```

So, after creating the instance of my class, I just call it with my Engine class' function as so:

```

Engine.start(class1)

```

And then it runs as expected!

I hope that's clear. If it isn't I'd be happy to attempt to help anyone else who stumbles upon this.

---

### Post by ofnuts on 2015-06-27
> **ajgreeny said:**
> "Figured it out" doesn't help anyone with the same query who happens to be searching for an answer to the same problem.

Tell us all please what the solution was.

[http://www.python-forum.org/viewtopic.php?f=6&t=16125](http://www.python-forum.org/viewtopic.php?f=6&t=16125)

---

