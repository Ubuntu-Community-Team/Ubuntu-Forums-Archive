---
title: "PYTHON: how to find the newest file in a directory and open it with cat"
date: 2010-07-07
forum: Programming Talk
---

### Post by leahk on 2010-07-07
i am trying to first identify the last file added to the directory and then open it with cat.


r=commands.getoutput('ls -ct1 | head -1')

print r

os.system('cat r')



if i wrote os.system(cat 'name of file') it works but not with the variable

??

---

### Post by xb12x on 2010-07-07
Keep in mind that I'm currently learning Python myself:

c = 'cat'
x = c + ' ' + r
os.system(x)

---

### Post by schauerlich on 2010-07-07
os.system is evil.

```
filelist = os.listdir(os.getcwd())
filelist = filter(lambda x: not os.path.isdir(x), filelist)
newest = max(filelist, key=lambda x: os.stat(x).st_mtime)
```

"newest" will be a string with the name of the last modified file. You can then open it just like you would anything else.

---

### Post by leahk on 2010-07-07
the code is printing out the .pyc file....not the.py??

---

### Post by schauerlich on 2010-07-07
> **leahk said:**
> the code is printing out the .pyc file....not the.py??

Well, the .pyc file is created when the .py file is run, so it's going to be newer. You can manually filter out specific file extensions. Look into the "endswith" method of the string class, and look at the line using "filter".

---

### Post by geirha on 2010-07-08
And then, instead of running os.system('cat...'), do the "cat" with python.

---

### Post by schauerlich on 2010-07-08
> **geirha said:**
> do the "cat" with python.

[http://grab.by/grabs/a921b5c18ce82835b213355fcd69b8d0.png](http://grab.by/grabs/a921b5c18ce82835b213355fcd69b8d0.png)

Am I doing it right?

---

### Post by geirha on 2010-07-09
> **schauerlich said:**
> [http://grab.by/grabs/a921b5c18ce82835b213355fcd69b8d0.png](http://grab.by/grabs/a921b5c18ce82835b213355fcd69b8d0.png)

Am I doing it right?

Yes, that's exactly what I meant :)

---

