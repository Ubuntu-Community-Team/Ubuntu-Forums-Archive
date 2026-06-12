---
title: "python 3 and shutil.copy2"
date: 2015-03-12
forum: Programming Talk
---

### Post by lance bermudez on 2015-03-12
on windows trying to copy python3_files to python dir. Can not use xcopy on this version of windows and need it to be cross platform.
```

import os
import shutil 
os.chdir('C:/Users/l_bermudez/Documents')
os.listdir('.')
shutil.copy2('C:/Users/l_bermudez/Documents/python3_files', 'C:/Users/l_bermudez/Documents/python')

```

error is
```

Traceback (most recent call last):
  File "C:/Users/l_bermudez/Documents/pythontest1.py", line 5, in <module>
    shutil.copy2('C:/Users/l_bermudez/Documents/python3_files', 'C:/Users/l_bermudez/Documents/python')
  File "C:\Python34\lib\shutil.py", line 244, in copy2
    copyfile(src, dst, follow_symlinks=follow_symlinks)
  File "C:\Python34\lib\shutil.py", line 107, in copyfile
    with open(src, 'rb') as fsrc:
PermissionError: [Errno 13] Permission denied: 'C:/Users/l_bermudez/Documents/python3_files'

```

---

### Post by Holger_Gehrke on 2015-03-14
Is the source argument 'C:/Users/l_bermudez/Documents/python3_files' a directory ? Then you're trying to use a file-copy function on a directory, which obviously doesn't work. You'd probably want  'copytree()' which recursively copies directories instead of 'copy2' which copies files and tries to preserve as much metadata as it can.

---

### Post by lance bermudez on 2015-03-20
I changed my code to get some output but it will still not show the files as they are copied over.
```

import os
import shutil

ls=os.listdir('.')#list current dir
print('listing current dir\n')
print(ls)
os.chdir('C:/Users/lance/Documents')
print('\nchanging dir to Documents\n')
nls=os.listdir('.')
print(nls)

print('\nmoving new python dir in Documents\n')
event=shutil.copytree('C:/Users/lance/Documents/python3_files', 'C:/Users/lance/Documents/python')
output = event.communicate()
print(output)

```

the error i get is
```

Traceback (most recent call last):
  File "C:\Users\lance\Documents\pcopy.py", line 20, in <module>
    output = event.communicate()
AttributeError: 'str' object has no attribute 'communicate'

```

---

### Post by ofnuts on 2015-03-20
The [copytree doc](https://docs.python.org/3/library/shutil.html) says it returns the destination argument... what makes you think it returns an "event"?

---

### Post by lance bermudez on 2015-03-20
I do not know. I was told to use it because it would show the files as they are copied over to the other dir. As I have said I must have been told wrong because it does not work. Now that I think about it if I can not see the files as they are moving then I need some kind of progress bar.

---

### Post by ofnuts on 2015-03-21
It wouldn't be very difficult to replace the one-shot copy tree by individual copy operations for each file. Then you would be able to add progress monitoring.

---

### Post by lance bermudez on 2015-03-27
I know I must be a pain to you but thank you for helping this newbie. Just so I'm clear change the folder tree copy(shutil.copytree) to the single files in the folder (shutil.copy2). I can do that no problem if that is what you are talking about. I was also told that I needed a gui library. I did not know if I even needed one. I was thinking something from the command line but when it come right down to it what ever will be the easiest and work on Windows and Linux. I did not know it was this complex. I have used python for years but just started learning to write my own code instead of having a someone do it for me. The reason I want to see the files or have a progress bar is to know that the script is running and not stuck. I hope this helps you understand what I'm looking for and thank you for your time. I need all the help I can get.

---

### Post by ofnuts on 2015-03-28
[LIST=1]
[*]You don't need a GUI library if it's a command-line script... 
[*]This whole thing isn't complex per se,  as a programming exercise, it's even very simple. But programming is complex, because you have to think about all the little details and make sure that you haven't forgotten anything, because computers aren't very forbidding machines for programmers. What you want the program to do must also be very clear in your head. After that writing the actual code is somewhat trivial. 
[/LIST]

To solve your problem, you write a function that takes a directory as argument;that does:
[LIST]
[*]creates the corresponding target directory
[*]obtains a list of the source directory contents (os.listdir())
[*]for each item in this list:
[LIST]
[*]if it is a directory (os.path.isdir()), calls itself with that directory
[*]if it's a file, prints the file and uses shutil.copyfile() to copy the file
[/LIST]
[/LIST]

Then all your programs need to do is call this function with your source directory.

---

