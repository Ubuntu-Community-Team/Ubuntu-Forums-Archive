---
title: "Plz try to solve this Python problem"
date: 2012-05-27
forum: Programming Talk
---

### Post by prismctg on 2012-05-27
I know that using os module i can access bash script (os.module("nautilus") ) ; but now my problem is how can i open "nano example" and write some text from python script ?

---

### Post by Russss on 2012-05-28
Is there a reason you have to write from nano and not python:

```

with open('filename', 'w') as fil:
    fil.write(txt)


```

[http://docs.python.org/tutorial/inputoutput.html]("http://docs.python.org/tutorial/inputoutput.html")

---

### Post by prismctg on 2012-05-28
hm.. i didn't think about it .. but thanx for the idea

---

