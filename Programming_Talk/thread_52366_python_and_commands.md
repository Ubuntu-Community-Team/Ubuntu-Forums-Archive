---
title: "python and commands"
date: 2005-07-27
forum: Programming Talk
---

### Post by somuchfortheafter on 2005-07-27
I am trying to make a clone of pspvideo9 for linux and I figured the simplest way would be to create a gui front end of ffmepg, just out of curiousity in python how do i use it to exit command in the local hosts console?

---

### Post by DJ_Max on 2005-07-27
Do you mean as in the way bash exit() does?
If so you wanna import sys, and do a sys.exit()

Unless you're looking for something else.

---

### Post by somuchfortheafter on 2005-07-27
no like ffmpeg -ibankanr blaiklk blah
so that it runs that as a command into the terminal/console

---

### Post by LordHunter317 on 2005-07-27
sys.exec() I believe, but I don't do much (any) python programming.

---

### Post by jerome bettis on 2005-07-27
import os
os.popen("shell command")

also if you need the output of the command you can do something like

if (os.popen("whoami").readlines() != "root\n")
   print "script must be run as root"
   sys.exit()

---

### Post by somuchfortheafter on 2005-07-28
I dont know how many know what pspvideo9 does but for windows it converst video formats from whatever they are to mp4 for use on a psp. Currently there is no simple program to do this in linux so I figured I would start by writing a front end for ffmpeg and that would be the simplest solution. anyway here is the code so far:
```

import os
import sys

print"/t /t PSPLIN 1.0"

print "Enter Video File For Conversion"
host_video_1 = raw_input(': ')
print "Enter Filename For Exported Video"
export_video_1 = raw_input(': ')

print "/n Video Is Currently Being Exported..."
os.system('ffmpeg -i '<host_video_1> '-an -b 300 -vcodec mpeg4 '<export_video_1>)
print "Congradulations! Video Exported"

raw_input ("\n\nPress The Enter Key To Exit.")

```

anyway trying to execute this very very simple version of the program it returns a syntax error in the os.system line at the host_video_1 portion. I have tried everyway imaginable to add these lines into that but still it returns a syntax error. Any suggestions?

yes I realize my talent is somewhat lacking but I figured the best way to learn to program is to pick a task i cannot do and then stick with it until it is finished.

---

### Post by thumper on 2005-07-28
Not sure what all your angle brackets are with your command, but I'd suggest creating the command string separately from the execution of the command.  You can always echo the command in a print statement so you can see what the system is being given.

For example
```

cmd = 'ffmpeg -i %s -an -b 300 -vcodec mpeg4 %s' % (host_video_1, export_video_1)
print 'About to execute:\n%s' % cmd

```

Also I tend to use **os.popen** instead of **os.system** but this depends on whether you are trying to parse the output of the command  :) .

---

### Post by cwaldbieser on 2005-07-28
```
os.system('ffmpeg -i '<host_video_1> '-an -b 300 -vcodec mpeg4 '<export_video_1>)

```

The string literal you are passing to os.system is malformed.  It looks like you have unescaped single quotes in a python string literal that is delimited by single quotes.  Try something like

```
os.system("ffmpeg -i '<host_video_1> '-an -b 300 -vcodec mpeg4 '<export_video_1>")
```
I am guessing you will have to interpolate values for <host_video_1> and <export_video_1>.

---

