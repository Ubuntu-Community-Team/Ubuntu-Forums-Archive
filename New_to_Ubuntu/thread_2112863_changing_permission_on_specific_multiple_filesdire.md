---
title: "changing permission on specific multiple files/directories"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by toad3000 on 2013-02-05
I can't seem to figure out how finish off the last command 

```
 ls -p testfiles/ | more | grep "^d" | chmod 700 

```

I want to change the permission on all the files/directories that start with a d to 700. I just don't know what to write after chmod 700. I expect chmod to already know the files because it's streamed to it. 

Thanks

---

### Post by Cheesemill on 2013-02-06
How about...
```
find testfiles -type d -exec chmod 700 {} \;
```

---

### Post by Abu_Dayya on 2013-02-06
> **Cheesemill said:**
> How about...
```
find testfiles -type d -exec chmod 700 {} \;
```

No. I think your command will change directories to 700 rather than files that start with d. 

What you want is something like this:
```
find /path/to/testfiles -name "d*" -exec chmod 700 {} \;
```

---

### Post by Cheesemill on 2013-02-06
Your absolutely correct, I misread the OP.

---

