---
title: "[Python] join file to path confusion"
date: 2010-05-02
forum: Programming Talk
---

### Post by OgreProgrammer on 2010-05-02
This variation of my code works.
```

workfile = '/home/alan/pythonprojects/movefiles/start/Plain text document.txt'
shutil.copy(workfile, '/home/alan/pythonprojects/movefiles/dest')

```

however, if I do it like this, as I need to do, it doesnt work. I actually want to join a variable filename to the path. I cant make it work. Something is escaping me.

```

workfile = '/home/alan/pythonprojects/movefiles/start/'.join('Plain text document.txt')
shutil.copy(workfile, '/home/alan/pythonprojects/movefiles/dest')

```

I sure could use a helpful tip. It looks right according to the documents for shutil, and that is the correct way to join strings.

---

### Post by OgreProgrammer on 2010-05-02
So it seems that the proper way is with +, but with real strings it works best with .join().

So thats good to know.

I have my strings all made up, but the files wont copy. 

```

    for root,dirs,files in os.walk(source):
        for f in files:
            shutil.copy(source+f, destin)

```

The file names print right, but nothing happens. Yet if I fill in the path names by hand, it works fine. What gives?

---

### Post by OgreProgrammer on 2010-05-02
So I am a bit of an idiot. The problem was that my destination folder string was slightly different from the real folder. 

But its fixed.

Some knowledge has been accumulated, but I feel dumber all the same. :D

Have a good morning. I'm going to.

---

### Post by kostkon on 2010-05-02
Always use [os.path.join()]("http://docs.python.org/library/os.path.html#os.path.join") to join paths.

---

