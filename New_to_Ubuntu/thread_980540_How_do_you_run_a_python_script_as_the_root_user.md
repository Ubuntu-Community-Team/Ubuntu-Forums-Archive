---
title: "How do you run a python script as the root user?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Meshach on 2008-11-12
Hello all.


How would you run a python script as the root?


Thanks,
Meshach

---

### Post by jamesrl on 2008-11-12
```
sudo python name_of_python_script.py
```

---

### Post by OutOfReach on 2008-11-12
Just like any other command
```

sudo python mypythonscript.py

```

EDIT: Beaten, again!

---

### Post by Meshach on 2008-11-15
Thanks guys.

Best Regards,
Meshach

---

### Post by master5o1 on 2008-11-15
1up to the above posters :)

But why wouldn't one just say 'script.py' instead of 'mypythonscript.py' or 'name_of_python_script.py'.

Also, would it work without the `python` command in there if the file is permissed as executible for everyone?

chmod 777 ./script.py
sudo ./script.py

Or does it have to have the `python` command in there?

---

### Post by unutbu on 2008-11-15
If script.py begins with a "shebang" line such as:
```

#!/usr/bin/env python
```
then you can type
```

% script.py
```
to run it from the terminal. If script.py does not 
contain a shebang line, then you need to specify python at the terminal:```

% python script.py
```

---

