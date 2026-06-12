---
title: "Python packaging: os.mkdir dependency"
date: 2008-10-31
forum: Programming Talk
---

### Post by Don S on 2008-10-31
Hi, I'm having a slight problem with a package using the os.mkdir function. It works fine on my home computer/the computer I'm developing on, but on any other computer, with a brand new Ubuntu installation on, it doesn't work. The error appears in a line, where it calls the function to read a file, in the directory that it was supposed to create and make a file in. Those two obviously failed, and the file is not in the folder, hence it fails to load. Now, this doesn't happen on my home computer. The os.system function works and if I manually create these folders and files, the program runs just fine.

So, is there a certain package that the os.mkdir module depends on, in order to work?

» Don S

---

### Post by geirha on 2008-10-31
os.mkdir should be available on all platforms with a base install of python. And if os.mkdir fails to create a directory, it will throw an exception, so unless you are catching and ignoring that exception, os.mkdir is not failing. It's probably just given the wrong path, so it creates the directory somewhere else or something.

---

### Post by Can+~ on 2008-10-31
Please post some code and the error.

---

### Post by Don S on 2008-10-31
It should definitely be in the right path. Well, I think I'm gonna have to try and solve it out, by the old model of trial and error, then. I don't really have any idea, why it doesn't throw an exception and doesn't create the directory.

This is the code, where the error occours:
```
try:
	listFile = open(user+"/.xoba/listsettings.txt")
except:
	IOError
	os.mkdir(user+"/.xoba")
	listFile = open(user+"/.xoba/listsettings.txt", "w")
	listFile.write("Main\n")
	listFile.close()
	listFile = open(user+"/.xoba/settings.txt", "w")
	listFile.write("Main")
	listFile.close()
```

"user" is a variable that stores the user directory.

---

### Post by Can+~ on 2008-10-31
*edit* Whoops, didn't read that, I'll see what I can do.

How are you getting the user path?

[FONT="Courier New"]os.environ["HOME"][/FONT]

---

### Post by Don S on 2008-10-31
I use this:
```
user = os.path.expanduser("~")
```

But the user variable is used many places elsewhere, where it functions just properly. There is also, as said, no issues on my primary computer.

---

### Post by geirha on 2008-10-31
```
try:
	listFile = open(user+"/.xoba/listsettings.txt")
except:
	IOError
	os.mkdir(user+"/.xoba")

```

You are not catching IOError here. You are catching any exception/error. The except should be:

```

except IOError:
# or
except IOError, e:  # If you want to print the error message (str(e)) in a warning for instance

```

Also, I would've used os.path.join instead of using "/", since "/" wouldn't have worked on windows (saves you the trouble later if you want to make it run on other operating systems as well).
 
And also, use isdir,isfile,exists etc from os.path to check if they exist, instead of checking for an IOError. And put a "catch all" try/except around all that to catch unforseen cases (like out of disk space, insufficient permissions etc)

```

try:
    confdir = os.path.join(user, ".xoba")
    if not os.path.isdir(confdir):
        os.mkdir(confdir)
    listsettings = os.path.join(confdir, "listsettings.txt") 
    if not os.path.isfile(listsettings):
        file(listsettings, "w").write("Main\n")
    # etc ...
except Exception, e:
    print >>sys.stderr, "Error creating config:", e

```

---

### Post by Greyed on 2008-10-31
> **geirha said:**
> Also, I would've used os.path.join instead of using "/", since "/" wouldn't have worked on windows (saves you the trouble later if you want to make it run on other operating systems as well).

While your intentions are good your specifics are bad.  /some/path/in/Windows/ works perfectly fine.  Python, when it makes the appropriate calls, converts the / to \ as needed.  os.path.join is a good habit here, however.

 > And also, use isdir,isfile,exists etc from os.path to check if they exist, instead of checking for an IOError. And put a "catch all" try/except around all that to catch unforseen cases (like out of disk space, insufficient permissions etc)

This too has good intentions but is bad.  Remember, you're in a multi-user environment and although most people's machines are effectively in a single-user environment it is a bad habit to code as if that were always true.

Using isdir(), isfile() to check to see if they are a directory or a file is good.  Using them to check for the existence of a directory or file is meaningless.  Because what happens when the file you checked in one line is deleted before the next executes?  You're going to have an IOError.  Just open the darn file and check for the exception.  If it opened then it exists.  If you get an exception, the exception will tell you the problem and you can handle it accordingly.

---

### Post by geirha on 2008-10-31
> **Greyed said:**
> While your intentions are good your specifics are bad.  /some/path/in/Windows/ works perfectly fine.  Python, when it makes the appropriate calls, converts the / to \ as needed.  os.path.join is a good habit here, however.

Ah, haven't used Windows much, so I just assumed it wouldn't work :)
 
> **Greyed said:**
> 
This too has good intentions but is bad.  Remember, you're in a multi-user environment and although most people's machines are effectively in a single-user environment it is a bad habit to code as if that were always true.

Guess my wording was off. I was referring to that specific piece of code, which was doing stuff in the user's home directory.

> **Greyed said:**
> 
Using isdir(), isfile() to check to see if they are a directory or a file is good.  Using them to check for the existence of a directory or file is meaningless.  Because what happens when the file you checked in one line is deleted before the next executes?  You're going to have an IOError.  Just open the darn file and check for the exception.  If it opened then it exists.  If you get an exception, the exception will tell you the problem and you can handle it accordingly.

In this case, it was creating a configuration directory inside the user's home if it didn't already exist. If it already exists, doing os.mkdir will throw an IOError, so it's of course an option to check for that, but using os.path.isdir is shorter and nicer. And if the directory should suddenly appear between the isdir and mkdir, then that's the user's fault, and the program shouldn't need to expect that, other than exit from mkdir's IOError.

And the files inside the directory. They should only be created if they don't already exist. Opening a file for writing will not give an exception if the file exists. For reading a file I agree with you, no need to check, just try reading and catch an exception if it isn't there.

Anyway, that was based on my interpretation of what that piece of code was supposed to do, and how I expect a program to deal with the configuration files.

---

### Post by ghostdog74 on 2008-10-31
actually, to check for files existence, the function to use is  os.path.exists().

---

### Post by geirha on 2008-11-01
> **ghostdog74 said:**
> actually, to check for files existence, the function to use is  os.path.exists().

Yes, that'll work too. The difference is only in how you want to handle the cases where for example a file you intend to create exists, but is not a file. exists() will return True, the program will skip creating the file, and will eventually throw an IOError when it tries to read it. isfile() will return False, and when the program tries to create it, it throws an IOErrror.

---

