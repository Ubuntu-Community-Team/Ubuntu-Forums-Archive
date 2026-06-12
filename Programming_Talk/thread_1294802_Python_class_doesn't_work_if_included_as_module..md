---
title: "Python class doesn't work if included as module."
date: 2009-10-18
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-18
ID3Reader.py
```
import ID3Data

song = ID3("/home/user/song.mp3")

```

ID3Data.py
```
class ID3:

    def __init__(self, file):
        print "File:", file
```

```
NameError: name 'ID3' is not defined
```

What's wrong ?

---

### Post by NoaHall on 2009-10-18
Error comes from running ID3Data.py or ID3Reader.py? It works for me using python from terminal - haven't tried using files yet though.

---

### Post by OpenGuard on 2009-10-18
From ID3Reader ( ID3Data is meant to be a module ).

---

### Post by NoaHall on 2009-10-18
```

import ID3Data
from ID3Data import *

song = ID3("/home/user/song.mp3")

```
Try that

---

### Post by Bachstelze on 2009-10-18
song = ID3Data.ID3("/home/user/song.mp3")

---

### Post by NoaHall on 2009-10-18
Why did you delete my posts and my correct answer?

---

### Post by OpenGuard on 2009-10-18
Thank you, tough, it resulted in a new error ..

ID3Reader.py
```
from ID3Data import *

song = ID3("/home/user/song.mp3")
ID3.readData()
```ID3Data.py
```
class ID3:

    def __init__(self, file):
        self.file = file
        
    def readData(self):
        print "Reading .."
``````

[COLOR=Red]TypeError: unbound method readData() must be called with ID3 instance as first argument (got nothing instead)[/COLOR]
```Any ideas ?

---

### Post by Bachstelze on 2009-10-18
> **NoaHall said:**
> Why did you delete my posts and my correct answer?

Your answer was not correct.

---

### Post by OpenGuard on 2009-10-18
> **Bachstelze said:**
> Your answer was not correct.

It was correct ( at least to some point ), not to mention the fact that you've no rights to do what you just did. Sad ..

---

### Post by Bachstelze on 2009-10-18
> **OpenGuard said:**
> Thank you, tough, it resulted in a new error ..

ID3Reader.py
```
from ID3Data import *

song = ID3("/home/user/song.mp3")
ID3.readData()
```ID3Data.py
```
class ID3:

    def __init__(self, file):
        self.file = file
        
    def readData(self):
        print "Reading .."
``````

[COLOR=Red]TypeError: unbound method readData() must be called with ID3 instance as first argument (got nothing instead)[/COLOR]
```Any ideas ?

1) **Do not** use [font=monospace]from module import *[/font]. Doing so is bad practice, as it will pollute your namespace.

2) 

```
import ID3Data

song = ID3Data.ID3("/home/user/song.mp3")
song.readData()
```

---

### Post by OpenGuard on 2009-10-18
Thank you - works like a charm :) Regarding "bad practices" - not an easy task for a beginner.

---

### Post by NoaHall on 2009-10-18
How, in what sense was it incorrect(I would like to know, I don't know much python), and on what grounds does that give you permission to delete my posts? I've submitted a complaint. You seem to have it out for me, when I'm not doing anything other than what I should be.

---

### Post by Can+~ on 2009-10-18
> **Bachstelze said:**
> 1) **Do not** use [font=monospace]from module import *[/font]. Doing so is bad practice, as it will pollute your namespace.

2) 

```
import ID3Data

song = ID3Data.ID3("/home/user/song.mp3")
song.readData()
```

It's a bad practice when it isn't necessary. But if is a class you made, or have a name that will probably not clash with others, and you'll probably use it a lot, then it's completely acceptable.

When working with Opengl, for example, it's better to use that, otherwise the whole code will be filled with "OpenGL.DoStuff()".

And doesn't give you the right to delete a response, anyway.

---

### Post by Bachstelze on 2009-10-18
> **Can+~ said:**
> It's a bad practice when it isn't necessary. But if is a class you made, or have a name that will probably not clash with others, and you'll probably use it a lot, then it's completely acceptable.

When working with Opengl, for example, it's better to use that, otherwise the whole code will be filled with "OpenGL.DoStuff()".

And doesn't give you the right to delete a response, anyway.

True, but someone as the OP who's not familiar with the language could easily make that mistake of creating objects whose names will clash with others. One could argue that one learns by making such mistakes, but I think it's better to stay on the safe side. The OP will have plenty of time to learn about that.

---

### Post by nvteighen on 2009-10-19
> **Bachstelze said:**
> Your answer was not correct.

That's not a reason to use mod powers and delete posts, you know. It was no harmful information nor anything against the CoC.

---

### Post by ajackson on 2009-10-19
> **Bachstelze said:**
> True, but someone as the OP who's not familiar with the language could easily make that mistake of creating objects whose names will clash with others. One could argue that one learns by making such mistakes, but I think it's better to stay on the safe side. The OP will have plenty of time to learn about that.
Then you point out why that approach **can** be a bad way of solving the problem rather than deleting the post in question or are all posts to be vetted by yourself to ensure they solve it the way you would?

---

