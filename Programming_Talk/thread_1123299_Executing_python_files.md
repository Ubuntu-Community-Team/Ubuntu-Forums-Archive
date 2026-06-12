---
title: "Executing python files"
date: 2009-04-12
forum: Programming Talk
---

### Post by shadow_code on 2009-04-12
Hi, this issue is driving me insane :S

When I click a python file in my file manager (that has execute permissions), the default action is to execute it. I want it to instead open in a text editor.

When it executes, my cursor changes to a window picker for every import call. Then it creates screenshots of the window I click and saves them as the import name!?

e.g.

```
import os
import xyz
```

Clicking the above file would save 2 screenshots of the windows I click, and save them as the files "os" and "xyz", in the current directory.
[B]
Questions are:
[/B]
[LIST=1]
[*]**Why on earth does it do this?**
[*]**How can I make it default to opening in a text editor?**
[/LIST]

Using:
xubuntu
Thunar
Compiz

Help please,

thanks in advance

---

### Post by diafanos on 2009-04-12
Do you use a shebag line at the very start of your file?
Something like this: 
```
#!/usr/bin/env python
```

or 

```
#!/usr/bin/python
```


In order to open it instead of execute it, you can uncheck the execute permission.
Then, whenever you want to execute it, just execute:

```
python <filename>.py
```

---

### Post by spupy on 2009-04-12
> **diafanos said:**
> Do you use a shebag line at the very start of your file?
Something like this: 
```
#!/usr/bin/env python
```

or 

```
#!/usr/bin/python
```


In order to open it instead of execute it, you can uncheck the execute permission.
Then, whenever you want to execute it, just execute:

```
python <filename>.py
```

A little clarification:
if you use the shebang and give execution permission, you can start your script like this:
```
./scriptname.py
```
For 
```
python scriptname.py
```
you don't actually need a shebang nor the executable permission. But is is good to have both the shebang and the executable flag (security considerations aside).

What happens in OP's case is due to the lack of the shebang. Since it is missing, the OS can't see that this is actually a Python script, so the file is interpreted as a BASH script instead. And in bash the import command creates a screenshot.

---

### Post by shadow_code on 2009-04-12
ahhh... that makes sense then!

Thanks heaps guys. You don't know how to stop Thunar executing Python files do you?

(apart from changing the file permissions)

There's some files that need the execute permission, and it's really annoying not knowing if Thunar's going to edit or run a script when I click on it...

---

### Post by shadow_code on 2009-04-12
I've decided to change the .py extension to the text/plain mime type, but Thunar is still detecting them as Python files :/

I added:

```
text/plain                    py
```

to ~/.mime.types

any ideas?

---

### Post by 0cton on 2009-04-12
it should detect it as python thanks to
#! /usr/bin/python

---

### Post by shadow_code on 2009-04-12
> **0cton said:**
> it should detect it as python thanks to
#! /usr/bin/python
Na, there's no shebang. I think thunar gets it from mime types but could be wrong

---

