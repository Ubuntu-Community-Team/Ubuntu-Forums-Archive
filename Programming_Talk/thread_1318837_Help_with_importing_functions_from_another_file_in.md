---
title: "Help with importing functions from another file in Python"
date: 2009-11-07
forum: Programming Talk
---

### Post by Tradewind on 2009-11-07
Hello, 
I need help on importing functions so they can be used in a different file. For example, if I have a file A, that looks something like this: 
 
 ```
def return_something(text, list_of_text): 
 
if text in list_of_text: 
   if text = 'Yes': 
      print 'True' 
   else: 
      print 'False' 
else: 
   print 'None'
```
  
And in another file B, I'll request user input through raw_input, and use the function "return_something" from A to process the text in B, so either "True" or "False" is printed in file B, how do I do that? "return_something" needs two parameters, but in file B all I want the user to do is input one string, and the program analyzes that string with the list_of_text in file A, processes it with the if/print statements, then display the result back in file B. 
 
Thanks!

---

### Post by themusicwave on 2009-11-08
If you want to use things from another file you need to use import. Check out this link for details:

[http://effbot.org/zone/import-confusion.htm]("http://effbot.org/zone/import-confusion.htm")

---

### Post by Tradewind on 2009-11-08
Hello I realize I have to use import, but I was confused about the two parameters. In the second file all the user does is input one line of text, but the function requires two parameters. How do I call the function from file A in file B after importing it? Is it return_something('user text here', list_of_text)? But would file B recognize what "list_of_text" is, if it's defined in file A?

---

### Post by themusicwave on 2009-11-08
[PHP]#File A.py
def foo(arg):
  print arg

#File B.py
import A

A.foo("Test")
[/PHP]

That is how you call a function in A from B with an argument. When the foo function gets called, whatever value you give it gets passed in as arg.

---

### Post by Tradewind on 2009-11-09
I need to use the same variable as the one found in file A. How do I write that if I want to call that function in file B?
E.g., in file A:
```
#a is some string, b is a list of strings
def func(a, b):
  if a in b:
    print 'True'
  else:
    print 'False'
```File B:
```
import A

answer = raw_input('please enter string for variable a: ')

#then call the function 'func' in file A to analyze the string 'answer', then print either True or False
```

---

### Post by themusicwave on 2009-11-09
I think you want something like this:

[PHP]
import A

answer = raw_input('please enter string for variable a: ')
words = ['word1','word2','word3']
value = A.func(words, answer)
print value
[/PHP]

You actually don't need value I just did that for readability.  you could do this instead:

[PHP]
import A

answer = raw_input('please enter string for variable a: ')
words = ['word1','word2','word3']
print A.func(words, answer)
[/PHP]

Also if this is python 3.0 make sure you use print as a function instead like print( A.func(answer, words) )

Hope that helps.

---

### Post by Tradewind on 2009-11-09
The problem is the list is not fixed, it's a variable. I cannot set what the list is, because the user enters it, so I need to treat it like a variable. I need a way to import that variable into the second file for use.

---

### Post by delfick on 2009-11-10
like this ??

FILE A.py----------
[php]
from B import func

numItems = raw_input("Enter the number of items in your list : ")
try:
    numItems = int(numItems)
except ValueError:
    numItems = None
    print "You didn't enter an integer, exiting now"

if numItems:
    items = []
    for item in range(numItems):
        next = raw_input("Enter the next item : ")
        items.append(next)
    
    print "You've entered %s" % items
    
    varA = raw_input("Please enter a value for variable a : ")
    
    func(varA, items)
[/php]

FILE B.py---------
[php]
def func(a, b):
  print a in b
[/php]

---

### Post by Tradewind on 2009-11-10
Hello,
That won't work as I already have what the list is in the first file, it's actually one of the return values of a really complex function. I need to directly import that variable into the second file, I cannot redo the entire function in first file to define what that variable is again in second file.
E.g.:
First file:
```
def complex_function(parameters):

    #lots of code

    a_tuple = (d1, d2, a)
    return a_tuple
```


Second file:

#Now I need to import "d1" and "d2" (since they're dictionaries) into another file. So I can write stuff like:

```
 x = d1[0] #first term in dictionary from first file
```

---

### Post by delfick on 2009-11-10
I get this feeling you don't fully understand what the computer is actually doing here.

I can't really give a decent explanation (hopefully someone will expand) but...
[SIZE="1"](edit: infact, reading it, I can see how that might not make much sense, sorry :p)[/SIZE]

Having code in different files is only a logical separation of code, as in it's only for the sake of humans. (Well, there are scope rules :  [http://en.wikipedia.org/wiki/Scope_(programming](http://en.wikipedia.org/wiki/Scope_(programming)) ) but at the end of the day. at the lowest level, it isn't running from the file itself.

When you pass a function some arguments then it doesn't matter which file you've created those variables in, it all ends up on the stack ([http://en.wikipedia.org/wiki/Call_stack](http://en.wikipedia.org/wiki/Call_stack)). Well, references to them anyways.

so you can do something like this

FILE A.py----------
[php]
from B import func

def funcThatCreatesList():
    return ['yes', 'no', 'maybe']


items = funcThatCreatesList()
varA = raw_input("Please enter a value for variable a : ")
func(varA, items)
[/php]

FILE B.py---------
[php]
def func(a, b):
  print a in b
[/php]

...

:)

---

### Post by Tradewind on 2009-11-10
Hello,
Thanks I figured out the problem I had. I just needed to re-define each parameter of the function of file A in file B, then I can successfully call that function, and even variables inside that function.

---

