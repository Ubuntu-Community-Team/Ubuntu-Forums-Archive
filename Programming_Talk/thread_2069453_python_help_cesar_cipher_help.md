---
title: "python help cesar cipher help"
date: 2012-10-10
forum: Programming Talk
---

### Post by snowlizard31 on 2012-10-10
I'm trying to make encryptor and decryptor that encrypts a message into number and vice versa using a dictionary but I'm stuck trying to get back the message in it's entirety, can someone help? 
```

tranlation_dict = { 'a':1, 'b':2,'c':3, 'd':4,'e':5,'f':6,'g':7,'h':8,'i':9,'j':10,'k':11,
'l':12,'m':13,'n':14,'o':15,'p':16,'q':17,'r':18,'s':19,'t':20,'u':21,'v':22,'w':23,
'x':24,'y':25,'z':26}

message = raw_input()
translated = ' '
for letter in list(message):
    translated =  tranlation_dict[letter]
print translated 

```

This only prints out the last letter of message and I can't seem to figure out how to make it print all the letter

---

### Post by Vaphell on 2012-10-10
indentation. python is sensitive to that.
all lines of loop body need to be aligned and you got *print translated* starting at the top level. That means it doesn't belong to the loop but is after the loop so it is executed once and the variable holds the last value.

---

### Post by snowlizard31 on 2012-10-10
I put the print statement out of the loop because I wanted to see if the for loop would return translated with all the letters translated into number but it only returns the last letter.

---

### Post by Bachstelze on 2012-10-10
The for loop doesn't return anything, it is not a function.

---

### Post by snowlizard31 on 2012-10-10
> 
The for loop doesn't return anything, it is not a function.     
I tried putting the code in a function but when a ran the code it didn't print anything
for translated

```

message = raw_input()
translated = ''

def tranlate(message):
    for letter in list(message):
        translated = tranlation_dict[letter]
    return translated

print translated 

```Here's something else I've tried that didn't work
```

message = raw_input()
translated = []

def tranlate(message):
    for letter in list(message):
        translated.append(tranlation_dict[letter])
    return translated

print translated 

```

---

### Post by lisati on 2012-10-10
It's usually not sufficient to 'def' a function: you need to call the function and put the result(s) somewhere. As your code stands, your function won't get called, and variable translated won't change.

---

### Post by Vaphell on 2012-10-10
it does translate all letters, but you don't do anything with the result.
message=abc
loop:
  letter=a -> trans=1 (don't print)
  letter=b -> trans=2 (don't print)
  letter=c -> trans=3 (don't print)
print trans=3

in other words you translate everything silently and print only last recorded value. If you moved print into the loop you would get all numbers.

In case you want to store all the numbers in a tidy list printed after the loop, you need to create one and append trans to it, eg
```
translated = []
for letter in list(message):
    translated.append( tranlation_dict[letter] )
print translated
```
i think you should add space to your dictionary, not being able to type words sucks ;-)

edit: i see the thread has seen a lot of action since i started typing :)

---

### Post by snowlizard31 on 2012-10-10
> 
t's usually not sufficient to 'def' a function: you need to call the  function and put the result(s) somewhere. As your code stands, your  function won't get called, and variable translated won't change. 	


Ah I forgot to call the function. I just added that but I'm still getting nothing in return

vaphell I tried it with the code that you posted and It worked thank you!! :)

---

