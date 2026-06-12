---
title: "Python interacting with zenity"
date: 2009-03-05
forum: Programming Talk
---

### Post by VCoolio on 2009-03-05
After having googeled all afternoon I give up and start this thread. I have a commandline python script which I want to turn into a nautilus script. This requires that the script at some point uses a popup window to print a message instead of printing in the shell. The code was as follows:
[PHP]   if ip_addr:
      print "Now serving on http://%s:%s/" % (ip_addr, httpd.server_port)[/PHP]

I changed that successfully to
[PHP] if ip_addr:
      os.system('zenity --info --text="Now serving on http://%s:%s/"' % (ip_addr, httpd.server_port))[/PHP]

So far so good. Now comes the tricky part. I want a window that enables me to cancel the script or approve. This would mean a zenity --queston window, with a 'cancel' and a 'ok' button. In zenity 'cancel' returns the value '1', and 'ok' returns the value '0'. But how do I tell the script to react on these buttons? 'Cancel' would mean 'sys.exit ()' and 'ok' would mean 'continue'. I checked loads of documentation on the subprocess possibility (which seems to have replaced the os.popen command) but I don't understand how it works or how to have it interact with a window. Who helps me out? It doesn't have to be with zenity by the way. A gtk-window or whatever comes standard with Ubuntu is also ok.

---

### Post by unutbu on 2009-03-05
[PHP]#!/usr/bin/env python
from subprocess import Popen

proc=Popen("zenity --question --text='Quit now?'", shell=True )
proc.communicate()
if proc.returncode:
    print "Cancel was pressed"
else:
    print "Ok was pressed"[/PHP]

---

### Post by Bodsda on 2009-03-05
Hi.

If you use 
```
zenity --question
```
ok returns 0
cancel returns 256

so you could do this

[PHP]
#! /usr/bin/env python
import os

question = os.system("zenity --question --text="continue?")
if question == 256:
    print "Operation canceled."
    exit()
else:
    print "Operation continuing."
[/PHP]

---

### Post by VCoolio on 2009-03-05
Thanks for your replies. I found out that 'cancel' gives 256 indeed. I don't know why the wiki on zenity says otherwise. However, someone got it working with the following: 
[PHP] if ip_addr:
      userschoice = os.system('zenity --question --text "Does not matter now"')

   # To kill it if the users presses the cancel-button

   if '256' in str(userschoice):
      sys.exit (1)[/PHP]

Problem solved. Thanks both for your help.

---

### Post by imdano on 2009-03-05
> **VCoolio said:**
> Thanks for your replies. I found out that 'cancel' gives 256 indeed. I don't know why the wiki on zenity says otherwise. It does return one, but when you use os.system() you get the return value bit-shifted to the left by 8, because it uses the return code given by an internally used wait() call (see [here](http://docs.python.org/library/os.html#os.wait) for an explanation of its return code).  To get the real return code you just shift it back.```
>>> 256 >> 8
1
```

edit: If you want to get the correct rc right away, use the subprocess module [php]>>> import subprocess
>>> p = sp.Popen("zenity --question", shell=True)  # Dialog appeared after hitting enter, I clicked cancel
>>> p.poll()
1
>>>
[/php]

---

### Post by Endolith on 2009-10-27
First, install python-setuptools. Then, do this:

```
sudo easy_install pyzenity
```Then do this:

[php]if ip_addr:
  if not PyZenity.Question("Now serving on http://%s:%s/" % (ip_addr, httpd.server_port)):
    sys.exit
[/php]
:)

---

