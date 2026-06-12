---
title: "Python and ascii table help"
date: 2008-02-19
forum: Programming Talk
---

### Post by sp0nge on 2008-02-19
I am trying to learn to program for a long time with out any formal instruction. I have done pretty well, but I've come to this road block. 

I am trying to code a (very) basic decryption program in python. Ideally, I want to be able to enter a string and have it decrypted accordingly. I'm trying to avoid manually assigning each ascii character a value, is there away to import something like this ascii table ([http://www.lookuptables.com/asciifull.gif)?](http://www.lookuptables.com/asciifull.gif)?)

---

### Post by LaRoza on 2008-02-19
The built in function for getting the asci code is "ord()".

```

for letter in "string":
    print ord(letter)

```

Here is the link, yours includes the )? : [http://www.lookuptables.com/asciifull.gif](http://www.lookuptables.com/asciifull.gif)

---

### Post by sp0nge on 2008-02-19
Perhaps I'm not looking at this correctly. Let me be a little more specific. 

The encryption is more than simple. I am spending more time to understand how to program it than I would to actually do it by hand but I really want to understand this!  

Ideally, the string:
```
aaaaa
```
 
will return the string:
```
abcde
```

I was thinking that by assigning a value to each character and adding one to the input would work, but I don't seem to understand any way to do this except manually. Please tell me I'm wrong.

---

### Post by LaRoza on 2008-02-19
> **sp0nge said:**
> 
I was thinking that by assigning a value to each character and adding one to the input would work, but I don't seem to understand any way to do this except manually. Please tell me I'm wrong.

I haven't studied cryptography, sorry.

---

### Post by pmasiar on 2008-02-19
> **sp0nge said:**
> I am trying to learn to program for a long time with out any formal instruction. 

Which book do you use? You may want to try couple different books, so you can see the same issue explained by different authors. Wiki in my sig has many free books for beginners.

There are many websites with tasks and solutions, I like PythonChallenge: they have 32 levels, solving level unlocks the next level. And forum to discuss and get hints for each level.

---

### Post by bobbocanfly on 2008-02-19
> **sp0nge said:**
> I was thinking that by assigning a value to each character and adding one to the input would work, but I don't seem to understand any way to do this except manually. Please tell me I'm wrong.

As in a rotation algorithm (Casesar shift) where A would become B and X become Y? 

They are fairly trivial to write, the major problem though is 'falling off the end of the alphabet'. In ASCII the character one value up from 'Z' is '[' while in your script you would want it to go back to 'A'.

I wrote a Python [ROT-13]("http://en.wikipedia.org/wiki/Rot13") script i can post if you want some pointers?

---

### Post by amingv on 2008-02-19
Maybe you can use something like this?

[PHP]#Module: coding.py

def encode(string):
    ''' Encodes a string by incrementing
        each character by its index number.

        Usage:
            >>> a = encode('aaaaa')
            >>> print a
            abcde
            >>> '''
    newString = ''
    for i in range(len(string)):
        char = string[i]
        newString += chr((ord(char) + i))
    return newString

def decode(string):
    ''' Decodes a string by decrementing
        each character by its index number.

        Usage:
            >>> a = decode('abcde')
            >>> print a
            aaaaa
            >>> '''
    newString = ''
    for i in range(len(string)):
        char = string[i]
        newString += chr((ord(char) - i))
    return newString
[/PHP]

Of course, this would be just the basis, it still needs tweaking (for example, it's easy to get chr() outside of range(256) if you use a sufficiently long string), but I'm sure you can move over from there...

---

### Post by sp0nge on 2008-02-19
> Which book do you use? You may want to try couple different books, so you can see the same issue explained by different authors. Wiki in my sig has many free books for beginners.

There are many websites with tasks and solutions, I like PythonChallenge: they have 32 levels, solving level unlocks the next level. And forum to discuss and get hints for each level.

I have read Python for Dummies, A Byte of Python, and pretty much just kinda toyed with the source code from there. It helped me and I feel I understand the very basics, but I know I've just scratched the surface. Thanks for the advice on PythonChallenge. I'll most deffinately be looking into this. 

> I wrote a Python ROT-13 script i can post if you want some pointers?

I'd love to see it. Any little bit helps. Thanks in advance.!

and amingv, thanks for the input. I'll give it a shot and let you know where I end up with that snipet.

---

### Post by amingv on 2008-02-19
The best guide (if you want to "formalize" yourself) comes from the [Master himself]("http://docs.python.org/tut/tut.html"), in fact A Byte of Python recommends to read the docs in the official webpage, if I recall correctly.
It looks like "encoding" it's a popular subject in Python, I was too working on an encoding program that worked on numbers generated from the fibonacci sequence (not the fibonacci sequence itself). But I lost interest in it as it served me no purpose...

---

### Post by bobbocanfly on 2008-02-19
> **sp0nge said:**
> I'd love to see it. Any little bit helps. Thanks in advance.!

and amingv, thanks for the input. I'll give it a shot and let you know where I end up with that snipet.

Amingv's script looks more like what you want but my Rot-13 script can be found at [http://codebrowse.launchpad.net/~bobbo/+junk/random/annotate/bobbocanfly%40gmail.com-20080219204655-x6867hi2uy1ch0zo?file_id=rot13.py-20080207190817-0opsfcahkq0fwnv0-4](http://codebrowse.launchpad.net/~bobbo/+junk/random/annotate/bobbocanfly%40gmail.com-20080219204655-x6867hi2uy1ch0zo?file_id=rot13.py-20080207190817-0opsfcahkq0fwnv0-4)

---

### Post by sp0nge on 2008-02-19
I have read a lot on the subject, and have made small programs modeled after various source code I've found. I have not found anything that answers my question, which brought me to the forum. 

Maybe what I'm looking for isn't possible. Maybe I have to do this the long way. Who knows, but thanks for the input none the less!

Well I've figured it out- simple as pie!

```
 
for i in 'foobar':
   print ord(i)

```

---

