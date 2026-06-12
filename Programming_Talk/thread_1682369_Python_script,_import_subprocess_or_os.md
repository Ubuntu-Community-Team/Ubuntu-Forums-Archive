---
title: "Python script, import subprocess or os"
date: 2011-02-05
forum: Programming Talk
---

### Post by mrfarrell on 2011-02-05
Hi,
I'm very new to python and even newer to scripting.
What is the difference between, for example, calling the subprocess.call("mkdir xyz") or os.mkdir("path")?
What's going on behind scenes?
Which is preferred?
Thanks!

---

### Post by johnl on 2011-02-05
```

os.mkdir("path")

```
Will:
1. invoke the linux kernel 'mkdir' syscall

which will create the specified directory and return.

```
subprocess.call("mkdir xyz")
```
will:
1. fork a new process
2. execute  the 'mkdir' program located in /bin
3. The 'mkdir' program will invoking the linux kernel 'mkdir' syscall. 
4. Once the mkdir program has exited, the function returns

I'll let you figure out which one is preferable :)

---

### Post by mrfarrell on 2011-02-05
lol thank you, thats a brilliant answer :)

---

