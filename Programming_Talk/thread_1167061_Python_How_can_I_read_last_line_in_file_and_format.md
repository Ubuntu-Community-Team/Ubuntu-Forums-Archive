---
title: "Python: How can I read last line in file and format the text?"
date: 2009-05-22
forum: Programming Talk
---

### Post by bwitherell on 2009-05-22
Hi,

I have an issue with some of my python code.

I have a file that i need to read the last line from. Then once that line is read i need to be able to format the text. ie: remove leading spaces and some words. below is an example of the file.

```

   0 hello
   1 hello
   2 hello
   3 hello
   4 hello
   4 hello
   4 hello
   5 hello

```

Basically, i need to get the number from the last line in the file read it into a variable and convert it into an integer.

Any help is much appreciated. Thank you all very much.

---

### Post by bwitherell on 2009-05-22
Sorry, I omitted some detail.

I tried reading the last line then print out only the portion of that line that i need by using something like:

```

myvar = open(myfile, 'r')
lst = myvar.readlines()
myvar = lst[len(lst)-1]
myvar.close
print lst[2:6]

```

When I do this though, it prints out only the first line in the file.

I have tried using repr() and str() to convert to a string but i get the same results when i do the "print lst[2:6]".

If i just "print lst" without the [2:6] it displays the last line. I am very confused. What am i doing wrong? I have tried for hours to figure this out.

Thanks Again.

---

### Post by meatpan on 2009-05-22
> **bwitherell said:**
> 
```

myvar = open(myfile, 'r')
lst = myvar.readlines()
myvar = lst[len(lst)-1]
myvar.close
print lst[2:6]

```



A few comments:
- myvar is a file
- lst is a list
- lst[len(lst) - 1] is a string
- You assign the string to the file ref, then try to close the ref (which is now a string and should throw an AttributeError)
- You print a 'slice' of the list, not a string.  'print myvar' might be what you want


Hope that is enough to help you get started

---

### Post by bwitherell on 2009-05-22
sorry, typo.... i meant i use 'print myvar' not 'print lst'

Thanks for the reply and clarification. That does help me understand more about what i am doing.

---

### Post by ghostdog74 on 2009-05-22
```

for line in open("file"):
    last=line
print last

```

---

### Post by smartbei on 2009-05-23
@ghostdog:
That's a funny way to do it... useing .readlines makes more sense IMO.

```

last_line = file(PATH_TO_FILE, "r").readlines()[-1]

```

---

### Post by ghostdog74 on 2009-05-23
> **smartbei said:**
> @ghostdog:
That's a funny way to do it... useing .readlines makes more sense IMO.

```

last_line = file(PATH_TO_FILE, "r").readlines()[-1]

```
there's an even more funnier way if you want to call it
```

for line in open("file"):pass
print line

```
for small files, both readlines method and this method works. 
for bigger files, in terms of MB/GB, using readlines() consumes memory you don't want to read everything into memory just to get the last line. therefore, its not funny anymore to use file iteration method.

---

### Post by Vadikus on 2009-05-25
And if you have 1GB log file... well... it will read it all first. And this may take a while. The only quick way I know, is to use shell 'tail' command. And get the result of it into the python script.

---

### Post by ghostdog74 on 2009-05-25
> **Vadikus said:**
> And if you have 1GB log file... well... it will read it all first. And this may take a while. The only quick way I know, is to use shell 'tail' command. And get the result of it into the python script.
memory mapping is another way in Python. use mmap module

---

### Post by soltanis on 2009-05-26
For the love of seek(), why do you iterate through the file when all you want is the last line?

```

Line_len = 10 # or however long a line is, since in your example they all looked the same
SEEK_END = 2
file = open(file_path, "r")
file.seek(-Line_len, SEEK_END)

integer = int(str(file.read(Line_len)).split(" ")[0].strip())

```

---

### Post by ghostdog74 on 2009-05-26
> **soltanis said:**
> For the love of seek(), why do you iterate through the file when all you want is the last line?

```

Line_len = 10 # or however long a line is, since in your example they all looked the same
SEEK_END = 2
file = open(file_path, "r")
file.seek(-Line_len, SEEK_END)

integer = int(str(file.read(Line_len)).split(" ")[0].strip())

```

that's not correct, you are merely getting the last 10 bytes. you have to find a way to count the "\n" to make up a line.

---

