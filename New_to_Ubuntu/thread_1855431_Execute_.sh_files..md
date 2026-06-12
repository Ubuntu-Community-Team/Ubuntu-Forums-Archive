---
title: "Execute .sh files."
date: 2011-10-06
forum: New to Ubuntu
---

### Post by flying_turtle on 2011-10-06
Hi, i am new at ubuntu and i have some .sh files, probably from windows.
I would like to know how to execute those files in ubuntu environment.
Any help is useful.

---

### Post by haqking on 2011-10-06
> **flying_turtle said:**
> Hi, i am new at ubuntu and i have some .sh files, probably from windows.
I would like to know how to execute those files in ubuntu environment.
Any help is useful.

```
sh filename.sh
```

```
./filename.sh
```

make sure you trust the source though before running them, be careful if you choose to run them as root also

---

### Post by P05TMAN on 2011-10-06
> **flying_turtle said:**
> Hi, i am new at ubuntu and i have some .sh files, probably from windows.
I would like to know how to execute those files in ubuntu environment.
Any help is useful.

What are these files?

If they are bash scripts you can execute them like so: 

```


./filename


```They must, however, be an executable file so you may need to perform: 

```
 

chmod +x filename.sh


```haqking's example works as well; please heed the advise about trusting the source! (+1)

---

### Post by flying_turtle on 2011-10-06
Well, i checked the source and it works fine now.
Thanks!

---

