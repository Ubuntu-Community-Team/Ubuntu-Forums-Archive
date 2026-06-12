---
title: "No Space After Variables in Python (3.2)"
date: 2011-08-30
forum: Programming Talk
---

### Post by dniMretsaM on 2011-08-30
I'm writing a script in Python 3.2 and I'm wondering how to insert a variable into a string without there being a space after it. If your not sure what I mean I can give an example.

---

### Post by llanitedave on 2011-08-30
don't you mean something like 

mystring = "first part of text " + str(variable) + "second part of text"

---

### Post by cgroza on 2011-08-30
You should post a some code. How do you insert the variable into the string? Using concatenation or do you use the format method?
Using format:
```
 
"{0} {1} {2}".format(var0, var1, var2)

```

---

### Post by Smart Viking on 2011-08-30
Example, yes! Don't ask, just give an example in the first post, we can't read your mind but we can read code!

Python does not insert a space in a string variable. The print function, however, does. Also maybe you're confusing space with EOL, so I'll just give examples for both.

Get ridd of space and EOL after print:
```

print("Hello",end=''),
print("World!")
# "end=''" removes extra space, the "," removes the EOL character.

```

Edit: You don't need the "," in this situation, the "end='' " also removes the EOL character.

---

### Post by dniMretsaM on 2011-08-31
Example:
```
name = input("What is your name? ")
print("Hello, ", name, "!")
```

So if you entered "Joe Smith" as your name you would get the output:
```
Hello,  Joe Smith !
```

What I am looking for is this:
```
Hello, Joe Smith!
```

Anyway, someone mentioned concatenation and I tried that. It worked. I forgot that you could use that for variables. So anyway, solved. Thanks people!

---

### Post by ofnuts on 2011-08-31
> **dniMretsaM said:**
> Example:
```
name = input("What is your name? ")
print("Hello, ", name, "!")
```So if you entered "Joe Smith" as your name you would get the output:
```
Hello,  Joe Smith !
```What I am looking for is this:
```
Hello, Joe Smith!
```Anyway, someone mentioned concatenation and I tried that. It worked. I forgot that you could use that for variables. So anyway, solved. Thanks people!

You can also use the % operator:
```

name='Joe Smith'
print 'Hello, %s!' % name

Hello, Joe Smith!

```

---

### Post by dniMretsaM on 2011-08-31
> **ofnuts said:**
> You can also use the % operator:
```

name='Joe Smith'
print 'Hello, %s!' % name

Hello, Joe Smith!

```

Ok, I'll take note of that. Thanks.

---

