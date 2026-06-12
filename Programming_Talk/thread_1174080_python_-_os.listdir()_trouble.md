---
title: "python - os.listdir() trouble"
date: 2009-05-30
forum: Programming Talk
---

### Post by prem1er on 2009-05-30
I can't figure out what I am doing wrong here.  The code looks exactly like it does in my book, but yet I can't get it to read the files in the directory. 

```
_inputDir = '/home/dev/shellScript'

```

```
class PTmp(ProcessEvent):
   def process_IN_CREATE(self, event):
      _inputFile = _inputDir + '/'  + event.name + '/'
      print _inputFile
      _fileList = os.listdir(_inputFile)
      for name in _fileList:
         print name

```

edit: I'm still confused.  I just changed the variable '_inputFile' to a hard coded string and it only printed out 2 of the files in the directory (which should be 10), so I'm completely lost as to what it could be.

Here are the results of the test with a hard coded _inputFile.

```

./test.py
/home/dev/shellScript/new/
00 - Surfer Rosa.m3u
12 - Vamos.mp3

```

---

### Post by unutbu on 2009-05-30
I stuck your code in here (lightly modified), and it worked:
[PHP]#!/usr/bin/env python
import sys
from pyinotify import WatchManager, Notifier, EventsCodes, ProcessEvent
import os

class PTmp(ProcessEvent):
    def process_IN_CREATE(self, event):
        _inputDir = os.path.join(os.environ['HOME'],'test')
        _inputFile = os.path.join(_inputDir,event.name)
        print _inputFile
        _fileList = os.listdir(_inputFile)
        for name in _fileList:
            print name

if __name__=='__main__':
    try:
        path = sys.argv[1]
        if not path.endswith('/'):
            path=path+'/'
    except IndexError:
        print 'use: %s dir' % sys.argv[0]    
    wm = WatchManager()
    mask = EventsCodes.IN_CREATE
    notifier = Notifier(wm, PTmp())
    wdd = wm.add_watch(path, mask, rec=True, auto_add=True)
    while True:  
        try:
            notifier.process_events()
            if notifier.check_events():
                notifier.read_events()
        except KeyboardInterrupt:
            notifier.stop()
            break
[/PHP]
There is nothing wrong with the code you posted.

Can you post the output of 
```

ls -l /home/dev/shellScript/new/
```

---

### Post by prem1er on 2009-06-01
```
-rw-r--r-- 1 dev dev  551766 2009-05-30 14:21 00 - Cover.jpg
-rw-r--r-- 1 dev dev    1984 2009-05-30 14:21 00 - Surfer Rosa.cue
-rw-r--r-- 1 dev dev    6207 2009-05-30 14:21 00 - Surfer Rosa.log
-rw-r--r-- 1 dev dev     866 2009-05-30 14:21 00 - Surfer Rosa.m3u
-rw-r--r-- 1 dev dev  638059 2009-05-30 14:21 00 - Tracklisting.jpg
-rw-r--r-- 1 dev dev 5930201 2009-05-30 14:21 01 - Bone Machine.mp3
-rw-r--r-- 1 dev dev 3618144 2009-05-30 14:21 03 - Something Against You.mp3
-rw-r--r-- 1 dev dev 3158945 2009-05-30 14:21 04 - Broken Face.mp3
-rw-r--r-- 1 dev dev 8031497 2009-05-30 14:21 05 - Gigantic.mp3
-rw-r--r-- 1 dev dev 5038373 2009-05-30 14:21 06 - River Euphrates.mp3
-rw-r--r-- 1 dev dev 7407188 2009-05-30 14:21 07 - Where Is My Mind.mp3
-rw-r--r-- 1 dev dev 4092074 2009-05-30 14:21 08 - Cactus.mp3
-rw-r--r-- 1 dev dev 3697852 2009-05-30 14:21 09 - Tony's Theme.mp3
-rw-r--r-- 1 dev dev 3524856 2009-05-30 14:21 10 - Oh My Golly!.mp3
-rw-r--r-- 1 dev dev 1319697 2009-05-30 14:21 11 - (Untitled).mp3
-rw-r--r-- 1 dev dev 8388044 2009-05-30 14:21 12 - Vamos.mp3
-rw-r--r-- 1 dev dev 3238230 2009-05-30 14:21 13 - I'm Amazed.mp3
-rw-r--r-- 1 dev dev 4152774 2009-05-30 14:21 14 - Brick Is Red.mp3
-rw-r--r-- 1 dev dev   11472 2009-05-30 14:21 Folder.jpg

```

I have no idea what is going wrong?  Here is the complete code.

```
#!/usr/bin/env python

from pyinotify import WatchManager, Notifier, ProcessEvent, IN_CREATE
import os

logFile = 'musicIndexer.log'
_inputDir = '/home/dev/shellScript/'

wm = WatchManager()
mask = IN_CREATE

class PTmp(ProcessEvent):
   def process_IN_CREATE(self, event):
      _inputFile = _inputDir + event.name + '/'
      print _inputFile
      _fileList = os.listdir('/home/dev/shellScript/new')
      for name in _fileList:
         print name

p = PTmp()
notifier = Notifier(wm, p)
wdd = wm.add_watch(_inputDir, mask, rec=False)
notifier.loop()

```

---

### Post by ghostdog74 on 2009-06-01
use os.chdir() before you use os.listdir()

---

### Post by prem1er on 2009-06-01
> **ghostdog74 said:**
> use os.chdir() before you use os.listdir()

Like this?

```
class PTmp(ProcessEvent):
   def process_IN_CREATE(self, event):
      _inputFile = _inputDir + event.name + '/'
      print _inputFile
      os.chdir('/home/dev/shellScript/new/')
      _fileList = os.listdir('/home/dev/shellScript/new/')
      for name in _fileList:
         print name


```

---

### Post by prem1er on 2009-06-01
After making that change I still only get 2 results from the directory.

```
class PTmp(ProcessEvent):
   def process_IN_CREATE(self, event):
      _inputFile = _inputDir + event.name + '/'
      print _inputFile
      os.chdir(_inputFile)
      _fileList = os.listdir(_inputFile)
      for name in _fileList:
         print name

```


```
dev@bubbles:~/shellScript$ ./test.py 
/home/dev/shellScript/new/
00 - Surfer Rosa.m3u
12 - Vamos.mp3

```

---

### Post by dandaman0061 on 2009-06-01
You could try to start small and add to it. Does the below work?

```

#!/usr/bin/env python

import os

_input_dir = '/home/dev/shellScript/new'

_file_list = os.listdir(_input_dir)
for name in _file_list:
    print name

```

---

### Post by prem1er on 2009-06-02
Yes, this works without a problem.

---

### Post by prem1er on 2009-06-02
edit: Sorry for post not sure what was going on again.

---

### Post by prem1er on 2009-06-02
I FINALLY figured it out!!! The directory I was watching is waiting for me to create a file. When I copied a file into it the script started to execute and it would try to list the directories that were copied, so I'm guessing the script was running before all the files were copied.  That is why I was getting an incomplete file list.  So, here is my next question.  Should I just make the program sleep for a little while after it detects a new file?  Is this my best option?

---

### Post by unutbu on 2009-06-02
Oh... congratulations, I think you found the problem!

So what are you trying to do?

Why list all the files in the directory? In general, I think you are supposed to write process_* methods to handle single files as they are created, modified, etc. 

Also, if you want the PTmp to do something *after* a new file is created in /home/dev/shellScript/, then perhaps you want IN_CLOSE_WRITE instead of IN_CREATE.

---

### Post by prem1er on 2009-06-03
I'm not sure if I should start a new thread for this or what. What I was originally trying to do was pull out one (any) .mp3 file from the directory and read the id3 tag from it. I was suggested this.  How does this sound?

```
for root, dirs, files in os.walk(path):
   for f in files:
       filename = os.path.join(root, f)
       if filename.endswith('.mp3'):
           #do something

```

I'm not too worried if this is not the best way to do this and I have to remove what I just did, I am trying to learn python anyway, so suggestions are welcomed.  Thanks.

---

### Post by unutbu on 2009-06-03
Do you want the script to pull out an mp3 the moment it runs, or do you want it to monitor a directory and pull out a random mp3 in reaction to the creation of a file?

---

### Post by prem1er on 2009-06-03
Monitor the directory and pull an mp3 when a new file is created.  I have rtorrent set up to move completed downloads to a certain directory.  I want to watch that directory for new files.  Once there is a new file I want to grab any of the mp3's from inside it and read the id3 tag off of it.

---

### Post by unutbu on 2009-06-03
Would this do?
[PHP]
#!/usr/bin/env python
class PTmp(ProcessEvent):
   def process_IN_CLOSE_WRITE(self, event):
       if event.pathname.endswith('.mp3'):
           # read id3 tag[/PHP]

This could be used monitor a directory, and react *after* an mp3 is completely written.
event.pathname returns the full path to the file which has just been written.

---

### Post by prem1er on 2009-06-03
Thanks. I'll try it out and let you know.

---

### Post by prem1er on 2009-06-03
Ok, I think I see what you are saying, but the albums are being moved to a directory /music/.  That is the directory being watched.  Now inside that there will be directories being created (album names), so something like this /music/Zeppelin III/. But I want to move into that directory and pull out an mp3.  I think your script is just looking in the /music/ directory for new albums.  I'm going to work on it now and see if I can figure it out.

---

### Post by unutbu on 2009-06-03
Try changing
```

wdd = wm.add_watch(_inputDir, mask, rec=False)
```

to
```

wdd = wm.add_watch(_inputDir, mask, rec=True, auto_add=True)
```

This will make wm recursively watch _inputDir. Not only will /music be watched, but so will all subdirectories. Then you can continue monitoring IN_CLOSE_WRITE events and react to the creation of the mp3 files in /music/Zeppelin III/ rather than the creation of the "Zippelin III" directory itself.

---

