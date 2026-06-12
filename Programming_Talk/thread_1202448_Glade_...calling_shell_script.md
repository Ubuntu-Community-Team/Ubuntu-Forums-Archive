---
title: "Glade ...calling shell script"
date: 2009-07-02
forum: Programming Talk
---

### Post by san2sh on 2009-07-02
hello 
I have just started exeprimenting with glade and now i have a shell script which does lot of functions.

I have created a gui using glade and now i want to know how to execute a shell script when a button is clicked.That is mainly how to call a shell script. I am using python as programming language

Please let me know as how to go about this 

Thanks in advance.

---

### Post by WRDN on 2009-07-02
To run a system command in Python:

```

import subprocess
subprocess.call(["/path/to/script.sh","args"],shell=True)

```

---

