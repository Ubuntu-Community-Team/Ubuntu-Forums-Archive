---
title: "How to check if variable is a string (python)"
date: 2008-09-07
forum: Programming Talk
---

### Post by Sagekilla on 2008-09-07
Hello all, I'm new to python and I was wondering how I could check if the variable I gave was a string. I need a solution that's very short, nothing long and complex (I don't need to use try, except, continue, etc. That isn't applicable for me right now)

Basically what I have is:

```
n = Input("enter number ");
for x in range(n):
  print "Hello world!"
```


I need to be able to check whether n is a number or not though. Thanks!

---

### Post by Wybiral on 2008-09-07
You can see if something is an instance of something using 'isinstance' such as:

```
[color=#000080]**>>> **[/color][color=#008000]isinstance[/color]([color=#BA2121]'hello'[/color], [color=#008000]str[/color])
[color=#808080]True
[/color][color=#000080]**>>> **[/color][color=#008000]isinstance[/color]([color=#666666]7[/color], [color=#008000]int[/color])
[color=#808080]True
[/color][color=#000080]**>>> **[/color][color=#008000]isinstance[/color]([color=#666666]1.5[/color], [color=#008000]float[/color])
[color=#808080]True
[/color]
```

But I suggest in this case you not use 'input', and use 'raw_input' instead. Then use the 'int' function, which raises an exception if it can't be returned as an int.

```
x [color=#666666]=[/color] [color=#008000]raw_input[/color]()
[color=#008000]**try**[/color]:
    y [color=#666666]=[/color] [color=#008000]int[/color](x)
[color=#008000]**except**[/color]:
    [color=#008000]**print**[/color] [color=#BA2121]'cannot cast to int'[/color]

```

---

### Post by Sagekilla on 2008-09-07
I just read the python documentation, and from I understand raw_input will convert what I enter into a string, unless I'm understanding this wrong.

I have another question: If I do the following, it seems to fail completely when it's anything but a number. I get the same result as if there were no isinstance.

```

def main():
  x = raw_input("Enter number ");
  if isinstance(x,int):
    print x, "is a number"

```

---

### Post by LaRoza on 2008-09-07
> **Sagekilla said:**
> I just read the python documentation, and from I understand raw_input will convert what I enter into a string, unless I'm understanding this wrong.

I have another question: If I do the following, it seems to fail completely when it's anything but a number. I get the same result as if there were no isinstance.


Python is stongly typed. Anything can be in a string, including numbers, but they are strings. You can convert them to integers and test them using the various string functions.

[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

---

### Post by Sagekilla on 2008-09-07
Thank you all, I had to learn the hard way that Try, except was the best way.

---

### Post by Sinkingships7 on 2008-09-07
You can test it as it comes as well.
```
[color=#008000]**try**[/color]:
    n [color=#666666]=[/color] [color=#008000]int[/color]([color=#008000]raw_input[/color]([color=#BA2121]"Number: "[/color]))
[color=#008000]**except**[/color]:
    [color=#008000]**print**[/color] [color=#BA2121]"Err: Input not integer."[/color]

```

---

### Post by true_friend on 2008-09-07
A regex can also be used to test whether the input is according to criteria or not.

---

### Post by LaRoza on 2008-09-07
> **true_friend said:**
> A regex can also be used to test whether the input is according to criteria or not.

That would be overkill. The built in methods (isdigit(), for example) is more than enough, even without exception handling.

---

### Post by jgeewax on 2008-09-14
> **Wybiral said:**
> You can see if something is an instance of something using 'isinstance' such as:

```
[color=#000080]**>>> **[/color][color=#008000]isinstance[/color]([color=#BA2121]'hello'[/color], [color=#008000]str[/color])
[color=#808080]True
[/color][color=#000080]**>>> **[/color][color=#008000]isinstance[/color]([color=#666666]7[/color], [color=#008000]int[/color])
[color=#808080]True
[/color][color=#000080]**>>> **[/color][color=#008000]isinstance[/color]([color=#666666]1.5[/color], [color=#008000]float[/color])
[color=#808080]True
[/color]
```



I think it might be important to mention that if you are dealing with things other than str's (ie, unicode), you should use isinstance(val, basestring):

```

>>> isinstance('abcd', str)
True
>>> isinstance('abcd', basestring)
True
>>> isinstance(u'abcd', str)
False
>>> isinstance(u'abcd', basestring)
True

```

---

### Post by zobayer1 on 2010-12-13
thanks ... ...
btw, I am facing problems like reading input with raw_input or input is slow. how can I speed it up?

---

### Post by Tony Flury on 2010-12-13
> 
thanks ... ...
btw, I am facing problems like reading input with raw_input or input is slow. how can I speed it up? 

if you are waiting for input from the user - does it matter that the function may take a few miliseconds ? I would guess that the actual human typing the input and hitting return would be far slower than calling the actual function.

---

### Post by ssam on 2010-12-13
> **Sagekilla said:**
> I just read the python documentation, and from I understand raw_input will convert what I enter into a string, unless I'm understanding this wrong.


you are thinking the wrong way around.

when you type something it is a string of characters (look up ascii). so if you type '10', then it is a '1' character followed by a '0' character. it takes extra interpretation to make this in to a number. raw_input just leaves the input raw, i.e. as a string.

if you want a number then you need to use int() or float() to convert the string. the safe way to do this is to try it and handle the error if it fails. see Sinkingships7's example.

---

