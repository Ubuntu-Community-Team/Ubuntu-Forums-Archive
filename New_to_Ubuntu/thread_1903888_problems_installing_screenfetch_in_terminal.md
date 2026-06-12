---
title: "problems installing screenfetch in terminal"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by sm0gg on 2012-01-03
[SIZE=3][FONT=Microsoft Sans Serif]So I downloaded[/FONT][/SIZE]  'screenfetch-dev-2.3.7.tar.gz' [SIZE=3][FONT=Microsoft Sans Serif]I moved it to my home folder & unpacked it.

Open terminal & 'ls' lists it there in the directory. but when I `chmod +x /screenfetch/screenfetch-dev` 

I get 'chmod cannot access  `/path/to/screenfetch/screenfetch-dev': No such file or directory'

What am I missing please?



[/FONT][/SIZE]

---

### Post by MG&amp;TL on 2012-01-03
so, if it's in your home folder, try:

```
cd ~/ #cd to your home folder, if you aren't already
cd screenfetch #cd to screenfetch dir
ls #see what's here
chmod u+x screenfetch
```

I think you've most likely typed it wrong, no disrespect. ;)

Another way of doing it would be to go to the file in nautilus (file browser) and right-clicking on the file -> properties -> Permission and tick 'allow executing file as program'-this does the same thing.

---

### Post by Immolatus on 2012-01-03
you need to be in the same directory as "screenfetch-dev". the command you entered is searching for "/screenfetch/screenfetch-dev" which is the next directory out so of course it does not exist within itself.

---

### Post by mcduck on 2012-01-03
> **sm0gg said:**
> [SIZE=3][FONT=Microsoft Sans Serif]So I downloaded[/FONT][/SIZE]  'screenfetch-dev-2.3.7.tar.gz' [SIZE=3][FONT=Microsoft Sans Serif]I moved it to my home folder & unpacked it.

Open terminal & 'ls' lists it there in the directory. but when I `chmod +x /screenfetch/screenfetch-dev` 

I get 'chmod cannot access  `/path/to/screenfetch/screenfetch-dev': No such file or directory'

What am I missing please?



[/FONT][/SIZE]

If you start the path with a "/" that means you start at the root of your file system, not from the current directory.

For example this would point to /screenfetch/screenfetch-dev
```
chmod +x /screenfetch/screenfetch-dev
```

...while this one points to a directory called "screenfetch", *located in your current directory*:
```
chmod +x screenfetch/screenfetch-dev
```

So if you actually unpacked it into your home, and are also currently in that directory, the second command would be correct as the right path is /home/*yourusername*/screenfetch/screenfetch-dev, not /screenfetch/screenfetch-dev.

---

### Post by sm0gg on 2012-01-03
OK thx guys, I can see where I went wrong  I hope. Thanks for your input, I'll see how I go, at least I'm learning right?

---

### Post by sm0gg on 2012-01-03
> **mcduck said:**
> If you start the path with a "/" that means you start at the root of your file system, not from the current directory.

For example this would point to /screenfetch/screenfetch-dev
```
chmod +x /screenfetch/screenfetch-dev
```...while this one points to a directory called "screenfetch", *located in your current directory*:
```
chmod +x screenfetch/screenfetch-dev
```So if you actually unpacked it into your home, and are also currently in that directory, the second command would be correct as the right path is /home/*yourusername*/screenfetch/screenfetch-dev, not /screenfetch/screenfetch-dev.


thank you, that's what I was screwing up.

---

