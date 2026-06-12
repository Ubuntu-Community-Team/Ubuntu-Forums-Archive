---
title: "autorun .py files"
date: 2008-01-13
forum: Programming Talk
---

### Post by ryeterrell on 2008-01-13
Does nayone know of some way I can make linux run .py files without having to prefix them with 'python'?

In other words, I would like to run a program by typing:

'myprogram.py'

instead of:

'python myprogram.py'

Thanks for any help :)

-newb

---

### Post by kevykev on 2008-01-13
You should already be able to do this if your program has 
```
#!/usr/bin/env python
```
as it's first line.

You also need to make it executable
```
$ chmod +x myprogram.py
```

Then you can run it with
```
$ ./myprogram.py 
```

Note you'll always need the ./ unless the program is in a location on the system PATH. This is the same for all scripts/executables on linux.

-Kevin

---

### Post by Martin Witte on 2008-01-13
put as first line in our script** #!/usr/bin/env pyton**, change permissions of the file the  script is in to be an executable - eg, **chmod 755 myscript.py**, and then run it with** ./myscript.py**

---

### Post by ryeterrell on 2008-01-13
aha, that worked wonderfully; thanks guys

---

