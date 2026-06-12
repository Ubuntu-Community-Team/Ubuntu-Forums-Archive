---
title: "Whats wrong with this python script.."
date: 2012-04-12
forum: Programming Talk
---

### Post by prismctg on 2012-04-12
I m using dynamic ip so , every time i reboot my ubuntu i want to log my IP .. i m using this simple script```
#!/usr/bin/python3
import urllib.request
raw = urllib.request.urlopen('http://automation.whatismyip.com/n09230945.asp')
finaldata=str(raw.read())
outputfile=open("iplist","a")
outputfile.write(finaldata + "\n") 
```Now using Startup Application program i place dis script as a startup item ... but its not working as startup scipt :(  .. How can i solve this problem  ?

---

### Post by papibe on 2012-04-12
Hi prismctg.

Use this instead:
```
from urllib import urlopen
raw = urlopen('http://automation.whatismyip.com/n09230945.asp')
```
And as good practice, log to a file referencing its full path:
```
outputfile=open("/path/to/iplist","a")
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by prismctg on 2012-04-12
hello papibe ; thanx for your advice .. but i m using python 3.2 .. so when io type dis">>> from urllib import urlopen" It gives me ">>> from urllib import urlopen
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    from urllib import urlopen
ImportError: cannot import name urlopen"  :(

---

### Post by ofnuts on 2012-04-12
> **prismctg said:**
> I m using dynamic ip so , every time i reboot my ubuntu i want to log my IP .. i m using this simple script```
#!/usr/bin/python3
import urllib.request
raw = urllib.request.urlopen('http://automation.whatismyip.com/n09230945.asp')
finaldata=str(raw.read())
outputfile=open("iplist","a")
outputfile.write(finaldata + "\n") 
```Now using Startup Application program i place dis script as a startup item ... but its not working as startup scipt :(  .. How can i solve this problem  ?
If it works as a plain script but not as a startup script, maybe it's just because it starts before the network is operational... maybe be you only need to make it sleep 10-20 seconds before retrieving your IP.

---

### Post by prismctg on 2012-04-16
hm.. thats a good idea... thnx a lot :)

---

