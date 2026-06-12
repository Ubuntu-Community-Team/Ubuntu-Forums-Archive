---
title: "Anjuta IDE - Really Simple Python Question"
date: 2010-07-21
forum: Programming Talk
---

### Post by FieldDoc on 2010-07-21
I'm new to Linux, Python and the Anjuta IDE.

I have created a new file called hello.py. This is the contents of that file:

```
    #!/usr/bin/env python
    print "Hello World!"
```

All I want to do is run this in the terminal. I go to **Run** > **Execute** but I get the following error message:

> Program 'home/joe/Programming/Python//hello.py' does not have execution permission

How do I get this really simple program to run?

Thanks,

---

### Post by RiceMonster on 2010-07-21
```
chmod +x /home/joe/Programming/Python/hello.py
```

---

### Post by Åtta on 2010-07-21
Or if you prefer to do it graphically, just right click it, "Properties" &#8594; "Permissions" and tick the box saying "Allow this file to be executed" (or something like that).

---

### Post by FieldDoc on 2010-07-21
> **RiceMonster said:**
> ```
chmod +x /home/joe/Programming/Python/hello.py
```

Thanks.

When I double click it - I get a dialog asking me if I want to run it in the Terminal or Run it. When I click either option - nothing really seems to happen. I'd have thought a Terminal window would open?

---

### Post by RiceMonster on 2010-07-21
> **FieldDoc said:**
> Thanks.

When I double click it - I get a dialog asking me if I want to run it in the Terminal or Run it. When I click either option - nothing really seems to happen. I'd have thought a Terminal window would open?

try executing it directly from a terminal to see the output. First, cd to the directory it's in:
```
cd ~/Programming/Python/
```

Then, execute it by doing either of the below:
```
python hello.py
./hello.py
```

---

### Post by FieldDoc on 2010-07-21
> **RiceMonster said:**
> try executing it directly from a terminal to see the output. First, cd to the directory it's in:
```
cd ~/Programming/Python/
```

Then, execute it by doing either of the below:
```
python hello.py
./hello.py
```

Thanks.

---

### Post by cgroza on 2010-10-24
Bringing this alive. Is there a plugin for python support for anjuta?

---

