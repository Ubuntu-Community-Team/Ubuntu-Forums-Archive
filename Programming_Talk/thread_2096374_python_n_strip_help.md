---
title: "python \n strip help"
date: 2012-12-19
forum: Programming Talk
---

### Post by DTSDeveloper on 2012-12-19
Hi everybody! This is my first post on this forum. I've been on other forums before so I'm aware of the general rules but if i break one (unknowingly) please dont take offense and let me know. Heres my question is, im trying to read in lines of a file which is working, but i cant strip the newline from the input. ive tried strip('\n') rstrip('\n') but it still has the '\n'. as a side note i am currently on a mac running i think python 5 with the default interpreter. i know this is a linux forum, but i am a linux hacker at heart and just havent had a chance to install my live ubuntu disc.

---

### Post by Vaphell on 2012-12-19
doesn't mac use \r? either way, i think strip() without params should do

---

### Post by DTSDeveloper on 2012-12-19
yes i forgot to mention that i tried ("\r\n"). and thanks for the suggestion ill try it

---

### Post by DTSDeveloper on 2012-12-19
i tried just .strip, but it didnt work. is there anything else i can do

---

### Post by steeldriver on 2012-12-19
All these work for me - this is 2.7.3 on Win64 fwiw

```
>>> s = "abcd\n"
>>> print s
abcd

>>> print s.strip('\n')
abcd
>>> 
``````
>>> s = "abcd\n"
>>> print s
abcd

>>> print s.strip()
abcd
>>> 

``````
>>> s = "abcd\nefg"
>>> print s
abcd
efg
>>> print s.replace('\n','')
abcdefg
>>>
```

---

### Post by DTSDeveloper on 2012-12-19
what if i post my code?

---

### Post by steeldriver on 2012-12-19
Posting code fragments is positively encouraged! so long as it's not 100s of lines obviously - if you could please enclose it between [CODE] tags as well like I did above (select the text and use the # button in the post editor)

---

### Post by Vaphell on 2012-12-19
try printing *list(yourstring)*, you will get a list of characters and you will know what's there.

```
$ python -c 'x="a\n\r\n\r"; print list(x), list(x.strip())'
['a', '\n', '\r', '\n', '\r'] ['a']
```

---

### Post by DTSDeveloper on 2012-12-19
thanks for the help everybody! i would like to thank steeldiver especially for the idea. i figured out the problem (via some testing in the interactive console); for some reason on my interpreter it doesnt keep the newline stripped as is seen in the picture. so i just have to manually strip it every time but ill also try line = line.strip() which might work

---

### Post by steeldriver on 2012-12-19
I think maybe you want to assign the result of the strip() back to the variable? otherwise you are just seeing a temporary string

```
>>> s = "abcd\n"
>>> print s
abcd

>>> print s.strip()
abcd
>>> print s    # still "abcd\n"
abcd

>>> s = s.strip()
>>> print s    # now has the modified value
abcd
>>> 
```

---

### Post by DTSDeveloper on 2012-12-19
yeah im sorry if i didnt make that clear. so your last line is what i have to do for a permanent change. if i just do string.strip(), the line isnt permanent

---

### Post by Vaphell on 2012-12-20
yes, strip() returns a string derived from the original, but you have to explicitly assign it to some variable to store it (original will do), otherwise it's lost.

x=1
x+1
it's the same situation. You will add 1 to x, but without assigning it back to x that operation is meaningless.
x=x+1

---

