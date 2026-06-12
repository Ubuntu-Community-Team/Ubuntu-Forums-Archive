---
title: "python - get any .mp3 file in directory"
date: 2009-05-29
forum: Programming Talk
---

### Post by prem1er on 2009-05-29
New to python.  I have a script I'm working on and I'm using,

```
os.chdir()
```

to move into a specific directory.  Once in that directory I want to pull one of the .mp3 files in the directory and store it in a variable.  How can this be achieved?  Thank you.  

edit: to specify, I only need the ID3 tag information off of one of the .mp3.  If the ID3 info does not exist on the random .mp3 I'm going to assume it doesn't exist on any of them.

---

### Post by matmatmat on 2009-05-30
How about this?
```

for root, dirs, files in os.walk(path):
   for f in files:
       filename = os.path.join(root, f)
       if filename.endswith('.mp3'):
           #do something

```

To randomize you could do something like this:
```

count = 0
for root, dirs, files in os.walk(path):
   for f in files:
       filename = os.path.join(root, f)
       if filename.endswith('.mp3'):
           count += 1
rand = randint(1,count)
count = 1
for root, dirs, files in os.walk(path):
   for f in files:
       filename = os.path.join(root, f)
       if filename.endswith('.mp3'):
           if count == rand:
               #do something to filename
           else:
               count += 1

```
(messy)

Have a look at [this]("http://id3-py.sourceforge.net/") for id3 tags

---

### Post by ghostdog74 on 2009-05-30
if you know the directory of where your mp3 files is stored, and you know the file name, its just a matter of giving that filename to your ID3 tag retrieval tool.
```

# mp3info <options> <inputfile> 

```

---

### Post by prem1er on 2009-05-30
@mat - Than you. I will look into your solution and let you know.

@ghost - Thank you, but that is the problem. I will be getting new albums every so often and I want a dynamic way to pull out a file name from the directory.

---

### Post by ghostdog74 on 2009-05-30
> **prem1er said:**
> 
@ghost - Thank you, but that is the problem. I will be getting new albums every so often and I want a dynamic way to pull out a file name from the directory.
```
find /path -type f -iname "filename*mp3"
```

---

