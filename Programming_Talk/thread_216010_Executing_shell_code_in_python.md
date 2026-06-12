---
title: "Executing shell code in python"
date: 2006-07-14
forum: Programming Talk
---

### Post by rhipwell on 2006-07-14
Is there a way to call system commands ( bash code ) from within python and assign it to a variable?

for the sake of simplicity, say I want to capture the contents of ls to a list assuming the directory to list is as follows: 

/path/to/dir
     |
      ----   file.txt
      ----   picture.jpg
      ----   song.mp3
      ----   video.avi 

A) how would you write the code
and 
B) how would the list or if you choose a different variable type, look after the capture of ls? 

Thanks in advance

-Robert


[EDIT]

If you use any information from a document or website, if you could please post the document title and section or the URL that would help immensly. Thanks again.

---

### Post by mostwanted on 2006-07-14
ls would give you a string of paths separated by newline symbols (\n).

I don't know Python, but I'm guessing the way of doing system calls is by using a function called system(), like system("ls /path/to/dir"). So you capture the output of that into a variable. Then I'm sure there is a split() function for strings in Python, so use that to split whenever there's a "\n". That gives you a list with the paths.

---

### Post by jayemef on 2006-07-14
Well, you can import os and use os.system() to run system commands, but in many cases, like with directory listing, you'll find that python already has a command built in. You will want to use the built-in methods, as forking another executable is significantly more costly performance-wise.

```
import os

os.listdir('/home/me')    # Built-in directory listing.
os.system('ls /home/me')  # System directory listing.
```

---

### Post by rhipwell on 2006-07-15
> **jayemef said:**
> Well, you can import os and use os.system() to run system commands, but in many cases, like with directory listing, you'll find that python already has a command built in. You will want to use the built-in methods, as forking another executable is significantly more costly performance-wise.

```
import os

os.listdir('/home/me')    # Built-in directory listing.
os.system('ls /home/me')  # System directory listing.
```

Thanks jayemef, this helps a bunch.

---

