---
title: "PyGtk question."
date: 2010-01-25
forum: Programming Talk
---

### Post by Freckletoe on 2010-01-25
Ok, so this is my first foray into pyGtk, and I want to build GUI that is able to get multiple instances of user input from one entry source (ie: it asks the user a question, if they answer yes to the question, then it asks them something else).

1)My first problem is that I can ask them the first question, but it get's increasingly hard to wait for the second input. So are there any specific methods to doing that, something I've missed?

2) (my sort of solution to #1) I also want to use only one main button to control the flow of it (a continue button). I've figured out how to connect the button to a certain event, and then after that I can connect that to a different event when clicked, BUT I can't connect it for a third time. Is that a limitation of python/pyGtk? Or am I just missing something?

Thanks in advance.

---

### Post by Bodsda on 2010-01-27
Im no GTK programmer but if you think about from a cli point of view first it is easier. I would be thinking along the route of a while loop that appends to a list, like this

```

answers = []
while 'quit' not in answers:
    answers.append(raw_input("Question?: "))

```You could also use a list to control the questions
```

answers = []
questions = ["Male or Female?: ", "Young or Old?: ", "Gnome or KDE?: "]
for i in questions:
    if 'quit' not in answers:
        answers.append(raw_input(i))


```
Output from that would be something like this
```

Male or Female?: Male
Young or Old?: Young
Gnome or KDE?: Gnome
>>> for i in questions:
...     if 'quit' not in answers:
...             answers.append(raw_input(i))
... 
Male or Female?: Male
Young or Old?: quit
>>> 

```
Hope this helps,
Bodsda

---

### Post by nvteighen on 2010-01-27
> **Freckletoe said:**
> Ok, so this is my first foray into pyGtk, and I want to build GUI that is able to get multiple instances of user input from one entry source (ie: it asks the user a question, if they answer yes to the question, then it asks them something else).

1)My first problem is that I can ask them the first question, but it get's increasingly hard to wait for the second input. So are there any specific methods to doing that, something I've missed?

2) (my sort of solution to #1) I also want to use only one main button to control the flow of it (a continue button). I've figured out how to connect the button to a certain event, and then after that I can connect that to a different event when clicked, BUT I can't connect it for a third time. Is that a limitation of python/pyGtk? Or am I just missing something?

Thanks in advance.

1) Hm... Create all widgets beforehand and show()/hide() them as needed.
2) There's no limitation for signal reconnection I recall of... can you post that code, please?

---

