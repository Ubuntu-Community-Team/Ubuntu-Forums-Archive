---
title: "Can't Figure Out Where I Went Wrong..."
date: 2010-11-11
forum: Programming Talk
---

### Post by JeremiahS on 2010-11-11
Im working on an encryption program... Im teaching myself Python as i'm writing this code. Well after the two loops(which is where im figuring the problem is at) my "encrypted message is still the same... Im at a loss I just need some more "expert" advise. The confusing parts(well for me atleast) are all pretty well commented. Any help will be greatly appreciated... Heres the code. ohh and i dont get any error codes, just a returned unencrypted message.

[PHP]
#############################
#    Amnite Productions     #
# New Ideas To Old Problems #
# Advanced Caesarian Cypher #
#   Built On Python 3.1.2   #
#############################

def GetMode():
    while True:
        print('(E)ncrypt or (D)ecrypt?')
        Mode = input().lower()
        if Mode in 'e d encrypt decrypt'.split():
            return Mode
        else:
            print('\nPlease Enter Proper Choice!')

def GetKey():
    while True:
        Key = 0
        print('\nPlease Enter A 20 Digit Number...')
        print('** Do NOT use zeros!!!! EX-NAY ERO-ZAY! **')
        try:
            Key = int(input())
            if (len(str(Key)) == 20):
                return Key
            else:
                print('Please Enter A Valid Number!')
        except:
            print('Please Enter A Valid Number!')

def OpenFile():
    while True:
        print('\nPlease Enter The File Location...')
        print('** TXT, EDT, or ODT File Types **')
        MsgLoc = input()
        try:
            File = open(MsgLoc, 'r')
            return File
        except:
            print('Could Not Open File ' + MsgLoc + '!')

def Translate(Mode, Key, File):
    if Mode[0] == 'e':
        print('\nEncrypting....')
        Encrypt(Key, File)
    else:
        print('\nDecrypting....')
        Decrypt(Key, File)

def Encrypt(Key, File):
    Contents = File.read()
    Message = Contents
    a = 0
    b = 19
    Key = str(Key)
    #Loop for proccessing Key
    for z in range(10):
        KeySkip = int(Key[a]) #How many chars to skip b4 changing ord
        KeyIncrement = int(Key[b]) #How many spaces ord value moves
        LetterSkips = len(Contents)//KeySkip #How many letters will be changed
        c = -1
        #Loop for Skip/Increment
        for y in range(LetterSkips):
            # REMEMBER!! - ord(){32-126}*No /n, /t*
            #Focusing on ords 32-126 so if ord+Increment>126 set to 32
            c += KeySkip
            if (c > len(Message)):
                pass
            elif (Message[c] == ' ' or Message[c] == '    '):
                pass
#            elif (ord(Message[c]) + KeySkip > 126):
#                d = ord(Message[c])
#                d = 126 - d
            else:
                e = ord(Message[c])
                e += KeyIncrement
                Message[c] == chr(e)
                
        a += 1 #Move to next KeySkip number
        b -= 1 #Move to next KeyIncrement number
    print(Message)

def Decrypt(Key, File):
    Contents = File.read()
    Message = Contents
    print(Contents)

Mode = GetMode()
Key = GetKey()
File = OpenFile()
Translate(Mode, Key, File)
[/PHP]

---

### Post by Arndt on 2010-11-12
```
         Message[c] == chr(e)
```

does not do what you think, I think.

---

### Post by JeremiahS on 2010-11-12
Oops... I see. using the comparison instead of assignment. I hope im not the only one who looks over minscule stuff like that... Atleast now i get some error codes so i can push on.....

---

### Post by Reiger on 2010-11-12
Consider defining a functions to cypher/decypher individual characters, functions to cypher/decypher whole strings, and then master functions which control what parts of the source input get cyphered/decyphered.

A simple demo to show the idea:
```

#!/usr/bin/python

CYPHER_SHIFT=2
CYPHER_LOWER=32
CYPHER_UPPER=126

def cypher(c):
  i = ord(c)
  if (i >= CYPHER_LOWER and i<=CYPHER_UPPER):
    mod = CYPHER_UPPER-CYPHER_LOWER
    code= (i + CYPHER_SHIFT) % mod
    return chr(CYPHER_LOWER + code)
  else:
    return c

def cypher_str(s):
  return "".join(map (cypher,s))

print cypher_str("the quick brown fox jumps over the lazy dog")

```

You will notice that the actual algorithm is confined to one easy-to-understand & easy-to-use function, that applying the algorithm to a whole chunk of text is simple using the Python builtins and that you can avoid writing explicit loops quite nicely this way.

---

