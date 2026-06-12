---
title: "Python help, IO Error!"
date: 2008-08-30
forum: Programming Talk
---

### Post by jacensolo on 2008-08-30
I'm pretty sure this was working the other day. I opened it up to work on it again in Geany and it didn't work. So I switched back to Idle and I'm getting an IOError.

I'm trying to get this to open woot.com and retrieve the information I want and save it to a different file each day. It's not nearly complete though. 

I created a basic library (to learn OO mainly) since I plan to do this with other sites too.
Error
[php]Traceback (most recent call last):
  File "/home/killian/Python/woot.py", line 24, in <module>
    f = open("info", 'r')
IOError: [Errno 2] No such file or directory: 'info'[/php]

Library:[php]import urllib

class Site:
    def __init__(self, site):
        try:
            self.site = urllib.urlopen(site)
        except IOError:
            print "Error: Could not find site"
    def writetofile(self, filepath):
        try:
            self.filepath = str(filepath)
            self.file = open(self.filepath, 'w')
        except TypeError:
            print "Please enter a string, not numbers!"
        except IOError:
            print "Please enter a valid path."
            print "If you are sure this is correct then there is an unknown error"
        try:
            if self.file and self.site:
                for line in self.site:
                    self.file.write(line)
        except:
            print "could not write to file"
[/php]

Program:
[php]
import weblib

def openwoot():
    yield weblib.Site('http://www.woot.com')
def savewoot(obj):
    name = raw_input("Please enter the name of the file\n")
    path = raw_input("Please enter the path in which you would like to save the file\n")
    string = path + name
    print string
    obj.writetofile(string)

try:
    f = open("info", 'r')
except IOError:
    woot = openwoot()
    f.close()
    print "This is your firt time running the program"
    folder = raw_input("Please enter a folder to save your pages and pictures\n")
    f = open("info", 'w')
    f.write(folder)
    f.close()
    f = open("info", 'r')
finally:
    directory = f.readline()

[/php]

I EVEN MADE AN IO EXCEPTION BUT IT DIDN'T COME UP! I know this exception worked before.

---

### Post by ghostdog74 on 2008-08-30
its obvious the error message tells you. the file "info" doesn't exist. you can insert a "print os.getcwd()" to see at which directory the script is in at that point in time before it calls the open(). Also, use 
```

try :
   ...
except Exception,e:
   ...

```to catch all exceptions that may occur and print out the "e" value.

---

### Post by raja on 2008-08-30
Change this

```
try:
    f = open("info", 'r')
except IOError:
    woot = openwoot()
    f.close()
    print "This is your firt time running the program"
    folder = raw_input("Please enter a folder to save your pages and pictures\n")
```

to ```
try:
    f = open("info", 'r')
except IOError:
    woot = openwoot()
    #f.close()
    print "This is your firt time running the program"
    folder = raw_input("Please enter a folder to save your pages and pictures\n")
```

Since f does not exist, trying to close it seems to get you out of the except clause and take you to the finally clause. Atleast that is what happens when I run your code.

---

