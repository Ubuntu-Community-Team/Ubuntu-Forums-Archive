---
title: "Python 3 make code faster"
date: 2017-01-05
forum: Programming Talk
---

### Post by kingpenguin on 2017-01-05
Ok at the moment I have a python 3 program. What I am trying to do is have a file open in the main block of code and have a function that will be able to write to this file. something like this
```

f = open('test.txt', 'a')

def write(word):
    f.write(word)

```
Dont get me wrong I know this will not work as is but it seems really dumb to keep opening a file over and over after every time the function is called. Because what i have at the moment is 
```

def write(word):
    with open('test.txt', 'a') as f:
        f.write(word)

```
but this function will be called a bunch and the 2nd way seems really bad for efficiency

---

### Post by kingpenguin on 2017-01-05
well the forum killed my spacing but hopefully you get the idea

---

### Post by coffeecat on 2017-01-05
> **rawrmonster2 said:**
> well the forum killed my spacing but hopefully you get the idea

I've edited your post to include BBCode code tags. If you want your spacing and formatting preserved, please use code tags - see here: [https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168). That's what they're there for.

---

### Post by The Cog on 2017-01-05
The thing to do is open the file, then do all the required work and writing inside the **with** block. Something like this perhaps:
```

with open('test.txt', 'a') as f:
    a = b = 1
    while a < 100:
        f.write(str(a) + "\n")
        a, b = b, a + b

```

---

### Post by Olav on 2017-01-09
Here's another thought, just pass the file handle:

```

def write(f, word):
    f.write(word)

f = open('test.txt', 'a')

write(f, 'hallo')
write(f, 'bye')
# whatever else

f.close()

```

---

### Post by kingpenguin on 2017-01-14
Wow I love this Idea. Thank you so much

---

