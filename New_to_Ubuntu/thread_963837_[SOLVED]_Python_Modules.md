---
title: "[SOLVED] Python Modules"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by simon303 on 2008-10-30
I am trying to use custom modules in Python that I have saved in "~/python.modules"
However, this is not where my programs are run from. I have created a file "~/.pythonrc.py" that modifies "PYTHONPATH" to include my custom directory, but to execute this file I need to run "import user" at the start of all my programs.
I was wondering if there is a global configuration file that I can either add "~/python.modules" to as a module location, or a line to execute "import user" every time python is started as this will save time and effort in the future.
Thanks
Simon

---

### Post by ethoxyethaan on 2008-10-30
normally modules are stored in:
/usr/lib/python2.5/

if that is your question.

---

### Post by simon303 on 2008-10-30
Not really,
I would like to store my own modules in my own directory and add that directory to the list that Python "looks" for modules in.
This can be done with a line of code at the bash prompt every time, or by running "~/.pythonrc.py" when python starts.
The second method requires the code "import user" to be run every time Python starts and I was wondering if there is a file that Pyhton runs every time it starts that I can add a line or 2 of code to so my directory is added automatically.

---

### Post by unutbu on 2008-10-30
Add this to your ~/.profile 
```

PYTHONPATH=$HOME/python_modules
export PYTHONPATH
```

Then change your ~/python.modules directory to ~/python_modules. You may not absolutely need to do this, but I think it is a good idea, because in general Python gives special meaning to the dot and
```

import python.modules 
```

means look for the file called 'modules' inside the directory called 'python'. Clearly, that is not what you want. (I know you don't intend to import python.modules, but still I think it is better not to use . or - in python directory or filenames.)

Finally, just logout and login to make the PYTHONPATH active.

---

### Post by simon303 on 2008-10-30
Thank you unutbu, that has worked

---

