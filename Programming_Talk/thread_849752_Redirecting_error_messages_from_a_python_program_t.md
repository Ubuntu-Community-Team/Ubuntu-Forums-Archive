---
title: "Redirecting error messages from a python program to a file"
date: 2008-07-04
forum: Programming Talk
---

### Post by mrcheesypants on 2008-07-04
Didn't know where exactly to put this, but I figured there would be more people familiar with my python problem in the programming forum than in a Linux forum. Anyway, I wrote an AIM bot in twisted worlds for a chatroom and it prints a lot of information as well as some error reports. I want to put in the errors in a file so it will be easier to debug.

A simple
```
 ./mycode > errors 
```

causes two problems:
1) Prompts such as raw_input("Username:") do not show in the standard output but are saved to the errors file.
2) None of the errors are saved.

Just to make sure I'm stating my problem clearly, let me give an example script test.py
```
 #!/usr/bin/python
print "Hello World!"
spam()

```

Now when I run the file, I get this output:
```
 Hello World!
Traceback (most recent call last):
    File "test.py", line 3, in <module>
    spam()
NameError: name 'spam' is not defined

```

Now if I were to use
```
 ./test.py > error 
```
Only the "Hello World!" would be saved to the file, and only the rest would be printed. What I want is for both to be printed, or atleast just the errors to be saved in a file.

---

### Post by Def13b on 2008-07-04
Something like this should work.

```
import sys
sys.stderr = open('errorlog.txt', 'w')

# do whatever

sys.stderr.close()
sys.stderr = sys.__stderr__
```

Could of sworn I read something about a better way to do this but can't for the life of me remember what or where, this should work though.

This will also obviously overwrite the log file each time the program is run so 'a' instead of 'w' might be better for logging.

---

### Post by mrcheesypants on 2008-07-04
I'm looking for a way to do it in bash if anyone knows a way, but I'll use this in the mean time. Thanks.

---

### Post by Def13b on 2008-07-04
ah, get your meaning now, perhaps this,

# sends errors to file, 'hello world' to stdout
```
./test.py 2> error
```

# sends both errors and 'hello world' to file
```
./test.py &> error
```

some other options here,
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)

---

