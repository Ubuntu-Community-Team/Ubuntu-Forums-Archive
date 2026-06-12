---
title: "turbo to free pascal"
date: 2011-08-30
forum: Programming Talk
---

### Post by conradin on 2011-08-30
Hi all, 
Im trying to run various pascal programs write in borlad Turbo pascal under MSDOS. 
when I run gpc I get a modules error. 
```
$ gpc hello.p  -o binaries/hello
hello.p:4: error: module/unit interface `crt' could not be imported

```

where can I get modules to make this work? For that matter, is there a library or something I need to get all these borland turbo pascal programs to run in linux?
the program source looks like:
```
program Hello;
 
uses
   crt;
 
begin
   ClrScr;{Clears the screen}
   Write('Hello world');{Prints "Hello world"}
   Readln;{Waits for the user to press enter}
end. 
```

---

### Post by Zugzwang on 2011-08-30
Looks like a solution can be found here: [http://www.g-n-u.de/pipermail/gpc/2000-August/004202.html](http://www.g-n-u.de/pipermail/gpc/2000-August/004202.html)

---

