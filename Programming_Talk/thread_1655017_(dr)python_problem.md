---
title: "(dr)python problem"
date: 2010-12-29
forum: Programming Talk
---

### Post by The__Doctor on 2010-12-29
I think there is something wrong with python. I'm using version 2.6.6 For some reason now I can't open files in the same directory as the source. For examples lets say i have a folder with inputfile.txt and source.py. in source.py the script would be 

#!/usr/bin/python

def main():
        file = open('inputfile.txt')
        file.close()
main()

if you'd run it in the terminal, you'd get this error

IOError: [Errno 2] No such file or directory: 'inputfile.txt'

I've tested this with programs i've written that have already worked beforehand.

Anotehr problem is that drPython (the IDE that i use) is broken. I can't open. if i click the shortcut in the menu (in ubuntu) the taskbar says it's opening drpython, then after a few seconds it goes away and drpython isn't open. i tried running it from the terminal, but that dind't work either. This all started when i accidently pressed update in the preferences window in drpython. I wasn't connected to the internet and when i clicked it, i coudln't close the preferences window, so i ended the process. now it doesn't work. I've tried uninstalling and reinstalling drpython aswell.

on an unrelated note, should i stay with python 2 or learn python 3?

---

### Post by Tony Flury on 2010-12-29
What happens if your run your script from the terminal.

i.e. not using drpython
```

python source.py

```

It might be that the IDE is pointing at the wrong current directory.

For such a simple program why use an IDE ?

The current advice is to continue to use Python 2.0 - Python3 is not fully supported with all the modules.

---

### Post by dodle on 2010-12-29
> **The__Doctor said:**
> Anotehr problem is that drPython (the IDE that i use) is broken. I can't open. if i click the shortcut in the menu (in ubuntu) the taskbar says it's opening drpython, then after a few seconds it goes away and drpython isn't open. i tried running it from the terminal, but that dind't work either. This all started when i accidently pressed update in the preferences window in drpython. I wasn't connected to the internet and when i clicked it, i coudln't close the preferences window, so i ended the process. now it doesn't work. I've tried uninstalling and reinstalling drpython aswell.

Try deleting drpython's preferences file:
```
rm ~/.drpython/preferences.dat
```

If that doesn't work, then try deleting the .drpython directory:
```
rm -r ~/.drpython
```


> **The__Doctor said:**
> ...I can't open files in the same directory as the source...

Try telling to program where the source is located:

[php]import os

# Get the path to the source directory
src_dir = os.path.dirname(__file__)

# File we want to open
test_file = "%s/test.txt" % src_dir

# Check if the file exists
if os.path.exists(test_file):
    print "File found"
else:
    print "File not found"[/php]

I agree with sticking with Python2 until Python3 becomes more supported.

---

### Post by The__Doctor on 2010-12-30
@Tony Flury:
I had already run the script from the terminal, that's where i got the error. That's not an actual program that I wrote, it's just an example to show the problem :). I only use an IDE though cause it's easy to test the program. and the autotabbing and syntax highlighting. Thanks for the help though :D

@Dodle:
I deleted the .drpython directory, and that fixed it. Thanks for the help :D. And acutally I just fixed the other opening file problem.

And also, when python3 becomes more supported, would it be worth making the switch to it?

---

