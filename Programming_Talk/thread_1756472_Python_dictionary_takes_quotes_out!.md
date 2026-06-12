---
title: "Python dictionary takes quotes out!"
date: 2011-05-12
forum: Programming Talk
---

### Post by CoffeeRain on 2011-05-12
I have a python program that gets input, saves it in a dictionary, and writes it to a file. When I get it out at the next time I run it, all the quotes are gone so it will not work. Do you have any ideas how to fix it, or a command I could run to put the quotes in the right spots?

---

### Post by Riisen on 2011-05-12
how do you get the text and how do you write it to file x?

---

### Post by Arndt on 2011-05-12
> **CoffeeRain said:**
> I have a python program that gets input, saves it in a dictionary, and writes it to a file. When I get it out at the next time I run it, all the quotes are gone so it will not work. Do you have any ideas how to fix it, or a command I could run to put the quotes in the right spots?

Do you have some example code that shows the problem?

---

### Post by CoffeeRain on 2011-05-12
Sure, here's some code.

```
r = open('dictionary.txt', 'r')
d = r.read()
d = eval(d)
r.close()

word = raw_input('Foo? ')
word2 = raw_input('Baz? ')
d[word] = word2

os.system('echo ' + pickle.dumps(d) + ' > dictionary.txt')
```

I mean this isn't all of it, in case it doesn't work, but I hope it's enough to give you a general idea.

---

### Post by simeon87 on 2011-05-12
If you use pickle to write the file then you also have to use pickle to load the file: [http://docs.python.org/library/pickle.html#pickle.load](http://docs.python.org/library/pickle.html#pickle.load) or [http://docs.python.org/library/pickle.html#pickle.loads](http://docs.python.org/library/pickle.html#pickle.loads)

---

### Post by CoffeeRain on 2011-05-12
I figured I should put the error message up...

```
File "dict.py", line 6, in <module>
    d = eval(d)
  File "<string>", line 1

{box: A box is something that can hold stuff., hut: A hut is a dwelling place, usually thought of as small.,.....}
```

The first few times I tried putting quotes around the stuff to figure out if that was the problem, and it worked the next time, but it just took the quotes out. Would it be something about using pickle?

---

### Post by CoffeeRain on 2011-05-12
Thanks, I was probably composing my thing when you replied. I'll try that.

---

### Post by CoffeeRain on 2011-05-12
Now it says

 ```
Traceback (most recent call last):
  File "dict.py", line 5, in <module>
    d = pickle.load('/Users/foo/dictionary.txt')
  File "/System/Library/Frameworks/Python.framework/Versions/2.6/lib/python2.6/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/System/Library/Frameworks/Python.framework/Versions/2.6/lib/python2.6/pickle.py", line 841, in __init__
    self.readline = file.readline
AttributeError: 'str' object has no attribute 'readline'
```

I'm guessing it means that the dictionary got converted to a string and didn't get converted back.

---

### Post by simeon87 on 2011-05-12
> **CoffeeRain said:**
> Now it says

 ```
Traceback (most recent call last):
  File "dict.py", line 5, in <module>
    d = pickle.load('/Users/foo/dictionary.txt')
  File "/System/Library/Frameworks/Python.framework/Versions/2.6/lib/python2.6/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/System/Library/Frameworks/Python.framework/Versions/2.6/lib/python2.6/pickle.py", line 841, in __init__
    self.readline = file.readline
AttributeError: 'str' object has no attribute 'readline'
```

I'm guessing it means that the dictionary got converted to a string and didn't get converted back.

You are calling pickle.load with a string but you have to call it with a file object, see the documentation: [http://docs.python.org/library/pickle.html#pickle.load](http://docs.python.org/library/pickle.html#pickle.load)

---

### Post by CoffeeRain on 2011-05-12
Like this?

```
r = open('dictionary.txt', 'r')
d = pickle.load(r.read())
```

I've tried it, but it still gives an error about a string.

---

### Post by simeon87 on 2011-05-12
> **CoffeeRain said:**
> Like this?

```
r = open('dictionary.txt', 'r')
d = pickle.load(r.read())
```

I've tried it, but it still gives an error about a string.

Try pickle.load(r). By calling read() you're still turning it into a string.

---

### Post by Zugzwang on 2011-05-12
> **CoffeeRain said:**
> Sure, here's some code.

```
r = open('dictionary.txt', 'r')
d = r.read()
d = eval(d)
r.close()

word = raw_input('Foo? ')
word2 = raw_input('Baz? ')
d[word] = word2

os.system('echo ' + pickle.dumps(d) + ' > dictionary.txt')
```

I mean this isn't all of it, in case it doesn't work, but I hope it's enough to give you a general idea.

@OP: Apprently you didn't got an answer to the question where the quotes went until now (or did I miss the post?). The reason is that when calling os.system, the quotes are interpreted by the shell and thus never appear in "dictionary.txt". Example terminal session:
```

me@my-computer:/tmp$ echo "Hello"
Hello

```
As you can see, the quotes vanish.

However, the solution not to use "os.system" that has somewhat been proposed in this thread is the right one to solve your problem.

---

### Post by CoffeeRain on 2011-05-12
Thanks for the tips! Thanks for explaining why the quotes go away. Now I get an end of file error for pickle.load(r).

---

### Post by CoffeeRain on 2011-05-12
I think I fixed that, because I found out nothing was in the file. Now I get...
 ```
raceback (most recent call last):
  File "dict.py", line 5, in <module>
    d = pickle.load(r)
  File "/System/Library/Frameworks/Python.framework/Versions/2.6/lib/python2.6/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/System/Library/Frameworks/Python.framework/Versions/2.6/lib/python2.6/pickle.py", line 858, in load
    dispatch[key](self)
KeyError: '{'

```

I tried using pickle in the interpreter, but it won't work. Yes, it was imported. I get this...
```
 Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/System/Library/Frameworks/Python.framework/Versions/2.6/lib/python2.6/pickle.py", line 1374, in loads
    return Unpickler(file).load()
  File "/System/Library/Frameworks/Python.framework/Versions/2.6/lib/python2.6/pickle.py", line 858, in load
    dispatch[key](self)
  File "/System/Library/Frameworks/Python.framework/Versions/2.6/lib/python2.6/pickle.py", line 1156, in load_binget
    self.append(self.memo[repr(i)])
KeyError: '105' 
```

---

### Post by simeon87 on 2011-05-12
Can you post your updated code to see what you're doing now? If you're getting errors in pickle it most likely means you're passing the wrong kind of data as input or arguments. Use the documentation to see what kind of information a function expects. Python won't say anything unless you run the code and see that it wasn't the right thing.

---

### Post by CoffeeRain on 2011-05-12
OK,

```
r = open('dictionary.txt', 'r')
d = pickle.load(r)
d = eval(d)
r.close()
f = file('dictionary.txt', 'w')
......
pickle.dump(d, f)
```

---

### Post by simeon87 on 2011-05-12
The following code writes a dictionary to file, using pickle, and reads it using pickle:

```
import pickle

d = {"Test": "Foo", 1: 2}
f = file('dictionary.txt', 'w')
pickle.dump(d, f)
f.close()
r = open('dictionary.txt', 'r')
d = pickle.load(r)
r.close()
print d
```

When you use pickle.load, it already constructs the dictionary.

Make sure dictionary.txt doesn't contain some incorrect data. If necessary, just remove it manually and dump the dictionary again to the file.

---

### Post by cgroza on 2011-05-12
> **CoffeeRain said:**
> OK,

```
r = open('dictionary.txt', 'r')
d = pickle.load(r)
d = eval(d)
r.close()
f = file('dictionary.txt', 'w')
......
pickle.dump(d, f)
```
Why do you use eval on it? d is already a dictionary instance. I think you do not understand how serialization works.
Pickle does not return the content of the file. Pickle reads the file and gives you the saved instance of the object it contained. So, when you did pickle.load, d turned to a dictionary instance.

You were trying to eval a dictionary object.

---

### Post by CoffeeRain on 2011-05-13
I'm now getting a KeyError: '{' and sometimes " ' "

---

### Post by cgroza on 2011-05-13
> **CoffeeRain said:**
> I'm now getting a KeyError: '{' and sometimes " ' "
Did the code change since post #16?

---

### Post by CoffeeRain on 2011-05-13
Yes. I took the eval(d) out.

```
r = open('dictionary.txt', 'r')
d = pickle.load(r)
r.close()
f = file('dictionary.txt', 'w')
.......
pickle.dump(d, f)
```

---

### Post by cgroza on 2011-05-13
> **CoffeeRain said:**
> Yes. I took the eval(d) out.

```
r = open('dictionary.txt', 'r')
d = pickle.load(r)
r.close()
f = file('dictionary.txt', 'w')
.......
pickle.dump(d, f)
```
Did you remove the dictionary.txt after you applied the fix? Chances are that you are loading the corrupt version again.

---

