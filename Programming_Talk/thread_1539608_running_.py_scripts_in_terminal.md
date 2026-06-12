---
title: "running .py scripts in terminal"
date: 2010-07-26
forum: Programming Talk
---

### Post by Chris1274 on 2010-07-26
```
print('Hello world!')
input('Hit Enter to quit')
```

When I try to run this script in the terminal, it just blips. I thought the input() line was supposed to keep the program running until the user hits the Enter key, and *then* the terminal is supposed to close. Does anyone know what's going on?

Oh, I'm running 10.04.

---

### Post by wojox on 2010-07-26
Did you type in  ```
python
``` first?

---

### Post by Chris1274 on 2010-07-26
No, my "absolute beginner" books don't say I'm supposed to LOL I thought the .py extension told the system what it needs to know in that regard. I'll give it a try and see what happens.

---

### Post by Chris1274 on 2010-07-26
That doesn't work. It only ends up opening a python terminal.

---

### Post by TheStroj on 2010-07-26
When you're in terminal run script like this:

```
python something.py
```

Works for me :)

---

### Post by GlazedDonut on 2010-07-26
Or you can ad #!/usr/bin/python as the first line then you can just run the script as ./<my script here>

---

### Post by Chris1274 on 2010-07-26
Ah ha, that's the ticket. I was double-clicking on the GUI icon in the desktop folder, which then opens up a dialog box with a button to "run in terminal". How come that doesn't work?

---

### Post by wojox on 2010-07-26
> **TheStroj said:**
> When you're in terminal run script like this:

```
python something.py
```

Works for me :)

Yeah I misread it if you all ready have a script. TheStroj will work.

---

### Post by Chris1274 on 2010-07-26
@GlazedDonut: excellent, that works when opening the file from the GUI too, thanks!

---

### Post by GlazedDonut on 2010-07-26
> **Chris1274 said:**
> @GlazedDonut: excellent, that works when opening the file from the GUI too, thanks!

You're welcom :D

---

