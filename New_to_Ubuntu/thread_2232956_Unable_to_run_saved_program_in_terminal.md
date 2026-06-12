---
title: "Unable to run saved program in terminal"
date: 2014-07-05
forum: New to Ubuntu
---

### Post by pgslmatias on 2014-07-05
I wrote a hello world python program in gedit. I saved it in a folder i created in my desktop called python and called the program file hello.py . I switched my directory in the terminal to the location of the folder, which I found by right clicking on the folder and choosing properties, and wrote the command python hello.py to run my hello world. However, my terminal said that there is no such file or directory. Here are the pictures of the terminal [ATTACH=CONFIG]254488[/ATTACH], the folder in my desktop [ATTACH=CONFIG]254490[/ATTACH], the location of the folder [ATTACH=CONFIG]254491[/ATTACH] and the file inside the folder[ATTACH=CONFIG]254492[/ATTACH]. What should I do? I just started using ubuntu and programming, so I'm sorry if it's something very straightforward that I'm unaware of.

---

### Post by steeldriver on 2014-07-05
You put the file hello.py in a *subdirectory* of the Desktop folder, called *python*. So you need to change to that directory first:

```

cd python
python hello.py

```

---

### Post by pgslmatias on 2014-07-05
Okay so I went to the teminal, posted the location of the folder and added the name of the folder itself and ran the program. Everything went perfectly fine. Here's a picture of the terminal for everyone that might encounter the same problem I did[ATTACH=CONFIG]254493[/ATTACH]. Thanks for your help! :)

---

### Post by steeldriver on 2014-07-05
... so now you know that 

```

cd [COLOR=#ff0000]**/**[/COLOR]python

```

is **NOT** the same thing as 
```

cd python

```
;)

---

