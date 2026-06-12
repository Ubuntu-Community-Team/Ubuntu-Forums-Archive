---
title: "Get a loop in python"
date: 2013-03-07
forum: Programming Talk
---

### Post by PaulNL on 2013-03-07
Hello All i want to loop this script til i stop it. how can i do that ??

i have made 

```

import os
import time

os.system("clear")
os.system("sudo virsh -c qemu:///system list")
 

```

Paul

---

### Post by r-senior on 2013-03-07
Something like this?

```

import time

while True:
    print 'Hello'
    time.sleep(1)

```

---

### Post by PaulNL on 2013-03-07
when i use that i get an error IndentationError: expected an idented block

i have made a second script to work with the first script

```

while true;
do python status.py ;
sleep 5s ;
done

```

i cant get it all in the same file

---

### Post by r-senior on 2013-03-07
Just do it in Python, there's no need for a calling script.

Python needs the content of the loop indented consistently, i.e. the same number of spaces for each line within the indent.

```
#!/usr/bin/env python

import os
import time

while True:
    os.system("clear")
    os.system("sudo virsh -c qemu:///system list")
    time.sleep(5)

```

I've added the shebang line at the top so it runs as a script. Don't forget to 'chmod +x'.

---

### Post by PaulNL on 2013-03-07
when i use your script i get an error se thread above

---

### Post by schragge on 2013-03-07
The TAB/space characters could get messed up when pasting from the browser window. Delete the spaces, and re-insert them manually.

---

### Post by PaulNL on 2013-03-07
Works :) Thanks

---

