---
title: "[Python] Problem with urllib2"
date: 2010-01-17
forum: Programming Talk
---

### Post by baskar007 on 2010-01-17
hi friends,
I building a simple downloader application in python using urllib2.

now i have a major problem with urllib2.

i used this type of the code:
[PHP]
import urllib2
connection = urllib2.urlopen("http://softwareroxer.110mb.com/apps/rdm/rdm0.9-1alpha.deb.zip")
rec_size = 0
fsize = connection.headers(["Content-Length"])
while 1:
    Out = connection.read(5*1024)  #5kb buffer
    rec_size = len(Out)+rec_size
    if rec_size == fsize:
        print "File size matched"
        break
    elif Out == "":
        print "Empty output...."
        print rec_size,fsize
    else:pass
[/PHP]

i think my code was correct, But urllib2 giving empty output ("") in the middle of the file.

I have also tried with httplib, but the same error occurred.  
Note:
    i am using threads for this connections.
 
whats wrong with urllib or my code, I can't get any ideas about this ,

please help me friends.

thanks in advance.

---

### Post by Unlimited Bit on 2010-01-17
```
import urllib2

remoteFile = urllib2.urlopen("http://softwareroxer.110mb.com/apps/rdm/rdm0.9-1alpha.deb.zip")
print "Remote file size:", remoteFile.info()["Content-Length"], "bytes"

print "Reading 5x1024 bytes .."

inBound = remoteFile.read(5*1024)
dataLength = len(inBound)

print "Received:", dataLength, "bytes"

remoteFile.close()

``````
Remote file size: 402764 bytes
Reading 5x1024 bytes ..
Received: 5120 bytes
```

---

### Post by baskar007 on 2010-01-17
> **Unlimited Bit said:**
> ```
import urllib2

remoteFile = urllib2.urlopen("http://softwareroxer.110mb.com/apps/rdm/rdm0.9-1alpha.deb.zip")
print "Remote file size:", remoteFile.info()["Content-Length"], "bytes"

print "Reading 5x1024 bytes .."

inBound = remoteFile.read(5*1024)
dataLength = len(inBound)

print "Received:", dataLength, "bytes"

remoteFile.close()

``````
Remote file size: 402764 bytes
Reading 5x1024 bytes ..
Received: 5120 bytes
```
i think you don't understand my Q. sorry for that.

here is my problem:
 i want to download 402764 bytes size file. So i am using 5kb buffer in a while loop.  after 201382 bytes completed urllib2 will give a empty output (that is 'len("")').

---

