---
title: "Waiting for firefox to exit"
date: 2008-07-01
forum: Programming Talk
---

### Post by DrFugly on 2008-07-01
I'm not sure if this really belongs here. But I'm creating a perl script that uses a pretty simple line of code: exec("firefox")
Now what I want is for it to hang until firefox is exited. Or atleast know when firefox is closed. But it looks like the system call is just a quick call and firefox goes on in a different process. Anyway to track down firefox other than using ps?

Thanky!

---

### Post by odyniec on 2008-07-01
If you want to do it properly, you need to fork() a new process, and then wait() for the child process (Firefox) to exit.
```
if ($pid = fork()) {
    waitpid($pid, 0);
    print("Firefox exited.\n");
}
else {
    exec("firefox -no-remote");
}
```
The -no-remote option is there to make Firefox launch a new instance of the browser, instead of attempting to use an existing one.

---

### Post by DrFugly on 2008-07-04
very cool, exactly what i was looking for. I already knew about forking but '-no-remote' is news to me.

Thanks so much for the help!

---

