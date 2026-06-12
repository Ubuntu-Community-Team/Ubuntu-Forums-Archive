---
title: "Parameters unknown on cat"
date: 2017-08-14
forum: New to Ubuntu
---

### Post by sed_faster on 2017-08-14
Hello,

I found this command:
```

find . -type f -exec cat {} \;

```
I understand the purpose of the parameter -type and -exec but I don't understand for what to serve parameter {} and \; 
Why I need this?

Thanks

---

### Post by steeldriver on 2017-08-14
The only argument (parameter) that `cat` sees is the names of the files

{} is a placeholder for the each of the file(s) returned by the find command

\; tells the find command where the end of the -exec action is (the \ is just to escape the ; from interpretation by your shell)

---

### Post by sed_faster on 2017-08-14
Hummm, this is means which all the times I need use the argument -exec I need use the tag \; to the argument -exec know where my this arguments ends?

---

