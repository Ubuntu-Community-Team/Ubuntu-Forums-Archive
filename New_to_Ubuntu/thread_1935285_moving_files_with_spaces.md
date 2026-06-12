---
title: "moving files with spaces"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by mferarri on 2012-03-04
Hi UbuntuForums,

I know you can move a file with spaces. say:

I have 3 files:

file 1
file 2
file 3

I can move file 1 like this:

```
mv "file 1" destination1
```

but how do i move all  files that have the word file in it?

like:

```
mv "*file*" destination1
```

this dosent work. what am i doing wrong?:P

---

### Post by codemaniac on 2012-03-04
Hello mate ,

Does this work for you

```
mv file\ [1-3] destination1
```

Best Regards

---

### Post by mferarri on 2012-03-04
> **codemaniac said:**
> Hello mate ,

Does this work for you

```
mv file\ [1-3] destination1
```

Best Regards

I'm really sorry code maniac, that probably would've worked for the example i gave. I simplified my problem so much that it wasnt the same as the one i really had.


My real problem is that I have lots of files including the ones that I want to move (the ones I want to move contain the words python) :

Python programming
Python in a nutshell
Python for unix
Rapid programming with python


So the result should be any files with the word python are moved into a new folder called python.

---

### Post by utnubuuser on 2012-03-04
mv path/to/Python * path/to/destinationfolder

---

### Post by mferarri on 2012-03-04
> **utnubuuser said:**
> mv path/to/Python * path/to/destinationfolder

when i type:
```
mike@mike-desktop:~/Downloads$ mv Python * /home/mike/Downloads/python

```

i get:

```

mv: cannot stat `Python': No such file or directory
mv: cannot move `python' to a subdirectory of itself, `/home/mike/Downloads/python/python'
```

---

### Post by codemaniac on 2012-03-04
Please use xargs to pass the arguments to mv , like below

```
ls -1 | grep -i "python" | xargs -I  file mv file ~/destination
```

---

### Post by Vishal Agarwal on 2012-03-04
change the directory  to the source directory
find . -name "*file*"  -type f  -exec mv {} /to/path \;

Try this and inform back

---

### Post by mferarri on 2012-03-04
> **codemaniac said:**
> Please use xargs to pass the arguments to mv , like below

```
ls -1 | grep -i "python" | xargs -I  file mv file ~/destination
```

this didnt work the first time, but i tried it again and it worked? O_O

---

### Post by codemaniac on 2012-03-04
The commandline should move the files containing "python" string in filename .
This is what your requirement was i guess mate . no ?

---

### Post by codemaniac on 2012-03-04
> **mferarri said:**
> this didnt work the first time, but i tried it again and it worked? O_O


Strange .This should work everytime :D

---

### Post by mferarri on 2012-03-04
> **codemaniac said:**
> Please use xargs to pass the arguments to mv , like below

```
ls -1 | grep -i "python" | xargs -I  file mv file ~/destination
```

It took ages to go though the man pages to find out what that line meant. The only bit I didn't get was ```
file mv file
```

why is the word file used? and why does it work with every case despite using grep to find a different word?

Thanks Codemaniac. In the end you provided me with the answer that I needed. A big thanks to everyone that posted. ):P

---

### Post by codemaniac on 2012-03-04
That is the way you learn my dear friend .
Here is a brief explanation about xargs :

xargs command is designed to construct argument lists and invoke other utility. xargs reads items from the standard input or pipes, delimited by blanks or newlines, and executes the command one or more times with any initial-arguments followed by items read from standard input. 

EDIT
{} as the argument list marker

{} is the default argument list marker. You need to use {} this with various command which take more than two arguments at a time. For example mv command need to know the file name. The above commandline will grep out filenames containing "python" keyword and move them to ~/destination .

note :You can rename {} to something else. In the above example {} is renamed as file. This is more readable as compare to previous {} commandline .

*
```
ls -1 | grep -i "python" | xargs -I {} mv {} ~/destination
```

Cheers

---

### Post by mferarri on 2012-03-04
Thanks codemaniac, that was a great explaination!:popcorn:

---

### Post by utnubuuser on 2012-03-04
Neat to learn something new...   

I didn't notice that not all of your files started with Python or python.

Apparently the wildcard character * will work in either case, so the files could have just as easily been moved with > mv /path/to/python/files/*ython* /path/to/destination

This approach covers all files containing "ython" somewhere in their title, regardless of other words, letters, and/or spaces.

---

