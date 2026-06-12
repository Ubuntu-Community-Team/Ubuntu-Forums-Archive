---
title: "Python Vigenere"
date: 2011-11-17
forum: Programming Talk
---

### Post by maxpol on 2011-11-17
Hey guys, you were awesome last time I needed help, so I came back for more :) . 

Still on the topic of Python, the assignment is to write a Vigenere encryption only program. This is what I have so far and it sort of works.
```

def getInput():
    data = input("Please enter your string: ")
    key = ""
    while 1:
        key = input("Please enter an alphabetic key: ")
        if key.isalpha():
            return data,key
        else:
            print("That's not a valid input!")
def makekey(key_input,no_char):
    key = []
    i = 0
    x = 0
    while i < no_char:
        key.append(key_input[x])
        i = i + 1
        x = x + 1
        if x == (len(key_input)):
            x = 0
    return key
def giveNO(char):
    no = ord(char)
    return (no-ord('A'))
def giveCHAR(no):
    if no>=0 and no<=25:
        return chr(no+ord('A'))
    elif no>25:
        return chr(no+ord('A')-26)
    elif no<0:
        return chr(no+ord('A')+26)
def encode(key_input,data):
    key = makekey(key_input,len(data))
    i = 0
    enSTR = ""
    while i < len(data):
        if data[i] == " ":
            enSTR = enSTR + " "
        else:
            no = giveNO(data[i]) + giveNO(key[i])
            enSTR = enSTR + giveCHAR(no)
        i = i + 1
    print ("Result: %s"%enSTR)

def main():
    data, key = getInput()
    encode(key,data)
main()


```

The catch here is that it only works on UPPERCASE letters. But in my assignment, I need it to work for uppercase and lowercase at the same time, have it maintain the same case and be able to leave anything un-alphabetic as is. I still can't wrap my head around how to get it to do those functions, even after reading countless articles. Could someone steer me in the right direction please? 

Thanks!

---

### Post by Bachstelze on 2011-11-17
```
if letter is lowercase
   offset = ord("a")
else
   offset = ord("A")

result = ((ord(letter) - offset + ord(key_letter)) % 26)+offset
```

---

### Post by maxpol on 2011-11-17
> **Bachstelze said:**
> ```
if letter is lowercase
   offset = ord("a")
else
   offset = ord("A")

result = ((ord(letter) - offset + ord(key_letter)) % 26)+offset
```

Now, if I need to skip lets say a period, do I just set the offset to 0?

---

### Post by Bachstelze on 2011-11-17
Of course not because setting the offset to 0 will still modify the character (and you will get an ASCII character with code < 26, which will give you an unprintable character).

---

