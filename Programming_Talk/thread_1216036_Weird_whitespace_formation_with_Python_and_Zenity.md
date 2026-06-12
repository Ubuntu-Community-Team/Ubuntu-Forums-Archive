---
title: "Weird whitespace formation with Python and Zenity"
date: 2009-07-17
forum: Programming Talk
---

### Post by BluShift on 2009-07-17
Hi all. I have been just experimenting with Python (trying to extend my Python understanding) and I was playing around with integrating Zenity and Python, using a temp text file. Here's the code:

```
#!/usr/bin/python
import os, time
# TEST 1
raw_input("Press any key to bring up the file selection dialog")
fout=open("/home/alex/Desktop/yo.tmp", "w")
fout.write("Hi there man")
fout.close()
fin=open("/home/alex/Desktop/yo.tmp", "r")
print fin.read()
fin.close()
#TEST 2
raw_input()
os.system("zenity --file-selection>hithere.tmp")
fish=open("/home/alex/Desktop/hithere.tmp", "r")
print fish.read()
fish.close()
raw_input()
```

Now when TEST 1 is complete, it writes, reads, and prints the lines FLAWLESSLY. When TEST 2 finishes, it somehow inserts a newline (\n) character into the end of the line ALWAYS. I have opened the "hithere.tmp" file and there is no newline in the file. That's just how Python reads it. What is going on here? Character encoding problems?

---

### Post by ghostdog74 on 2009-07-18
> **BluShift said:**
> Hi all. I have been just experimenting with Python (trying to extend my Python understanding) and I was playing around with integrating Zenity and Python, using a temp text file. Here's the code:

```
#!/usr/bin/python
import os, time
# TEST 1
raw_input("Press any key to bring up the file selection dialog")
fout=open("/home/alex/Desktop/yo.tmp", "w")
fout.write("Hi there man")
fout.close()
fin=open("/home/alex/Desktop/yo.tmp", "r")
print fin.read()
fin.close()
#TEST 2
raw_input()
os.system("zenity --file-selection>hithere.tmp")
fish=open("/home/alex/Desktop/hithere.tmp", "r")
print fish.read()
fish.close()
raw_input()
```

Now when TEST 1 is complete, it writes, reads, and prints the lines FLAWLESSLY. When TEST 2 finishes, it somehow inserts a newline (\n) character into the end of the line ALWAYS. I have opened the "hithere.tmp" file and there is no newline in the file. That's just how Python reads it. What is going on here? Character encoding problems?

i don't have zenity, so i don't what zenity --file-selection does. But let's another example, using echo.

```

echo "hello" > temp

```
using echo like that, hello will be saved to temp , including a newline. that's just how echo works. in bash, if you don't want to include newline, you can use printf. As for your Python code, fout.write() method doesn't include newline for you. if you try to write another sentence to your file, it will just join with your previous line to make one long line. Therefore, its always good to put a newline yourself , eg fout.write(line + "\n")

---

### Post by BluShift on 2009-07-18
Thank you so much! I was really beginning to lose faith in the forums... that was all I needed to fix my problem. I actually have one more question; is there a better way to get variables from a bash shell and incorporate them into a Python script? I remember reading something like creating a bash instance FROM a python instance creates a forked environment, so that the variables are inaccessible through any "get env variable" methods.

---

### Post by ghostdog74 on 2009-07-18
you can get environment variables through the os.environ . check the docs on os and sys module for more information.

---

