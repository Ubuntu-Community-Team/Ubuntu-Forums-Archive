---
title: "gccgo compiler problems"
date: 2014-09-06
forum: Programming Talk
---

### Post by tolid on 2014-09-06
Hello,

For some strange reasons I can't execute gccgo compiled 'Hello world' files.
This is my GO code:
```
$ cat hello.go
package main
import "fmt"
func main() {
    fmt.Println("Hello, world")
}
```

I tried to compile  hello.go in 2 different ways:
1. gccgo hello.go -o hello1
2. gccgo -static-libgcc hello.go -o hello2

But both executable files (hello1 & hello2) are failed to run with the same result:
```
$ ./hello2
no debug info in ELF executable errno -1
fatal error: no debug info in ELF executable

runtime stack:
no debug info in ELF executable errno -1
panic during panic
```

What is wrong? Maybe someone had similar experience and can help me?

Ubuntu 14.04.1 LTS,  
$ gccgo --version
gccgo (Ubuntu 4.9-20140406-0ubuntu1) 4.9.0 20140405 (experimental) [trunk revision 209157]

---

### Post by spjackson on 2014-09-06
> 
gccgo hello.go -o hello1

I don't know enough about go to know why, but you need -g.
```

gccgo -g -o hello1 hello.go

```
If you install the gccgo-go package then you can use "go build".
```

go build -o hello1 hello.go

```

---

### Post by tolid on 2014-09-06
> **spjackson said:**
> I don't know enough about go to know why, but you need -g.
```

gccgo -g -o hello1 hello.go

```


Thank you very much - it works!

---

