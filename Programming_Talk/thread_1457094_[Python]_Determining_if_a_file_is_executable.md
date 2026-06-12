---
title: "[Python] Determining if a file is executable"
date: 2010-04-18
forum: Programming Talk
---

### Post by dodle on 2010-04-18
I'm looking through the Python documentation, trying to figure out how to determine if a specified file is executable or not.  I've looked through the os module, but haven't found anything yet.  I've seen that there is a method os.chmod() for changing the mode of a file.  Is the "mode" what I am looking for?

I want to do something like this I guess:
[php]# Determine a files executable status

class AFile():
    def IsExecutable(self, file):
        
        # somecommand would return the files executable status
        fileinquestion = somecommand(file)
        
        #"executable" is used in place of whatever the correct value would be
        if fileinquestion == executable:
            return true
        else:
            return false[/php]
Does python have a module that can help me?  Also, will the returned value for an executable script be different than that of a binary executable?

---

### Post by ssam on 2010-04-18
looks like you you os.stat and the constants defined in the stat module.

```
os.stat("/bin/bash")[stat.ST_MODE]
```
gets you the permissions (ie the -rwxr-xr-x you see in ls -l).
in binary this is
```
0b1000000111101101
```
you then need to check the bit that corresponds to the property you are interested in.
```
stat.S_IXUSR
```
correspond to "Owner has execute permission." [http://docs.python.org/library/stat.html#stat.S_IXUSR](http://docs.python.org/library/stat.html#stat.S_IXUSR)
this is 64 in decimal or
```
0b0000000001000000
```
so you need to check if the 64 bit is set in permission bits. the logical AND does this. so the
```
0b1000000111101101 & 0b0000000001000000 = 0b0000000001000000
```
so the whole thing is
```
stat.S_IXUSR & os.stat("/bin/bash")[stat.ST_MODE]
```
which gives 64
or
```
stat.S_IXUSR & os.stat("/etc/resolv.conf")[stat.ST_MODE]
```
which gives zero.

then you can do

```

if stat.S_IXUSR & os.stat(filename)[stat.ST_MODE]:
    print filename, "is executable by its owner"


```

---

### Post by dodle on 2010-04-18
Wow, that's a bit advanced for me, but it works.  Thanks a bunch.  I also figured out another way to do it with a bash command, but I guess that would be considered non-pythonic.```
import commands

isexecutable = commands.getoutput("if [ -x myfile ]\nthen echo true\nfi")
if isexecutable == "true":
    return True
else:
    return False
```

---

### Post by soltanis on 2010-04-18
Who cares if it's non-pythonic, it works.

You can one-liner the sh command, as well as make it useful with os.system by collecting the exit status:

```

if [ -x myfile ]; then true else false; fi

```

Executing that with os.system, if the exit status is 0, then the true command (which exits with a 0 exit status) was run, so you have an executable file, otherwise false (which exits with non-0 status) will have executed, so you have a non-executable file.

Of course this only works on Unix-like systems, but it is POSIX portable (all POSIX systems must implement the sh) and Windows has no concept of "Executable" anyways.

---

### Post by snova on 2010-04-18
[os.access()]("http://docs.python.org/library/os.html#os.access")

[PHP]is_executable = os.access(path, os.X_OK)[/PHP]

> **dodle said:**
> Also, will the returned value for an executable script be different than that of a binary executable?

No.

> **soltanis said:**
> Who cares if it's non-pythonic, it works.

That doesn't make it good code.

---

### Post by soltanis on 2010-04-18
> **snova said:**
> That doesn't make it good code.

That really depends on how you define code to be good. Personally, one critical criterion for "good" is "it works" versus "it doesn't work."

---

