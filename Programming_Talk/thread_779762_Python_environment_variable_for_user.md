---
title: "Python environment variable for user?"
date: 2008-05-03
forum: Programming Talk
---

### Post by ecs_pf5 on 2008-05-03
I am opening a file to write

filetosave = open(filename, 'wb')

..and that line seems to save it in the user's home directory.

I wanted to place the file on the user's /home/Desktop

so is 

filetosave = open(/Desktop/filename, 'wb')

okay, or should I be accessing some kind of environment variable?

(it seems to give me an error: 'Error: unable to open "/Desktop/foo.extension" for writing.')

---

### Post by tseliot on 2008-05-03
it should be ```
Desktop/filename
``` instead of ```
/Desktop/filename
```

---

### Post by ecs_pf5 on 2008-05-03
I was playing about with os.environ['HOME'] when you posted back - it works but for some reason, makes the Desktop flash and jump about, like an old ZX81 :mad:

(the commented out bit, below..)

```

        try:
            #video_filename = os.environ['HOME'] + "/Desktop/" + video_filename
            video_filename = "Desktop/" + video_filename
            video_file = open(video_filename, 'wb')

```

your suggestion - just plain Desktop/filename - works great, thanks :)

---

### Post by tseliot on 2008-05-03
It is usually better to use os.environ['HOME'] so that the result of your script does not depend on the place from which you're running the script ;)

---

### Post by ssam on 2008-05-03
the os.path module is good if you want to deal with paths in a robust cross platform way.

there is an expanduser() function, which can do what you want.

[http://docs.python.org/lib/module-os.path.html](http://docs.python.org/lib/module-os.path.html)

---

### Post by Martin Witte on 2008-05-03
> **ecs_pf5 said:**
> 
```

        try:
            #video_filename = os.environ['HOME'] + "/Desktop/" + video_filename
            video_filename = "Desktop/" + video_filename
            video_file = open(video_filename, 'wb')

```


You could consider the os.path functions to generate a pathname, e.g.
```
video_filename = os.path.join(os.path.expanduser('~'), 'Desktop', video_filename)
```

---

### Post by ecs_pf5 on 2008-05-04
Thanks folks, I'll look at those ideas because when I tried to build my program on Windows (via py2exe), I discovered Windows doesn't set a HOME variable by default.. so build errors happen.

I ended up with 

```

        try:
            userdesktop = os.environ['HOME'] + "/Desktop/"
            # for linux

        except KeyError:
            userdesktop = os.environ['USERPROFILE'] + "\\Desktop\\"
            # for microsoft

```which sort of works but maybe I can use os.path.join / expanduser() to do it a better way

---

### Post by Martin Witte on 2008-05-04
According to the [documentation]("http://docs.python.org/lib/module-os.path.html") and other [sources]("http://www.diveintopython.org/file_handling/os_module.html") os.path.expanduse('~') should work on windows, I don't have Windows at hand now to test it.

---

