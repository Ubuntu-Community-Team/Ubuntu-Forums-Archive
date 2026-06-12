---
title: "Python - Caeser Cipher encryption function not working with string bigger than 1"
date: 2014-03-22
forum: Programming Talk
---

### Post by Yozuru on 2014-03-22
Hello good people, 

I have recently started to learn python and I am having trouble with a function. I am working on an encryption program that takes a key of a lower case letter and a message that is a string of lower case letters. Using this, I would add the key to each letter of the string. (which I have a bit of trouble doing). 

Here is a pastebin of what I have for my encryption function (which is the last function listed)

[HTML]http://pastebin.com/VzbSA35u[/HTML]

All of my other functions work fine except for the encryption.

Please excuse my English as it is not my first language. I am also a beginner so please explain as much as possible. Many thanks in advance for any help/advice. 

- Yozuru

This has been **RESOLVED**.

---

### Post by trent.josephsen on 2014-03-22
A couple of things stand out:
```
    m = str
```
Not sure what you meant here, but I'm pretty sure this wasn't it.
```
    cipherText = addchr(keyValue, m)
```
If you delete "m = str", this will encrypt the first character of the string **m** and put the result in **cipherText**. How are you going to get to the other characters of the plaintext?
```
    for i in cipherText:
        return cipherText
```
You can only return from a function once, so a simple return in a loop is not meaningful. Nevertheless, cipherText only ever has one character in it, so the loop could never execute a second time anyway.

---

### Post by Yozuru on 2014-03-22
Many thanks for the suggestions to work on. Using: cipherText = addchr(keyValue, m). I wanted to add the key with whatever string was input. for example:

encr('a', 'abc')

It would return back to abc since key 'a' = 0. 

Is there a way for me to do it this way since I am at a lost.

---

### Post by steeldriver on 2014-03-22
Here's a fairly pythonic way of doing it, I think

```

def encr(key, m):
    return ''.join([addchr(c,key) for c in m])

```

---

### Post by trent.josephsen on 2014-03-22
I'd lose the [ ] -- they just cause the characters to be collected in a list first, which has no advantage. str.join takes any iterable, so a plain generator is more Pythonic than a list comprehension.

Here's another solution, even less Pythonic but perhaps more readily understood:
```
def encr(key, m):
    result = ''
    for ch in m:
        result += addchr(ch, key)
    return result
```

---

### Post by Yozuru on 2014-03-22
Many thanks to the both of you! I am still learning .join so I am not so familiar with it yet. I'll already readjusted my function code with your suggestions and it works wonderful. 

You're example solution is really easily understood Trent, and you're a sweetheart for sticking through with me on this. I shall mark this as resolved. 

- Yozuru

---

