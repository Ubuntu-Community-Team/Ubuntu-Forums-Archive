---
title: "Problem with the &quot;shebang&quot; in ubuntu"
date: 2016-02-15
forum: Programming Talk
---

### Post by alex13gamerz on 2016-02-15
Hello, all.
I'm programming in python 2.7, and I happened to have a problem in executing my programms/scripts.
I write #!/usr/bin/env python, but the system seems to not recognize this line because executes my python script as a bash script. I tryed to write #!/usr/bin/python directly but does not work either. What can I do to solve this? Thank you.

---

### Post by steeldriver on 2016-02-15
Hello and welcome to the forums

How exactly are you trying to run the script?

---

### Post by alex13gamerz on 2016-02-15
I'm trying to run it like a normal executable:          ./script.py, I gave it execution permission too, but doesn't work at all.

---

### Post by Habitual on 2016-02-15
What the script written on a Linux Machine?
Can you post the script?

---

### Post by spjackson on 2016-02-15
Please post terminal output from trying to run the script.
Post the script if possible.
Post the output of
```

od -c ./script.py | head

```

---

### Post by Vaphell on 2016-02-16
are you sure you put it in the very first line? If not, then your shebang is nothing but a comment (#)

---

