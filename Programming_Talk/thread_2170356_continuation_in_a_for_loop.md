---
title: "continuation in a for loop"
date: 2013-08-25
forum: Programming Talk
---

### Post by wingnut2626 on 2013-08-25
First off this code is rough, hasnt been even cleaned up yet, but the question is still clear:

```
i[B]mport sys
import os.path
import subprocess
import time

def main():
  if len(sys.argv) == 1:
    subprocess.call(['espeak', 'i need a directory please'])
    sys.exit(0)
  elif len(sys.argv) == 2:
    if os.path.isdir(sys.argv[1]):
      a = os.listdir(sys.argv[1])
      subprocess.call(['espeak', 'there are' + str(len(a)) + ' items in the directory' + str(sys.argv[1])])
      time.sleep(1)
      subprocess.call(['espeak','they break down as follows'])
      for item in a:
        b = item.split('.')
        subprocess.call(['espeak', b[0]]);
        _os.path.isdir(item)_
    else:       
      subprocess.call(['espeak', sys.argv[1] + 'is not a valid directory'])
  else:
    subprocess.call(['espeak', 'too many arguments.  exiting'])[/B]



if __name__ == '__main__':
  main()
```

The underlined segment of code is not executing.  Is it something with the subprocess.call before it?  or is there something i should do?  I even put a semicolon in there to see...

---

### Post by prodigy_ on 2013-08-25
> **wingnut2626 said:**
> The underlined segment of code is not executing.
How do you know? os.path.isdir won't give you any output unless you're testing your code interactively in Python interpreter.

---

### Post by wingnut2626 on 2013-08-26
Well the original segment of code was:
if os.path.isdir(item): subprocess.call(['espeak' , 'spam']) #was not getting desired output

---

### Post by wingnut2626 on 2013-08-26
```
import sys
import os.path
import subprocess
import time

def main():
  if len(sys.argv) == 1:
    subprocess.call(['espeak', 'i need a directory please'])
    sys.exit(0)
  elif len(sys.argv) == 2:
    if os.path.isdir(sys.argv[1]):
      a = os.listdir(sys.argv[1])
      subprocess.call(['espeak', 'there are' + str(len(a)) + ' items in the directory' + str(sys.argv[1])])
      time.sleep(1)
      subprocess.call(['espeak','they break down as follows'])
      for item in a:
        b = item.split('.')
        subprocess.call(['espeak', b[0]]);
       [U] print(os.path.abspath(item))
        if os.path.isdir(item)):
          print(item)
        else:
          print('Nope')
        input()[/U]
    else:       
      subprocess.call(['espeak', sys.argv[1] + 'is not a valid directory'])
  else:
    subprocess.call(['espeak', 'too many arguments.  exiting'])



if __name__ == '__main__':
  main()
```

Added the underlined code (for debugging purposes only).  Shows the directory path on the printout, but everything gets a 'Nope'.  I did notice that because of the split('.') i was losing readout of the hidden directories and files, but that has nothing to do with the representation of item in the underlined code.....stumped....

---

### Post by Vaphell on 2013-08-26
[http://stackoverflow.com/questions/3761473/python-not-recognising-directories-os-path-isdir](http://stackoverflow.com/questions/3761473/python-not-recognising-directories-os-path-isdir)

---

### Post by ofnuts on 2013-08-26
You are confused about your various paths and directories:

[LIST]
[*]'os.listdir(sys.argv[1])' lists the **names** of files/directories in that directory (but not their full path) 
[*][FONT=arial]'os.path.abspath(item)' understands 'item' (which has no path) as the name of a file in your current directory (not sys.argv[1]) and so builds a full path to that hypothetical file (that doesn't exist)[/FONT] (this function does more or less does the same thing as the 'readlink' command) 
[*][FONT=arial]there is not much point into printing the output of [/FONT][FONT=arial]'os.path.abspath(item)' since you aren't using it in the code. But it shouldn't be printing the file paths you think and this should be a clue.[/FONT][FONT=arial] 



[/FONT] 
[/LIST]

---

