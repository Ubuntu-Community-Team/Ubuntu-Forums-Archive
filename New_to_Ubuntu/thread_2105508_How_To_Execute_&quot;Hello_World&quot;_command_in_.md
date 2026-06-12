---
title: "How To Execute &quot;Hello World&quot; command in Kornshell Script on Ubuntu Terminal"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Hendiesel on 2013-01-16
Hi. Does anyone know how to execute the "Hello World" command in Kornshell script?  I'm reading O'Reilly's Kornshell manual and it's just not absorbing...

---

### Post by haqking on 2013-01-16
> **Hendiesel said:**
> Hi. Does anyone know how to execute the "Hello World" command in Kornshell script?  I'm reading O'Reilly's Kornshell manual and it's just not absorbing...

Do you mean how do you write a shell script in korn shell to print "Hello World" ?
```

nano hello.ksh
``````
#!/bin/ksh
# Hello World 
echo "Hello World"
```Save it.

Set it to be executable
```

chmod +x hello.ksh
```then run it

```
./hello.ksh
```

---

### Post by Hendiesel on 2013-01-16
Yes, exactly. Thank you very much!  A simple question, I know.

---

