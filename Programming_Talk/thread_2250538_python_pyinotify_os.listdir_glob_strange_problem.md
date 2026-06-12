---
title: "python pyinotify os.listdir glob strange problem"
date: 2014-10-29
forum: Programming Talk
---

### Post by haydar-hotmail on 2014-10-29
hi all

I am trying to make a simple piece of software that automatically makes a list based on the file contents of any newly inserted USB memory stick. 

using ubuntu 14.04.

now using os.listdir() and glob.glob() work fine on their own... 

```
#!/usr/bin/python

import os, glob

input_dir = '/media/oico/one/'
print "input dir is",input_dir
print "current directory is", os.getcwd()
print "printing glob",glob.glob(input_dir+'*')
print "printing listdir", os.listdir(input_dir)
os.chdir(input_dir)
print "current directory is", os.getcwd()
```



however when using it with pyinotify, and getting the input_dir as os.path.join(event.path, event.name) ... I just get a blank list every time...

tried concatenating strings to add single quotes, double quotes etc... to no avail.

here's a snippet of code with lots of print statements to see progress along the way... I must be making some very basic mistake somewhere!

```
#!/usr/bin/python

#notifier setup
import pyinotify, os, glob

wm=pyinotify.WatchManager()
#blank path
input_dir = '/media/oico'
path=""
class EventHandler(pyinotify.ProcessEvent):
    def process_IN_CREATE(self,event):
        print "event name print ", event.name
        print "event path print", event.path
        global path
        path = os.path.join(event.path,event.name)
        print "path is", path
        os.chdir(path)
        print"current directory is", os.getcwd()
        print "printing listdir for current", os.listdir(path)
    #    for name in mainlist:
    #        print "printing main list", name
    #    print glob.glob('*')
    #    dirs = os.listdir(path)
    #    for file in dirs:
    #        print file
    #    for root, dirs, files in os.listdir(path):
    #        print root
    #        print dirs
    #        print files
        usb_insertion()

def usb_insertion():
    print "usb insertion started"
    print "path carried over", path
    newpath = path+"/"
    print "newpath", newpath        
    print glob.glob(newpath+"*")
    print "listdir", os.listdir(newpath)

handler=EventHandler()
notifier=pyinotify.Notifier(wm, handler)
wdd=wm.add_watch('/media', pyinotify.IN_CREATE, rec=True)
notifier.loop()

```

---

### Post by haydar-hotmail on 2014-10-29
I have solved this in case anyone is interested.
  Adding time.sleep(2) just before doing glob or os.listdir() seems to have done it.

---

