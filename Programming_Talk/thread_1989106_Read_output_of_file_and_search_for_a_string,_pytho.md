---
title: "Read output of file and search for a string, python"
date: 2012-05-28
forum: Programming Talk
---

### Post by Yukawa on 2012-05-28
Hey everyone,

I'm very new in Python. I have to read output of the file, search for the string and read the information in that line. 

H  1  6563A  **40.092   3.1917**      +Col  4438A  37.004   0.0026      

Line look like that:

The search string is 
H  1  6563A the information I need is in bold.

Please help

---

### Post by MG&amp;TL on 2012-05-28
You should probably start a new thread...but anyway:

```
for line in open("file"):
 if "H 1 6563A" in line:
  split_string = line.split()
  result_string = split_string[3] + " " + split_string[4] 
  print result_string    

```

Correct me if I'm wrong.

---

### Post by nothingspecial on 2012-05-28
> **MG&TL said:**
> You should probably start a new thread...

You are right.

But since Yukawa didn't, I have :)

---

### Post by Yukawa on 2012-05-28
> **MG&TL said:**
> You should probably start a new thread...but anyway:

```
for line in open("file"):
 if "H 1 6563A" in line:
  split_string = line.split()
  result_string = split_string[3] + " " + split_string[4] 
  print result_string    

```

Correct me if I'm wrong.

Thank you for such a quick answer. This works jut fine when string is at the beginning of the line, but sometimes is in the middle? What to do in that case?

---

### Post by sanderj on 2012-05-28
So, do you mean the two 'words' after "6563A" anywhere in the string. If so:

```
import string

line = "blabla blabla bla H 1 6563A 40.092 3.1917 +Col 4438A 37.004 0.0026"
searchstring = "6563A"

split_string = line[string.find(line,searchstring):].split()

result_string = split_string[1] + " " + split_string[2]
print result_string

```

with this result:

```
sander@R540:~$ python stringding.py 
40.092 3.1917
sander@R540:~$ 

```

---

### Post by Yukawa on 2012-05-28
> **sanderj said:**
> So, do you mean the two 'words' after "6563A" anywhere in the string. If so:

```
import string

line = "blabla blabla bla H 1 6563A 40.092 3.1917 +Col 4438A 37.004 0.0026"
searchstring = "6563A"

split_string = line[string.find(line,searchstring):].split()

result_string = split_string[1] + " " + split_string[2]
print result_string

```

with this result:

```
sander@R540:~$ python stringding.py 
40.092 3.1917
sander@R540:~$ 

```
Thanks mate it is working now

---

### Post by Yukawa on 2012-05-28
OK another question. If I wonna perform that in multiple files, with same extension. How I can do that?

---

### Post by MG&amp;TL on 2012-05-28
Using glob.glob would be one solution. [http://docs.python.org/library/glob.html#glob.glob]("http://docs.python.org/library/glob.html#glob.glob")

```

for files in glob.glob('/path/to/files/*.txt'):
 for lines in open(files):
 #Do stuff with lines here.

```

EDIT: although yeah, a quick google got that.

---

### Post by sanderj on 2012-05-28
> **Yukawa said:**
> OK another question. If I wonna perform that in multiple files, with same extension. How I can do that?

... I would advice you to read something on Python. It now feels like we're doing your homework.

---

### Post by Yukawa on 2012-05-28
> **sanderj said:**
> So, do you mean the two 'words' after "6563A" anywhere in the string. If so:

```
import string

line = "blabla blabla bla H 1 6563A 40.092 3.1917 +Col 4438A 37.004 0.0026"
searchstring = "6563A"

split_string = line[string.find(line,searchstring):].split()

result_string = split_string[1] + " " + split_string[2]
print result_string

```

with this result:

```
sander@R540:~$ python stringding.py 
40.092 3.1917
sander@R540:~$ 

```

> **MG&TL said:**
> Using glob.glob would be one solution. [http://docs.python.org/library/glob.html#glob.glob]("http://docs.python.org/library/glob.html#glob.glob")

```

for files in glob.glob('/path/to/files/*.txt'):
 for lines in open(files):
 #Do stuff with lines here.

```

EDIT: although yeah, a quick google got that.
I was doing that, found it on the google, but I was having some other mistake in the code, so when i tried this in the first place it didn't work. Don't worry this is not homework, no marks no grades.

Thanks once more.

---

