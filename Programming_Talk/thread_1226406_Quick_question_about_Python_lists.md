---
title: "Quick question about Python lists"
date: 2009-07-29
forum: Programming Talk
---

### Post by tdrusk on 2009-07-29
I am trying to run this
```

# list of numbers
num = [0, 1, 2]

# list of letters
let = ['a', 'b', 'c']

# get code to convert
numword = [1, 2, 2]

# convert numbers
for x in range(3):
    for y in range(3):
        if num[x]==numword[y]:
            print let.index(x)
```

Why can't I print 
```
b
b
c
```

The error output is
```
    print let.index(num[x])
ValueError: list.index(x): x not in list
```

---

### Post by CptPicard on 2009-07-29
Well, it's pretty obvious... contents of variable "x" is not in the list "let". Are you thinking "let[x]"?

I'm also not quite sure what you're doing there... it seems to me the "num" array is completely redundant?

```

code = [1,2,2]
let = ['a','b','c']

for c in code:
    print let[c]

```

Is it that you're after?

---

### Post by benj1 on 2009-07-29
i maybe miss understanding what you are trying to do but wouldn't

```

let = ['a', 'b', 'c']
numword = [1, 2, 2]

for entries in numword:
    print let[entries]
```

or even
```

numword = [1, 2, 2]

for entries in numword:
    print chr(entries+97)

```
be simpler?

---

### Post by tdrusk on 2009-07-29
Thanks guys. I see my over-thinking now.

---

### Post by CptPicard on 2009-07-29
```

>>> [chr(x+97) for x in [1,2,2]]
['b', 'c', 'c']

```

:)

---

### Post by tdrusk on 2009-07-29
What about going the other way? From letters to numbers...
I tried this, but to no avail...
```
# list of letters
let = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', ' ']

# get code to convert
numword = [1, 2, 2]
word = ['h', 'e', 'l', 'l', 'o']

# convert numbers
for x in numword:
    print let[x]

# convert letters
for x in word:
    print let.index(word[(x+1)])
```

---

### Post by CptPicard on 2009-07-29
```

[ord(x)-96 for x in ['a','b','c']]

```

... assuming you're indexing by alphabetical order. Otherwise you need to look up indexes in a list or have a hash or something.

---

### Post by tdrusk on 2009-07-30
Actually I want to define my alphabet/numbers.
Now I made my own alphabet by doing this
```
# list of letters
let = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', ' ']

# list of numbers
num = [1,2,3,4,5,6,7,8,9,'~','!','@','#','$','%','^','&','*','(',')','-','=','+','Q','W','E','R']

# get code to convert
numword = [1, 2, 2]
word = ['h', 'e', 'l', 'l', 'o']

#convert numbers
for y in range(3):
    print let[numword[y]]
```

Now I can't figure out how to convert the word to numbers.

I tried 
```
# convert letters
for y in range(3):
    print num[word[y]]
```

but 
```
  Error
  print num[word[y]]
TypeError: list indices must be integers, not str
```

Any tips.

---

### Post by kpkeerthi on 2009-07-30
> **tdrusk said:**
> 
I tried 
```
# convert letters
for y in range(3):
    print num[[COLOR="Red"]word[y][/COLOR]]
```

but 
```
  Error
  print num[word[y]]
TypeError: list indices must be integers, not str
```

Any tips.

In your case, **word** is a list of strings. word[y] (highlighted) would return a string which cannot be used to index the list num.

---

### Post by benj1 on 2009-07-30
```
word = ['h','e','l','l','o']

for letter in word:
    print ord(letter)-96
```


or if you want a list
```
word = ['h','e','l','l','o']
li = [ord(letter)-96 for letter in word]
```

note that word could just be a straight string

what exactly are you trying to achieve ?

---

### Post by nvteighen on 2009-07-30
Er... maybe what you want is a dictionary? But I may be not getting what you want...

```

table = {'a' : 1, 'b' : 2, 'c' : 3} # Example

```

---

### Post by tdrusk on 2009-07-30
I finished the program. It works just as I like. :)
```

# filename: encoDecode.py
# purpose: encode/decode a string from/to a code
# author: tdrusk

# import sys is necessary for printing on same line without a space, as a ',' would do.
import sys

# Create a list of letters to convert to/from.
let = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', ' ', '.', ',', ':']

# Create a list of numbers to convert to/from.
num = ['1','2','3','4','5','6','7','8','9','~','!','@','#','$','%','^','&','*','(',')','-','=','+','Q','W','E','R', 'T', 'Y', 'U']

# The encode function uses the start object.
#   The for loop uses the length of start as the amount of times it will iterate.
#       start[y] is what is in the y spot of the start list.
#       let.index(start[y]) is the index of the string, start[y], in the let list.
#       num[let.index(start[y])] uses the index in the let list and passes it to the num list.
#       For example, start[y] = a. The let.index of start[y] is 1. 1 is then put in num[1], which declares finish as '1'.
#       sys.stdout.write(finish) prints the individual strings without a space or newline after them.
def encode(start):
    for y in range(len(start)):
        finish = num[let.index(start[y])]
        sys.stdout.write(finish)

# The decode function uses the start object
#   The for loop uses the length of start as the amount of times it will iterate.
#       start[y] is what is in the y spot of the  list.
#       num.index(start[y]) is the index of the string, start[y], in the num list.
#       let[num.index(start[y])] uses the index in the num list and passes it to the let list.
#       For example, start[y] = 1. The num.index of start[y] is 1. 1 is then put in let[1], which declares finish as 'a'.
#       sys.stdout.write(finish) prints the individual strings without a space or newline after them.
def decode(start):
    for y in range(len(start)):
        finish = let[num.index(start[y])]
        sys.stdout.write(finish)

# The Main function ties the necessary functions together
def main():
    print '\n\t\t\tEncoDecode'
    ed = str(raw_input('Encode or Decode?(e/d)\n>'))
    if ed in 'e':
        start = str(raw_input("Enter the text you want to encode\n>"))
# list(start) creates a list of the string previously input.
        start = list(start)
        encode(start)

    if ed in 'd':
        start = str(raw_input("Enter the code you want to decode\n>"))
# list(start) creates a list of the string previously input.
        list(start)
# Execute decode function 
        decode(start)

# Run main function.
main()

```**[EncoDecode: Encode and Decode a String]("http://tdrusk.livejournal.com/2158.html")**

---

