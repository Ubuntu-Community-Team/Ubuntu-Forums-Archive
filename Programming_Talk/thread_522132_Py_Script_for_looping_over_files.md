---
title: "Py Script for looping over files"
date: 2007-08-10
forum: Programming Talk
---

### Post by b0ng0 on 2007-08-10
I am fairly new to python and I was just wondering if someone could post some code that would allow me to loop over files in a directory and perform a video conversion (using ffmpeg) one by one (so as not to chew up my CPU).
I was trying with os.walk() and os.listdir() but my knowledge of python is pretty limited. Thanks for any help/code :D

---

### Post by Soybean on 2007-08-10
I don't know how to do this in Python, so I probably shouldn't be answering at all... ;) But I just thought I'd mention that, even when I do learn Python, this is probably something I'd still use Perl for. The Perl syntax for looping over all files in the current directory is:
```

#!/usr/bin/perl

while(<*>)
{
  print "$_ \n";
}

```

Then, instead of printing the filenames, you just replace that line with whatever you want to do, where $_ is the variable for the filename.

If you're trying to run command-line programs on each file (I assume ffmpeg is something you run from the command-line?), you can use system
```
system("ffmpeg $_ ...");
```

---

### Post by [h2o] on 2007-08-10
```
import glob

mpgfiles = glob.glob("~/video/*.mpg")

for file in mpgfiles:
  system("ffmpeg %s ...." % file)


```

glob is your friend :)

---

### Post by b0ng0 on 2007-08-10
Woo! Thanks. 

Just one last thing - each file will obviously have a different name, so the ffmpeg command will be something like:

ffmpeg -i movie.avi convertedmovie.avi

If I put this into the *system("ffmpeg %s ...." % file)* do I use %s where the file name should be?

Thanks

---

### Post by [h2o] on 2007-08-10
The python syntax for string formatting is
```
mystring = "I am an %s from %s" % ("alien","Mars")
```

I guess what you want is something like:
```

import glob

avifiles = glob.glob("~/video/*.avi")

for file in avifiles:
  outfile = "converted_%s" % file  # a.avi becomes converted_a.avi
  command = "ffmpeg -i %s %s " % (file, outfile) # create command
  system(command) # Run command

```

---

### Post by b0ng0 on 2007-08-10
Awesome-o, thanks for that. I'll give it a go when I get back from work :D

---

### Post by b0ng0 on 2007-08-10
[I]Traceback (most recent call last):
  File "convert.py", line 8, in ?
    system(command) # Run command
NameError: name 'system' is not defined[/I]

I got this when I tried to run it. Should I have defined system before, or am I missing a module?

---

### Post by Nekiruhs on 2007-08-10
your missing a module. just add to the top 
```
from os import system
```

---

### Post by pmasiar on 2007-08-10
> **'[h2o] said:**
> 
```

for file in avifiles:

```

if you use any decent editor with syntax highlighting, you would notice that file has special color - it is reserved keyword and cannot be used as name. try infile instead.

---

### Post by Soybean on 2007-08-10
> **pmasiar said:**
> if you use any decent editor with syntax highlighting, you would notice that file has special color - it is reserved keyword and cannot be used as name. try infile instead.

Well that's interesting... gedit *does* color it differently, but on the other hand, it works. If file is a reserved word, why doesn't it cause an error? If you open python in interactive mode, it seems like you can use "file" however you want. That's kind of weird, isn't it?

---

### Post by pmasiar on 2007-08-10
Oh yes you are right. "file()" is built-in function (same as open()). So yes, you *can* use name "file" for something else, but is is considered bad taste.

I should fire IDLE and check it before posting. :-(

---

### Post by UbuWu on 2007-08-10
This one does it recursively, including all subdirectories:

```

import dircache, os, system

def ConvertVideos():
    thisDir = os.getcwd()
    for file in dircache.listdir(thisDir):
        if (file.endswith('mpg') or os.path.isdir(file)) and not file.startswith('.'):
            if file.endswith('mpg'):
                system("ffmpeg %s converted_%s" % (file,file))
            if os.path.isdir(file):
                os.chdir(file)
                ConvertVideos()
                os.chdir('../')

ConvertVideos()

```

(adapted from [this]("http://www.pthree.org/2007/08/09/recursion-in-python/"))

---

### Post by UbuWu on 2007-08-10
I was wondering, is it possible with a simple python script, to convert several files in parallel?

---

### Post by pmasiar on 2007-08-10
> **UbuWu said:**
> I was wondering, is it possible with a simple python script, to convert several files in parallel?

well, to work in parallel, you need to start asynchronous processes, check and synchronize results - how *that* would be simple? :-)

---

### Post by UbuWu on 2007-08-10
> **pmasiar said:**
> well, to work in parallel, you need to start asynchronous processes, check and synchronize results - how *that* would be simple? :-)

Ok, let's try:

```

import glob, system
from threading import Thread

class Convert(Thread):
   def __init__ (self,Video):
      Thread.__init__(self)
      self.video = Video
   def run(self):
      system("ffmpeg %s converted_%s" % (self.video, self.video))


mpgfiles = glob.glob("~/video/*.mpg")

threads = []

for file in mpgfiles:
   current = Convert(file)
   threads.append(current)
   current.start()

print 'waiting for all tasks to complete'
# next statement waits for all threads to finish
for t in threads: t.join()
print 'all tasks done'


```

Would this work? (cannot test it here right now)

---

