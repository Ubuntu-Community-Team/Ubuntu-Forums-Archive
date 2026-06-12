---
title: "[SOLVED] Python newbie, where did it go?"
date: 2008-08-16
forum: Programming Talk
---

### Post by Ingenue on 2008-08-16
Ok, I'm brand new to Python (like today) and new to programing (today also). I've made a simple little script and have made it executable with: ```
chmod +x *file* 
``` 

At least I think. Anyhoo, when I click on the program it asks me choose whether to run it or view it. When I choose to run it in a terminal, the terminal flashes and goes away before I can see it. So I searched the forums then went and changed the executable files settings in nautilus to automatically run when double clicked. Now nothing even happens! 

I know this is very elementary but I just can not move on until I understand it, OCD I know. It would always be in the back of my mind if I don't know the answer. Here is my little script.

```
#!/usr/lib/python
print 'melissa'
import sys
print sys.platform
```

School me please.

---

### Post by dje on 2008-08-16
> **Ingenue said:**
> Ok, I'm brand new to Python (like today) and new to programing (today also). I've made a simple little script and have made it executable with: ```
chmod +x *file* 
``` 

At least I think. Anyhoo, when I click on the program it asks me choose whether to run it or view it. When I choose to run it in a terminal, the terminal flashes and goes away before I can see it. So I searched the forums then went and changed the executable files settings in nautilus to automatically run when double clicked. Now nothing even happens! 

I know this is very elementary but I just can not move on until I understand it, OCD I know. It would always be in the back of my mind if I don't know the answer. Here is my little script.

```
#!/usr/lib/python
print 'melissa'
import sys
print sys.platform
```

School me please.

firstly the first line (which tells the os where the python interpreter is) should be like this:
```
#!/usr/bin/env python
```
next we import all needed modules before the program code and we do not print sys.platform so the final result is this:
```
#!/usr/bin/env python

import sys

print "melissa"
sys.platform
```

you could assign a variable to the output of sys.platform and print it as a string

```
#!/usr/bin/env python

import sys

print "melissa"
platform = sys.platform
print platform
```

it will flash away it you run it that way (because the terminal closes when the program exits) so open a terminal and try this:
```
python /path/to/python/file.py
```

have fun with python, it's a great language

dje

---

### Post by ad_267 on 2008-08-16
The terminal closes after it's run so you'll want to open up a terminal by going to Applications - Accessories - Terminal.

Then use:
```
cd "/home/username/path/to/python/script"
```
to change direction, then:
```
./name_of_script.py
```
to run the file.

---

### Post by pmasiar on 2008-08-16
Use IDLE - Python IDE. Included with Windows, but you need to install it separately on Linux. 

You can run your code, and more, with it.

BTW if you lack links for learning, see wiki in my sig. :-)

---

### Post by Ingenue on 2008-08-16
What about: ```
raw_input ()
```

Isn't that suppose to keep the Terminal open after it executes the script?

---

### Post by ad_267 on 2008-08-16
> **Ingenue said:**
> What about: ```
raw_input ()
```

Isn't that suppose to keep the Terminal open after it executes the script?

Well yes it would have that effect, but that's not really what it's supposed to be used for. It's better to just open a terminal and then run the script from there.

---

### Post by Ingenue on 2008-08-16
Thanks everyone!

---

