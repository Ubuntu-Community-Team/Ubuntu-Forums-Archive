---
title: "Simple Python Question"
date: 2007-07-19
forum: Programming Talk
---

### Post by tc101 on 2007-07-19
This does not work work:

print hello()
def hello():
    h = "Hello World"
    return h

But this does:

def hello():
    h = "Hello World"
    return h
print hello()

I assume because the interpreter goes line by line and in the first example the hello function has not been created yet. 

Is there some way to get around this limitation?  I am using SPE IDE.  Should I compile before testing or is there a better way?

---

### Post by smartbei on 2007-07-19
There is no way to get around this limitation. If I my ask: Why do you want to?

BTW - please use [ code] tags around your code - it keeps the tabbing in order. Like this:
[ code]
def hello():
h = "Hello World"
return h
print hello()
[/code ]

Looks like:
```

def hello():
	h = "Hello World"
	return h
print hello()

```

---

### Post by thomasaaron on 2007-07-19
It is considered good programming practice to put import statements first, then function definitions, then... whatever else you want to.

Python just enforces it (at least the function definitions coming before other code part).

---

### Post by steve.horsley on 2007-07-19
P.S.
You don't need to say **print hello()**. Just **hello()** will do, as the print statement is inside the function. In fact, hello() prints "Hello World" and then returns None. Your current code then goes on to print the None (a blank line) that hello() returned.

---

### Post by Mirrorball on 2007-07-19
His funcion returns "Hello World," but it's hard to see because of the lack of indentation.

---

### Post by pmasiar on 2007-07-19
> **tc101 said:**
> Is there some way to get around this limitation?  

It is not a limitation - it is a feature :-)  Parser after single pass knows what to do with every name.

Standard idiom is to define all functions, and possible initiating code, then add:

```

def main():
    # call functions for main functionality

# idiomatic start of the main() program
if __name__ == '__main__': 
    main()

```

This allows you to use your code as a module in other programs, without executing the main().

---

### Post by steve.horsley on 2007-07-20
> **Mirrorball said:**
> His funcion returns "Hello World," but it's hard to see because of the lack of indentation.

Oops! I'll just shuffle off back to my rubber cell. I hate that room. I keep slipping on the drible.

---

### Post by tc101 on 2007-07-20
Thanks for your help.  I see how the standards work.  This is new for me.  I was originally a COBOL programmer, starting in the 70's.  Then VB until I retired a few years ago.  I see how this works, but I still find it more appealing to see the main structure of the program in the first few lines of code, rather than having to scroll down though all functions to find the main() code that calls the functions.  That's just me though.  I know I am behind the times.

Another simple question.  Why do we surround certain names with two underscores, as in __Name__ ?

---

### Post by pmasiar on 2007-07-20
__vars__ have special meaning. __name__ is replaced with module name. Other __names__ can be used for method overloading, like __add__ to redefine +, etc. You don't need to know it untill you are deep into designing your own objects.

---

### Post by steve.horsley on 2007-07-21
After a while you get used to the main entry point being at the bottom. I have in the past placed a ```
def main():
``` at the top of the file, and placed 
```

if __name__ == "__main__":
    main()

```
at the bottom. It does have the advantage that you can "return" from main if you discover a problem without having to call sys.exit() - you can't return from the top level. 

It also means that you can import the file as a module to make use of the function definitiions it makes, without main() getting executed. __name__ is only set to "__main__" if the file is launched as the main python application, otherwise it is the name of the imported module.

---

### Post by tc101 on 2007-07-21
Thanks for your help guys.  I'll keep studying and eventually it will all become clear.

---

