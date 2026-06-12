---
title: "Python - Scan selected directory and subdirectories for .txt files"
date: 2013-04-17
forum: Programming Talk
---

### Post by josiahrulez on 2013-04-17
Hey all,

So my code works, but it doesn't scan subfolders.

```
def scanfolder():    
    import glob
    #Selects the directory to work with
    os.walk('c:/users/josiah/dropbox/scripts/metadata')
    #Scans for files using the glob module with the following rules, anyfilename with the .txt extension
    for name in glob.glob('*.txt'):
        print name
```

if i try this, it doesn't list any files.
```
for name in glob.glob('dir/subdir/*.txt'):
```

So in the python manual it says "Unix style pathname pattern expansion", doesn't the glob module work with windows?

and the script will only work with c:/users/josiah/dropbox/scripts/metadata and not C:\Users\Josiah\Dropbox\Scripts\Metadata?

---

### Post by schragge on 2013-04-17
What *os.walk* is supposed to do here? Should it be something like
```

def scanfolder()
    for path, dirs, files in os.walk('c:/users/josiah/dropbox/scripts/metadata'):
        for d in dirs:
            for f in glob.iglob(os.path.join(path, d, '*.txt')):
                print f

```:?:
But do you actually need glob for this? Try
```

def scanfolder()
    for path, dirs, files in os.walk('c:/users/josiah/dropbox/scripts/metadata')
        for f in files:
            if f.endswith('.txt'):
                print os.path.join(path, f)

```

---

### Post by josiahrulez on 2013-04-17
> **schragge said:**
> What *os.walk* is supposed to do here? Should it be something like
```

def scanfolder()
    for path, dirs, files in os.walk('c:/users/josiah/dropbox/scripts/metadata'):
        for d in dirs:
            for f in glob.iglob(os.path.join(path, d, '*.txt')):
                print f

```:?:

Thanks for the feed back, your code works.

I must of posted the modified code, i did have 
```
os.chdir('c:/users/josiah/dropbox/scripts/metadata'):

```


But another question, i kinda had it working with this
```

import os, time, glob, fnmatch


def scanfolder():
    os.chdir("c:\users\josiah\dropbox\scripts\metadata")
    for name in glob.glob('*/*.txt'):
        print name


print "Now scanning for text files"
scanfolder()
time.sleep(3)


```

but it only scans the subdirectories and not the top folder, how can you add mulitple rules for it to scan by?

I tried this, but it returns an error *TypeError: glob() takes exactly 1 argument (2 given)*
```
for name in glob.glob('*/*.txt', '*.txt'):
```

---

### Post by schragge on 2013-04-17
Perhaps you don't need glob at all. I've edited my post.

---

### Post by josiahrulez on 2013-04-17
> **schragge said:**
> Perhaps you don't need glob at all. I've edited my post.
i'm going to use your way, i was just curious to see why mine wasn't working.

---

### Post by schragge on 2013-04-17
> **josiahrulez said:**
> how can you add mulitple rules for it to scan by?Just as you said: *add*
```

from glob import glob

for f in glob('*.txt') + glob('*/*.txt'):
    print f

```

---

### Post by josiahrulez on 2013-04-18
> **schragge said:**
> Just as you said: *add*
```

from glob import glob
for f in glob('*.txt')+glob('*/*.txt'):
    print f

```

Wow thanks, that works, i had something similiar, but i scrapped it because i couldnt get it working.

i had something like this, i can't remember exactly

```

import os, time, glob, fnmatch

def scanfolder():
    os.chdir(folder)
    for name in glob.glob('*/*.txt'), + glob('*/*.txt'):
        print name
```

Now another question

What i want the python script to do is to scan for .mkv files and when found look for an .nfo with the same file name (not including the extension) in he same folder as where the mkv was found.
Then edit the .nfo file from movieinfo.nfo (Will be in the same folder as the moviename.mkv and moviename.nfo)

```
scan for mkv files in "g:\movies [1080p]" including one subdirectory
    "\moviename.mkv" found in "G:\Movies [1080p]\moviename\"
        query if "\moviename.nfo" exists in "G:\Movies [1080p]\moviename\"
                then edit "G:\Movies [1080p]\moviename\moviename.nfo" and delete all text and replace with "random text", $VARIABLE, "Random text" 
            else edit "g:\movies [1080p]\log.txt"
                add new line to log.txt file, "moviename.nfo not found"
```

now, thats pretty much what i want to do, edit existing nfo files with data pulled from another nfo. What i don't know how to do is use the information glob returns.

glob prints out that moviename.mkv exists in "g:\movies [1080p\moviename\"
then with that information it looks for moviename.nfo in the same folder

Could you please point me in the right direction or tell me what to search for so i can find the information?
Normally i would search for it myself and only ask for help if i couldnt find anything, but i dont know what to search for. I'm very new to scripting btw.

---

### Post by Tony Flury on 2013-04-18
once you get the name of your .mkv file, you need to look at creating the full path of your .nfo file - look at os.path.splitext and os.path.basename for way of breaking apart file names in a portable manner.

To change the contents of the .nfo file you will need to use the open function to open the file, and use the file.write method to write to it, and then use file.close afterwards.

---

### Post by josiahrulez on 2013-04-23
> **Tony Flury said:**
> once you get the name of your .mkv file, you need to look at creating the full path of your .nfo file - look at os.path.splitext and os.path.basename for way of breaking apart file names in a portable manner.

To change the contents of the .nfo file you will need to use the open function to open the file, and use the file.write method to write to it, and then use file.close afterwards.
Ok, I've made a bit of progress so far. 

But another question, heres kinda what i want to do in pseudo code

```
if os.path.isfile(c:\test.txt) is equal to "true"
then
    continue
else
    print "error file doesn't excist"
```

also when i use do this it errors, how can i use the error it returns similiar to what i want to do above?
*IndexError: list index out of range*

a = [COLOR=#000000][1, 2, 3, 4]
[/COLOR][COLOR=#000000]print a[0]
[/COLOR][COLOR=#000000]print a[1]
[/COLOR][COLOR=#000000]print a[2]
[/COLOR][COLOR=#000000]print a[3]
[/COLOR][COLOR=#000000]print a[4]  # errors here before a[4] isn't defined
#once it hits this error it exits the program
[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by schragge on 2013-04-23
```

import os

if not os.access("c:\test.txt", os.F_OK):
    raise  IOError("File doesn't exist")

```
[highlight]Edit[/highlight]
After reading it again, I guess you want it the other way round, i.e.
```

a = range(4)
for i in range(5):
    try:
        print a[i]
    except IndexError as e:
        print "List index out of range"

```

---

