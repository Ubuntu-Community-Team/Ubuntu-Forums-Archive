---
title: "Help removing file extensions from filename list"
date: 2007-11-08
forum: Programming Talk
---

### Post by jondecker76 on 2007-11-08
Hello

I have a list of filenames filled by os.listdir()

How can I remove the file extensions from this list?
I was looking at os.path.splitext() but it doesn't work on lists, and it returns a list of both the filename and the extension...

Any hints?

thanks,

Jon

---

### Post by jondecker76 on 2007-11-08
Hello again,

I have figured out a way to do it, but I feel as if I am way overcomplicating it (though it works)..  Here is the ugly version I came up with.. Can someone critique this code and show me a better way to do it?

```

#Get a lits of file names
filenames = os.listdir('/home/jondecker76/ROMS/TG16/')
#Now remove the file extensions			
i = 0

for thisItem in filenames:
     filenames[i] = os.path.splitext(thisItem)[0]
     i=i+1

#Lets see how they look	
print filenames

```

---

### Post by cwaldbieser on 2007-11-09
```

files = os.path.listdirs('.')
files = [os.path.splitext(x)[0] for x in files]

```

---

### Post by jondecker76 on 2007-11-09
I knew there had to be a more elegant way -  thank you!

---

