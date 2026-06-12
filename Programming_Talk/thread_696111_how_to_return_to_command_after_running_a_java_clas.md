---
title: "how to return to command after running a java class"
date: 2008-02-13
forum: Programming Talk
---

### Post by provisional_idiot on 2008-02-13
so basically in the terminal i want to run a java class multiple times without having to restart the terminal.... which is to say that whenever i run a java class from the terminal the command prompt doesnt return like it does, say, after a bash program finishes executing:

root@comp:#java someclass.java [ENTER]

the program runs but  root@comp:# doesnt return


can this be accomplished?? thanks

---

### Post by LaRoza on 2008-02-13
It must not stop for some reason, try hitting Ctrl + z to end it.

---

### Post by LittleLORDevil on 2008-02-13
In the end of the code when you want it to be finished add the line: 

System.exit(-1);

---

### Post by Zugzwang on 2008-02-14
Is it possible that you are searching for the "&" symbol? Just try:
```

java someclass.java &

```

---

