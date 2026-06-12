---
title: "i need to know how to make python esxecutable"
date: 2007-10-28
forum: Programming Talk
---

### Post by bribaetz on 2007-10-28
how do i make python executable files or what ever how do you do that once your finished programming

---

### Post by CptPicard on 2007-10-28
Put 

```

#!/usr/bin/python

```

as the first line (this makes the shell run any text file through the specified command)

and then do

```

chmod +x yourfile

```

To set the executable flag.

---

### Post by bribaetz on 2007-10-28
thats all it gives me

---

### Post by CptPicard on 2007-10-28
Congrats, it worked. Now you just choose what you want to do. Or alternatively you open a terminal yourself and type the filename (as ./myfile.py because current dir should not be in PATH)... and it runs.

---

### Post by smartbei on 2007-10-28
Perhaps what you are looking for is more along the lines of packaging your application so that any ubuntu user can just install the package and have the shortcut appear in the right place, etc? If yes, see sticky at the top of the programming forum (I think).

---

### Post by bribaetz on 2007-10-28
kind of sort of i just want it to work when i click on it

---

### Post by smartbei on 2007-10-28
Sorry, I would offer you more help but I am not next to my Ubuntu pc right now :(. Just checked, the sticky isn't there. Try Google... :|

---

