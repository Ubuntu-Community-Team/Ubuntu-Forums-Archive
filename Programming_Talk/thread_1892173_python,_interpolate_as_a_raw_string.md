---
title: "python, interpolate as a raw string"
date: 2011-12-07
forum: Programming Talk
---

### Post by cybo on 2011-12-07
i have a variable that contains a path to a file
full_path = 'C:\Documents and Settings\user\myfile.pdf'

this variable is accepted by a function. for this function to work this variable must be interpreted as a raw string. 

when there is regular text in python this can be achieved as following:

r'C:\Documents and Settings\user\myfile.pdf'

the question is how can i do this with a variable i.e something like

r'full_path'

any help is appreciated

---

### Post by CoffeeRain on 2011-12-07
Are you looking for something like eval()?

---

### Post by Vaphell on 2011-12-07
could you explain why do you need it as a raw string? maybe some small snippet showcasing the problem?

afaik r'' has meaning only when you create a string - treat '\' literally instead of escaping something else with it. Once the series of bytes is defined, it's over. The right place to do that would be
```
full_path = r'...'
``` because that's where full_path gets its value.

---

### Post by cybo on 2011-12-08
i'm writing a script where user will need to specify a full path to a file. the end user will specify it through a variable and doesn't understand much about python or raw strings.

also for the future use it would have been nice to know how to do that in case the path is specified through an option, i.e.

myscript.py -full_path "C:\My Documents\task.pdf"

---

### Post by cybo on 2011-12-08
i'd like to avoid using eval if possible.

---

### Post by ofnuts on 2011-12-08
> **cybo said:**
> i have a variable that contains a path to a file
full_path = 'C:\Documents and Settings\user\myfile.pdf'

this variable is accepted by a function. for this function to work this variable must be interpreted as a raw string. 

when there is regular text in python this can be achieved as following:

r'C:\Documents and Settings\user\myfile.pdf'

the question is how can i do this with a variable i.e something like

r'full_path'

any help is appreciatedI don't quite understand the problem. Once the data is in a variable it is used as is. Escaping and 'raw' concepts only get into play when interpreting literals. So you don't need to do anything special with full_path if its value contains backslashes (or quotes...)

---

### Post by 11jmb on 2011-12-08
> **cybo said:**
> i'm writing a script where user will need to specify a full path to a file. the end user will specify it through a variable and doesn't understand much about python or raw strings.

also for the future use it would have been nice to know how to do that in case the path is specified through an option, i.e.

myscript.py -full_path "C:\My Documents\task.pdf"

In this case, remember that whatever is calling your Python script will have first pass on parsing your arguments. bash and a python interpreter may parse different inputs differently before calling your script. This is outside of my experience, but it is another thing to look out for when using special characters as command line args.

---

### Post by cybo on 2011-12-08
> **ofnuts said:**
> I don't quite understand the problem. Once the data is in a variable it is used as is. Escaping and 'raw' concepts only get into play when interpreting literals. So you don't need to do anything special with full_path if its value contains backslashes (or quotes...)

say i have the following code:

```
full_path = 'C:\My Documents\tasks\mytasks.txt'
f = open(full_path)
```

the code won't work because \t will be interpreted as a special character.

the only way it will work if i interpret full_path as a raw string, i.e.
```
full_path = r'C:\My Documents\tasks\mytasks.txt'
```

the problem that i'm having is that full_path comes to me from somewhere else as a string and i need to convert it to a raw string.

---

### Post by StephenF on 2011-12-08
> **cybo said:**
> the problem that i'm having is that full_path comes to me from somewhere else as a string and i need to convert it to a raw string.
Python does not have a raw string variable type.

I think what the OP is saying is that a string has been supplied which contains among others tab characters and they require converting to literal \t. In nearly all cases this is the wrong thing to do. Suppose you are supplying the file name on the command line then there is some quoting method that enables you to supply that text in the correct form to the program. The example below shows the effect of double quotes.
```
 
$ echo hello\tworld
hellotworld
$ echo "hello\tworld"
hello\tworld

```

---

### Post by ofnuts on 2011-12-08
> **cybo said:**
> say i have the following code:

```
full_path = 'C:\My Documents\tasks\mytasks.txt'
f = open(full_path)
```the code won't work because \t will be interpreted as a special character.

the only way it will work if i interpret full_path as a raw string, i.e.
```
full_path = r'C:\My Documents\tasks\mytasks.txt'
```the problem that i'm having is that full_path comes to me from somewhere else as a string and i need to convert it to a raw string.
Exactly... If it "comes form somewhere else" (read from a file/pipe/console) python won't interpret your backslashes as escapes... Raw strings are used to short circuit an analysis that happens when the source code is read and that applies only to the source code.

Try this code:
```

while True:
    # in Python V3, "raw_input()" is renamed "input()"
    input=raw_input("Input any string:")
    print "You entered: %s (%d characters)" % (input,len(input))

```
You can enter all kinds of backslashes and they will be kept. If you put "\n" in your input, it will remain unchanged and the output will be on a single line.

---

### Post by CoffeeRain on 2011-12-08
If you ask a user for input, raw_input() would work.

---

### Post by cybo on 2011-12-08
OK. thanks. i think i can take it from here.

---

### Post by CoffeeRain on 2011-12-08
Cool! :P

---

