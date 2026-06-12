---
title: "Python Functions Confusion"
date: 2009-07-04
forum: Programming Talk
---

### Post by tdrusk on 2009-07-04
I am trying to write a program in python that involves many variables. To keep it simple I want a 
```
getVariableName()
returnVariableName(variableName)
```

I am trying to do it like this
```

#variableName.py
def getVariableName()
	variableName = raw_input("What is variableName?")
def returnVariableName(variableName)
	return variableName

getVariableName()
returnVariableName(variableName)

```

This obviously isn't correct because I am recieving an error saying
```

Traceback (most recent call last):
	File "variableName.py", line 8, in <module>
		returnVariableName(variableName)
NameError: name 'variableName' is not defined

```

What can I do to make my program functional?

---

### Post by CptPicard on 2009-07-04
To strictly answer the "what is wrong" question, you're probably looking for the Python "global" keyword. On the other hand I don't understand what you are trying to accomplish, esp. with a function that just returns its argument...

---

### Post by tdrusk on 2009-07-04
> **CptPicard said:**
> To strictly answer the "what is wrong" question, you're probably looking for the Python "global" keyword. On the other hand I don't understand what you are trying to accomplish, esp. with a function that just returns its argument...
So I tried doing something like
```

def x():
    x=int(raw_input("Enter variable"))
    return x

def main()
    x
    x()
    print x

main()

```and I get 
```
<function variable at *memory location*>
```

---

### Post by CptPicard on 2009-07-04
Well, naturally. The only meaningful thing you're doing is "print x" which... prints that x is a function.

I really don't get what you're trying to do, you seem rather confused :)

---

### Post by Can+~ on 2009-07-04
And how do you think the variable x from one of the functions is getting onto the other scope?

Variables declared inside a scope are bound to that scope.

[PHP]def x():
    z = int(raw_input("Enter variable"))
    return z

def main()
    print x()

main()[/PHP]

(Changed the function names to make it clearer)

---

### Post by days_of_ruin on 2009-07-04
I don't know what you are trying to do but using a dictionary would probably be better.

```
variables = {}
variables['foo'] = 123

print variables['foo']
```

---

### Post by howlingmadhowie on 2009-07-04
> **tdrusk said:**
> I am trying to write a program in python that involves many variables. To keep it simple I want a 
```
getVariableName()
returnVariableName(variableName)
```

I am trying to do it like this
```

#variableName.py
def getVariableName()
	variableName = raw_input("What is variableName?")
def returnVariableName(variableName)
	return variableName

getVariableName()
returnVariableName(variableName)

```

This obviously isn't correct because I am recieving an error saying
```

Traceback (most recent call last):
	File "variableName.py", line 8, in <module>
		returnVariableName(variableName)
NameError: name 'variableName' is not defined

```

What can I do to make my program functional?

'variableName' is only defined inside the function 'getVariableName()'. to make it exist outside the function you have to define it outside the function and then use the 'global' keyword to find it. here an example:

```

x=0

def incrementx():
  global x
  x=x+1

print(x)
incrementx()
print(x)

```

generally one of the useful qualities of functions is precisely the fact that variables don't tend to escape them. this allows you to be sure of the effect the function has on the state of the program. by using the 'global' keyword you are breaking this encapsulation.

---

### Post by Can+~ on 2009-07-04
Try to read more about [Scopes]("http://en.wikipedia.org/wiki/Scope_(programming)").

---

