---
title: "Basic Python Query."
date: 2009-06-05
forum: Programming Talk
---

### Post by s.fox on 2009-06-05
Hi,

I'm learning python and am getting rather into it but I have a query.  In the guide I have been following all the exercises have these lines at the start of the script.

```

#!/usr/bin/python
# Filename: thisFile.py

```

I realise they are commented out,  but I was wondering what are they for?

Thanks for helping my understanding.

-Ash R

---

### Post by benj1 on 2009-06-05
most comment lines (starting with a #) do nothing including your filename line.

the first line is important, that tells the OS what interpreter to use to execute the script.

i would however recommend using 

```
#! /usr/bin/env python
```

as its more portable.

---

### Post by ajackson on 2009-06-05
The first line is the [shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)"), if you make the file executable
```
chmod +x thisFile.py
```
You can run it directly
```
./thisFile.py
```
It knows that it has to the program /usr/bin/python to execute the file.

---

### Post by s.fox on 2009-06-05
> **benj1 said:**
> most comment lines (starting with a #) do nothing including your filename line.

the first line is important, that tells the OS what interpreter to use to execute the script.

i would however recommend using 

```
#! /usr/bin/env python
```as its more portable.


Oh,  I see.

Thank you for clearing that up for me  :D

-Ash R

---

### Post by s.fox on 2009-06-05
> **ajackson said:**
> The first line is the [shebang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29"), if you make the file executable
```
chmod +x thisFile.py
```You can run it directly
```
./thisFile.py
```It knows that it has to the program /usr/bin/python to execute the file.


That's something I have yet to do.  Might try that now actually.  

Thanks for the response :D

-Ash R

---

### Post by fiddler616 on 2009-06-05
> **Ash R said:**
> In the guide I have been following all the exercises have these lines at the start of the script.

```

# Filename: thisFile.py

```



-Ash R
Like the above people said, that line does nothing for the *execution* of your program. It's probably there for clarity in the book.

---

### Post by Volt9000 on 2009-06-06
Just to clarify, if you don't have the shebang/hashbang at the beginning of your program, you'll have to invoke the program manually from the command line by typing

```

python myfile.py

```


As an aside, I have a question.

> **benj1 said:**
> i would however recommend using 

```
#! /usr/bin/env python
```

as its more portable.

Why is "/usr/bin/env python" more portable than "/usr/bin/python"?

---

### Post by benj1 on 2009-06-06
my understanding was that env holds environmental variables such as where the python interpreter is installed and is pretty much standard, whereas the interpreter isn't necessarily installed in /usr/bin

i've never come across any issues so i suspect its an issue that can occur with BSD or cygwin or something, but its a good habit to get into i suppose

---

