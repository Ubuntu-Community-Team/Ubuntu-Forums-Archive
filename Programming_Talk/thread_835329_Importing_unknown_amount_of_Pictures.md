---
title: "Importing unknown amount of Pictures?"
date: 2008-06-20
forum: Programming Talk
---

### Post by xelapond on 2008-06-20
I am writing a kinda photo-manager-ish program in Python, with the PyGlet OpenGL Binding.  My only question is, I can get a list of all the pictures in the pictures folder, but I don't know how to import them all and be able to address then, because there name could be anything.  I guess to clarify, I need to be able to import all the pictures, and be able to iterate over them.  My idea was to import them all, and have a list of the imported object, and iterate over that and check for collisions, but I don't know how I would import in the first place.

Thanks a ton, 

Alex

---

### Post by smartbei on 2008-06-20
What do you mean by (emphasis mine):
> 
I am writing a kinda photo-manager-ish program in Python, with the PyGlet OpenGL Binding. My only question is, I can get a list of all the pictures in the pictures folder, but I don't know how to import them all and be able to address then, **because there name could be anything**. I guess to clarify, I need to be able to import all the pictures, and be able to iterate over them. My idea was to import them all, and have a list of the imported object, and iterate over that and check for collisions, but I don't know how I would import in the first place.


What name could be anything? If you mean the filename, you could use os.walk to walk the folder and get all the pictures, or glob.glob to get a list of all the files matching a certain pattern.

---

### Post by xelapond on 2008-06-20
Yes, I am referring to file name.  I have no problem getting a list of files, but once I have it how do I run image_object = image.load('Filename') on all of them?  In other words, how do I import them all into a usable image object, that I can then manipulate.

Thanks, 

Alex

---

### Post by smartbei on 2008-06-20
Let's say you have a folder name stored in the variable 'folder'. How about this:
```

import os

## folder = directory name of images to be imported
files = os.walk(folder).next()[2]

```

How it works:
os.walk returns an iterator object that is meant to be looped over using for. Since We don't care about recursive folders, I just iterate once. Then, since os.walk returns a tuple with three things: the path to the current folder, a list of folders there, and a list of files, I take the third (which is the only one that interests me.

Then, you could do something like:
```

image_list = []
for filename in files:
    image_list.append(image.load(filename))

```

---

### Post by xelapond on 2008-06-20
Ah, Thanks!

I knew it was something like that, but I guess it never quite clicked that I could have a list of objects.  Wow, that changes everything.  

Thanks again!

Alex

---

