---
title: "Insert Ubuntu Terminal Command in Python Script"
date: 2009-05-16
forum: Programming Talk
---

### Post by eng_akyq on 2009-05-16
Dear Forum Expert
I need your help to insert a terminal command in Python for the following Python Script:
```

```
import bluetooth

print "performing inquiry..."

nearby_devices = bluetooth.discover_devices(lookup_names = True)

print "found %d devices" % len(nearby_devices)

for name, addr in nearby_devices:
    print "  %s - %s" % (addr, name)
```

```


:oI need after finding the bluetooth devices, the command sending a text file to them by Obexftp terminal command.

Thank you very much

---

### Post by Reiger on 2009-05-16
There is the os module? And I'd assume the Python tutorials cover a simple shell call.

---

### Post by eng_akyq on 2009-05-16
Dear Forum Expert
I need your help to insert a terminal command in Python for the following Python Script:
```


import bluetooth

print "performing inquiry..."

nearby_devices = bluetooth.discover_devices(lookup_names = True)

print "found %d devices" % len(nearby_devices)

for name, addr in nearby_devices:
    print "  %s - %s" % (addr, name)


```
I need after finding the bluetooth devices, the command sending a text file to them by Obexftp terminal commands.

Thank you very much[/quote]

---

### Post by eng_akyq on 2009-05-16
Sorry for disturbing
I need also to add rssi function to this code to implement it distance control so it's only connect it to the specific distance and send a text file if the bluetooth device is approximately out of bluetooth range

Thank you very much

---

### Post by Bodsda on 2009-05-16
As mentioned before, terminal commands can be run using the os module.

```
os.system('echo $HOME')
```
for example.

To see other uses of the module you can use ```
python
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> help(os)
```

Hope this helps,

Bodsda

---

### Post by dandaman0061 on 2009-05-16
Actually the 'os.system()' call is being depreciated in favor of the 'subprocess' module.

```

import subprocess

return_code = subprocess.call("ls -l", shell=True)
if return_code == 0:
    print "success"
else:
    print "'ls' cmd failed"

```

Also, with the subprocess module you can get the output of stderr, stdout, or talk to the process with stdin.  Just use the 'subprocess.Popen()' call.  (Read the library reference for more info and examples)

---

### Post by eng_akyq on 2009-05-16
Thank you very much [dandaman0061]("http://ubuntuforums.org/member.php?u=126481") I'll read about subprocess module reference and tell you what I will get.

---

### Post by eng_akyq on 2009-05-22
I could implement os module.
with subprocess I could not understand it.
Now I need to implement rssi.
any idea about it

---

### Post by eng_akyq on 2009-08-09
Also I could implement 
>>>import commands
And I found magnificent results.

---

