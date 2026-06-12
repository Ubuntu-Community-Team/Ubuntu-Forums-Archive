---
title: "Bash scripting help. Automatically kill a programme"
date: 2012-06-23
forum: Programming Talk
---

### Post by jgcsd on 2012-06-23
If I have a script running that depending on some conditions starts a programme, is there a way to have my script kill that programme?

Semi-related question

Is there an easy way to run a programme, but automatically kill it if it takes longer than x seconds?

---

### Post by hakermania on 2012-06-23
1. To kill a program
Inside your script:
```

...
#launching your program:
myprog&
#getting its id
id=$!
#killing it whenever you want
kill $id
...

```

2 Killing a program after X seconds:
```

...
#function that takes as argument the seconds and the id
killprogram(){
sleep $2
kill $1
}

#launch program:
prog&
id=$!
#the 1st argument is the id and the second the seconds to sleep...
killprogram $id X& #e.g. killprogram 1342 17&
...

```

---

### Post by sisco311 on 2012-06-24
BashFAQ 068 (link in my signature).

---

